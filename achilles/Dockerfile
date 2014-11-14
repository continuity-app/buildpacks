#
# Achilles Buildpack
#

# Pull base image.
FROM dockerfile/ubuntu

# Install Ruby (https://github.com/dockerfile/ruby)
RUN \
  apt-get update && \
  apt-get install -y ruby ruby-dev ruby-bundler && \
  rm -rf /var/lib/apt/lists/*

# Install Bundler
RUN \
	gem install bundler

# Install Python. (https://github.com/dockerfile/python)
RUN \
  apt-get update && \
  apt-get install -y python python-dev python-pip python-virtualenv && \
  rm -rf /var/lib/apt/lists/*

# Install Node.js (https://github.com/dockerfile/nodejs)
RUN \
  cd /tmp && \
  wget http://nodejs.org/dist/node-latest.tar.gz && \
  tar xvzf node-latest.tar.gz && \
  rm -f node-latest.tar.gz && \
  cd node-v* && \
  ./configure && \
  CXX="g++ -Wno-unused-local-typedefs" make && \
  CXX="g++ -Wno-unused-local-typedefs" make install && \
  cd /tmp && \
  rm -rf /tmp/node-v* && \
  echo '\n# Node.js\nexport PATH="node_modules/.bin:$PATH"' >> /root/.bashrc

# Install Bower & Gulp (https://github.com/dockerfile/nodejs-bower-gulp/blob/master/Dockerfile)
RUN \
	npm install -g bower gulp

# Install grunt
RUN \
	npm install -g grunt-cli

# Define working directory.
WORKDIR /data

# Add our compile script
ADD compile.sh /usr/bin/compile
RUN chmod +x /usr/bin/compile

# Define default command.
CMD compile
