# rhub package
used to check a package on different systems via: [rhub](https://builder.r-hub.io/)

## commands

* `check_on_...()` starts a check for ... (windows, linux, osx, ...)
* `list_last_checks()` easy 

## Debug

If there are errors on specific systems:

* search for the docker container on: [rhub-docker](https://hub.docker.com/u/rhub)
    * **no windows** containers though
* `docker.pull rhub/<url>`
* `docker run -ti rhub/<url> bash`
* install dependencies (git, etc)
* clone repo
* `/opt/R-devel/bin/R -R 'install.packages("devtools")'`
* `/opt/R-devel/bin/R -R 'devtools::install_dev_deps()'`
* `docker commit`
* `/opt/R-devel/bin/R -R 'devtools::check()'`

## other dependencies 

If there are other things needed on the box.

DESCRIPTION:

```
remotes:
  r-lib/callr,
  github-user/repo  
SystemRequirements:
  libcurl: libcurl-devel  
  libcurl4-openssl-dev
```

Possible SystemRequirements in: [sysreqs](https://sysreqs.r-hub.io/).

