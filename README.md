buildpacks
==========

Buildpacks are containarized instances of Grunt, Gulp, Bower, etc... They all expect your project source to be mounted to the /data directory. Such as,

```bash
sudo docker run -v /path/to/project/src:/data achilles
```

In the above example we're using the `achilles` buildpack to compile `/path/to/project/src`.
