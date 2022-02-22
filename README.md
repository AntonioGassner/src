# README.md

## Installazione

### Requisiti

* Ubuntu 20.04 Focal Fossa
* ROS2 Foxy Fitzroy
* Gazebo simulator

### Step:

```bash
mkdir ~/project_ccc
cd ~/project_ccc/
git clone https://github.com/AntonioGassner/src.git
rosdep install --from-paths src --ignore-src -r -y rosdistro=foxy
colcon build

sudo nano ~/.bashrc

##scrivere sta roba dentro a .bashrc

export SVGA_VGPU10=0 
source /usr/share/colcon_cd/function/colcon_cd.sh
export _colcon_cd_root=~/ros2_install
alias python='python3.9' # Cambialo in base alla tua versione di Python
export GAZEBO_RESOURCE_PATH=/usr/share/gazebo-11
source DIRECTORY DEL PACCHETTO DI SIMULAZIONE (dovresti già averlo)
source ~/project_ccc/install/setup.bash

### RUN simulazione
(se sono state apportate modifiche ai file)
```bash
cd ~/project_ccc/
colcon build
export GAZEBO_MODEL_PATH=$GAZEBO_MODEL_PATH:<path_to_your_directory>/models
```

```bash
ros2 launch ccc_pkg simulation.launch.py
```

## RUN controller
```bash
ros2 launch ccc_pkg controllers.launch.py
```

### Organizzazione cartelle
    |_ launch/
    |_|__simulation.launch.py      #Lancia il simulatore e i nodi ros
    |_|__spawn_elements.py         #Prende un modello grafico e lo lancia nel simulatore
    |_models/                      #Contiene i file per descrivere l'aspetto di un robot
    |_src/                         #Può contenere script custom
    |_worlds/                      #Contiene i file che descrivono un mondo simulato
