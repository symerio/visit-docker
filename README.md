# visit-docker

A docker setup for VisIt (https://wci.llnl.gov/simulation/computer-codes/visit/)


# visit-docker

A docker setup for VisIt (https://wci.llnl.gov/simulation/computer-codes/visit/)


To start visit,

 1. Allow the root user to make connections to the running X server with,
    ```
    xhost +local:root;
    ```
    (see [xhost man page](http://manpages.ubuntu.com/manpages/zesty/en/man1/xhost.1.html))
 2. Run the docker container,
    ```
    docker run -it -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix:rw symerio/visit
    ```

## FAQ

1. *How can I make settings persistant or give VisIt access to the data?*
  
   One can mount any local folder within the container with the
   ```
   -v /host/directory:/container/directory
   ```
   option. For instance, to provide the user settings, add,
   ```
   -v ~/.visit/:/root/.visit/
   ```
 2. *Which operating systems are supported?*
    
    So far this setup has been tested on Linux. It might possibly be made to work on Mac OS X.  

 3. *Can I use hardware acceleration in this setup?*

    So far OpenGL support is not working properly ( see  [symerio/visit-docker#1](https://github.com/symerio/visit-docker/issues/1) )

## Reporting issues

In encounter any problem please open a new issue on Github at https://github.com/symerio/visit-docker


## License

This Docker image is open-sourced under the 3-clause BSD Licence.
