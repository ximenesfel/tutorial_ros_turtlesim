
- [Ambiente testado](#Ambiente-testado)
- [Instalação](#Instalação)
- [Uso](#Uso)

# Ambiente testado

- Ubuntu 18.04



# Instalação

- Instalar o docker no computador:

```
sudo apt-get install curl
curl -fsSL https://get.docker.com -o get-docker.sh
sh get-docker.sh
```

- Realizar esses passos para rodar o docker sem a necessidade do root:

```
sudo groupadd docker
sudo usermod -aG docker "usuario" (Trocar "usuario" pelo nome do seu usuário. Ex: sudo usermod -aG docker ximenes)
```

- Reiniciar o pc para validar a associação acima.

- Instalar o docker-compsoe no computador:

```
sudo apt-get install -y python3-pip
sudo python3 -m pip install docker-compose
```

- Clonar o código no seu pc:

```
sudo apt-get install -y git
git clone https://github.com/ximenesfel/tutorial_ros_turtlesim.git
cd tutorial_ros_turtlesim
```
- Realizar o build da imagem do docker. Esse passo demora um pouco !!!!

```
docker-compose build
```

- Rodar o docker container:

```
docker-compose up -d
```

- Verificar se o docker está rodando corretamente:

```
docker-compose ps
```
Resposta do comando se tiver rodando corretamente.
```

            Name                       Command           State   Ports
----------------------------------------------------------------------
tutorial_ros_turtlesim_ros_1   /ros_entrypoint.sh bash   Up 
```

- Acessar o docker container:

```
docker-compose exec ros bash
```


# Uso

- Rodar este comando no terminal:

```
xhost +local:root
```

- Acessar o docker container e rodar o roscore:

```
docker-compose exec ros bash 

root@46ef30c4b5eb:~# roscore
```

**Saída**

```
root@46ef30c4b5eb:~# roscore
... logging to /root/.ros/log/2b9ea84c-a523-11ea-a76b-0242ac1a0002/roslaunch-46ef30c4b5eb-226.log
Checking log directory for disk usage. This may take a while.
Press Ctrl-C to interrupt
Done checking log file disk usage. Usage is <1GB.

started roslaunch server http://46ef30c4b5eb:41597/
ros_comm version 1.14.5


SUMMARY
========

PARAMETERS
 * /rosdistro: melodic
 * /rosversion: 1.14.5

NODES

auto-starting new master
process[master]: started with pid [236]
ROS_MASTER_URI=http://46ef30c4b5eb:11311/

setting /run_id to 2b9ea84c-a523-11ea-a76b-0242ac1a0002
process[rosout-1]: started with pid [247]
started core service [/rosout]
```

- Abrir outro termininal, acessar o docker container e rodar o turtlesim:

```
docker-compose exec ros bash  (Acessar o docker container)
root@46ef30c4b5eb:~# rosrun turtlesim turtlesim_node (rodar o turtlesim)
```

**Saída**

```
root@46ef30c4b5eb:~# rosrun turtlesim turtlesim_node
QStandardPaths: XDG_RUNTIME_DIR not set, defaulting to '/tmp/runtime-root'
[ INFO] [1591138378.877094992]: Starting turtlesim with node name /turtlesim
[ INFO] [1591138378.881619179]: Spawning turtle [turtle1] at x=[5.544445], y=[5.544445], theta=[0.000000]
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
```

- O turtlesim vai aparecer.

![](https://i.imgur.com/LjndADb.png)