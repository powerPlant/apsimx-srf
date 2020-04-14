[![https://www.singularity-hub.org/static/img/hosted-singularity--hub-%23e32929.svg](https://www.singularity-hub.org/static/img/hosted-singularity--hub-%23e32929.svg)](https://singularity-hub.org/collections/2271)

Singularity recipe files for ApsimX, the next generation of the Agricultural Production Systems sIMulator (APSIM)

## Maintainer notes
This container downloads the ApsimX `deb` file built by the [BOB Build Service](https://github.com/APSIMInitiative/APSIM.Builds) at CSIRO and installs it on a Ubuntu:Bionic container.

There are two useful endpoints from the Build Service:
- [Get Latest Version](http://apsimdev.apsim.info/APSIM.Builds.Service/Builds.svc/GetLatestVersion): shows the full version number of the latest release
- [Get URL of Latest Version](http://apsimdev.apsim.info/APSIM.Builds.Service/Builds.svc/GetURLOfLatestVersion?operatingSystem=Debian): shows the download URL for the latest version of the specified OS

`ApsimSetup*.deb` files are named using the [build.issueNumber](https://github.com/APSIMInitiative/APSIM.Builds/blob/21a8ac85a1d868a45f60a994a35a5d07dc04562a/APSIM.Builds.Service/Builds.svc.cs#L278) instead of the full version number, so we must hardcode the URLs inside the recipe files, while using the full version number for the recipe file names.

To facilitate running the container, a `/usr/local/bin/apsimmodels` file is created as the entrypoint using `/usr/local/bin/apsim` as a template.

## Container-specific notes

- ApsimX apparently needs `/etc/localtime` to run so we have to install `tzdata` as a dependency. We configure our local timezone, but this can be overridden at run time by exporting the `TZ` environment variable.
