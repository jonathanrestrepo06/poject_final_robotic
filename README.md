# Simulacion de un drone en gazebo

## instalar gazebo 11 
http://gazebosim.org/tutorials?tut=install_from_source&cat=install

## instalar ardupilot 
https://ardupilot.org/dev/docs/building-setup-linux.html

## instalar ros
http://wiki.ros.org/noetic/Installation/Ubuntu

## instalar mavros/mavlink
https://github.com/mavlink/mavros/blob/master/mavros/README.md#installation

## descargar repositorio
1- abrir catkin_ws/src en el terminal

2- clonar mi repositorio

3- cd catkin_ws

4- catkin build

5- gedit ~/.bashrc

6- al final agrega estas líneas

** ros path 

  export ROS_PACKAGE_PATH=/catkin_ws/src/gazebo_apm_mavros/:$ROS_PACKAGE_PATH
  
  export ROS_PACKAGE_PATH=/catkin_ws/src/mavros/mavros:$ROS_PACKAGE_PATH
  
** gazebo path 

  export GAZEBO_RESOURCE_PATH=~/catkin_ws/src/gazebo_apm_mavros/worlds:${GAZEBO_RESOURCE_PATH}
  
  export GAZEBO_MODEL_PATH=~/catkin_ws/src/gazebo_apm_mavros/models:${GAZEBO_MODEL_PATH}
  
  export GAZEBO_PLUGIN_PATH=~/catkin_ws/src/gazebo_apm_mavros/build:${GAZEBO_PLUGIN_PATH}
  
  export GAZEBO_PLUGIN_PATH=~/catkin_ws/src/gazebo_apm_mavros/src:${GAZEBO_PLUGIN_PATH}
  
7- ctrl+s y cerrar

8- source ~/.bashrc

9- abrir scripts en el terminal

10- chmod +x obstacle_avoidance.py             # para darle permiso para ejecutarse, se hará esto para todos los módulos de Python #

11- nota:-abra el archivo apm.launch desde mavros y cambie la conexión FCU_URL a udp como "udp: //: 14550 @ 192.168.1.130@5760"

           o mire http://wiki.ros.org/mavros
          
## Simulacion
### abrir 4 terminales agregue cada una agregue estas líneas en orden y espere hasta que se inicie
- primero: roslaunch gazbo obstacle_avoidance.launch

- segundo: sim_vehicle.py -v ArduCopter -f gazebo-iris -I0

- tercero: roslaunch mavros apm.launch

- cuarto: rosrun gazbo obstacle_avoidance.py

# Mover a nueva ubicacion
- primero: roslaunch gazbo grass.launch

- segundo: sim_vehicle.py -v ArduCopter -f gazebo-iris -I0

- tercero: roslaunch mavros apm.launch

- cuarto: rosrun gazbo move_nesw_localy.py

