[![https://www.singularity-hub.org/static/img/hosted-singularity--hub-%23e32929.svg](https://www.singularity-hub.org/static/img/hosted-singularity--hub-%23e32929.svg)](https://singularity-hub.org/collections/2271)

Singularity recipe files for ApsimX, the next generation of the Agricultural Production Systems sIMulator (APSIM)

## Maintainer notes
This container downloads the ApsimX `deb` file built by the [BOB Build Service](http://apsimdev.apsim.info/APSIM.Builds.Service/Builds.svc/GetURLOfLatestVersion?operatingSystem=Debian) at CSIRO and installs it on a Ubuntu:Bionic container.

To facilitate running the container, a `/usr/local/bin/apsimmodels` file is created as the entrypoint using `/usr/local/bin/apsim` as a template.

## Container-specific notes

- ApsimX apparently needs `/etc/localtime` to run so we have to install `tzdata` as a dependency. We configure our local timezone, but this can be overriden at run time by exporting the `TZ` environment variable.
