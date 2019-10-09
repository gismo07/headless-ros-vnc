# Headless ROS environment
Jumpstart ROS developent with no headache! Full browser support. OpenGL support with no need of a physically atachted GPU.

>>Attention: the project is still under development. There may be gaps in the manual. Don't forget to mount the appropriate volumes to prevent data loss!

## Included

### ROS
 - full ros distro (currently melodic)
 - rqt and all plugins
 - rviz

### IDE
 - full python (2.7) environment
 - jupyter lab
 - visual studio code server

## Start the service
There are two options to start `headless-ros-vnc`:

Via `docker run`:
```
docker run -itd -p 80:8080 -p 5900:5900 -p 6080:6080 --rm johannhaselberger/headless-ros-vnc
```
Or `docker-compose`
```
docker-compose up -d
``` 

 ## Access the environment
  - to open the IDE, simply open the browser and go to `localhost:80`. The password is currently set to `dev@ros`. 
  - to see rviz or some other gui stuff, open another browser tab `localhost:6080/vnc.html` and click connect.

## Configuration
The environment comes shipped with a `docker-compose.yaml` to start the service and manage some parameters:

```yaml
version: '3.7'
services:
    headless-ros-vnc:
        ports:
            - '80:8080'
            - '5900:5900'
            - '6080:6080'
        image: johannhaselberger/headless-ros-vnc
```

Headless-ros-vnc makes use of three open ports:
 - `8080`: access to visual studio code server
 - `5900`: the default vnc port (could be theoretically accessed with any vnc client, however, as the port is forwarded via noVNC that's not intended)
 - `6080`: access to the novnc web interface

 **Important:** for each instance of `headless-ros-vnc` these ports have to be asigned to available host-ports!