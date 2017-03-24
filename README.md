# Setup and use environemnt-modules

Environment modules allows you easily switch between different versions of software by defining and modifying shell enviroment variables like PATH, LD_LIBRARY_PATH and any other defined variables


This docuemnt applied to ubuntu or debian

## Configure versions of software

For example we have two versions of cuda installed say 7.5 and 8.0, we need create definitions for the modules by create modulesfile for them.

* cuda/7.5

  Create a file under /etc/environment-modules/modules/cuda/7.5

  ```txt
  #%Module1.0#####################################################################
  ##
  ## modules cuda/7.5
  ##
  ##
  ##
  proc ModulesHelp { } {
          global version modroot
          puts stderr "cuda/7.5 - sets the Environment variables etc for cuda/7.5 in current shell"
  }

  module-whatis   "Sets the environment for using cuda-7.5"

  # for Tcl script use only
  set     topdir          /usr/loca/cuda-7.5
  set     version         7.5

  setenv          CPATH           $topdir/include
  prepend-path    PATH            $topdir/bin
  prepend-path    LD_LIBRARY_PATH $topdir/lib64

  ```
* cuda/8.0

  Create a file under /etc/environment-modules/modules/cuda/8.0

  ```txt
  #%Module1.0#####################################################################
  ##
  ## modules cuda/8.0
  ##
  ##
  ##
  proc ModulesHelp { } {
          global version modroot
          puts stderr "cuda/8.0 - sets the Environment variables etc for cuda/8.0 in current shell"
  }

  module-whatis   "Sets the environment for using cuda-8.0"

  # for Tcl script use only
  set     topdir          /usr/loca/cuda-8.0
  set     version         8.0

  setenv          CPATH           $topdir/include
  prepend-path    PATH            $topdir/bin
  prepend-path    LD_LIBRARY_PATH $topdir/lib64

  ```

## Typical commands

* Available modules
  ```bash
  module avail
  ```
* Load modules
  ```bash
  module load cuda/8.0
  ```
* Switch module between version
  ```bash
  module switch cuda/7.5
  ```
* Unload modules
  ```bash
  module unload cuda/7.5
  ```


## Reference

* gcc environment variables https://gcc.gnu.org/onlinedocs/gcc/Environment-Variables.html