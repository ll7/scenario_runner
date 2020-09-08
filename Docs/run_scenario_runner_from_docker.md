#Running CARLA container
This documentation describes what docker is, how you can install it and pull the CARLA image 0.9.9. 

Unfortunately, we got an error by executing the docker image which we couldn't solve. That's why till now it is just an Outlook for further work.

##1 What is Docker?
Docker is an open platform for developing, shipping, and running applications. Docker enables you to separate your applications from your infrastructure so you can deliver software quickly. 

With Docker, you can manage your infrastructure in the same ways you manage your applications. By taking advantage of Docker’s methodologies for shipping, testing, and deploying code quickly, you can significantly reduce the delay between writing code and running it in production.

For more information about
- the platform,
- the engine,
- its usage,
- its architecture, 
- etc. 

have a look on the following [Link](https://docs.docker.com/get-started/overview/).

##2 Install Docker on Ubuntu
To install Docker on Ubuntu follow the instructions on the following [Link](https://docs.docker.com/engine/install/ubuntu/).

To test if the installation was correctly enter the following command:
```
$ sudo docker run hello-world
```

If your installation worked correctly you will get the following message:
```
Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

[...]
```

##3 Install Nvidia-Docker

Similarly to Docker installation, start by setting the GPG and remote repo for the package
```
$ curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | \
  sudo apt-key add -
distribution=$(. /etc/os-release;echo $ID$VERSION_ID)
curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | \
  sudo tee /etc/apt/sources.list.d/nvidia-docker.list
```

Then update the apt lists
```
$ sudo apt-get update
```

Now you install nvidia-docker (2) and reload the Docker daemon configurations
```
$ sudo apt-get install -y nvidia-docker2
$ sudo pkill -SIGHUP dockerd
```

Nvidia GPUs first require drivers to be installed. Here is how you make sure they are installed 
```
$ sudo apt-get remove nvidia -384 ; sudo apt-get install nvidia-384
```

Now, the only thing left to do is test your environment and to make sure everything is installed correctly. Just simply launch the nvidia-smi (system management interface) application.
```
$ docker run --runtime=nvidia --rm nvidia/cuda:9.0-base nvidia-smi
```

The output should look something like this:
```
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 390.77                 Driver Version: 390.77                    |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  Tesla K80           Off  | 00000000:00:1E.0 Off |                    0 |
| N/A   39C    P0    83W / 149W |      0MiB / 11441MiB |     98%      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|  No running processes found                                                 |
+-----------------------------------------------------------------------------+

Congrats! You have successfully installed Docker and Nvidia-Docker in your environment.
```


##4 Running Carla container in theory (Outlook)
After we installed,
- Docker and 
- nvidia-docker-2

you can now follow the instructions [Running CARLA container](https://carla.readthedocs.io/en/latest/build_docker/).

In brief:

Pull the CARLA image (with the desired version).
```
docker pull carlasim/carla:0.9.9
```

Running CARLA under docker.
```
docker run -p 2000-2002:2000-2002 --runtime=nvidia --gpus all carlasim/carla:0.9.9
```

Unfortunately after running the command above you get the following error message:

```
sh: 1: xdg-user-dir: not found
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:4292:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:4292:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:4292:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4771:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2266:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:4292:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:4292:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:4292:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4771:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2266:(snd_pcm_open_noupdate) Unknown PCM default
```

If an idea for this is found I would like to be informed! Thanks!

We also created an open issue for this on github: [Running CARLA from Docker failed](https://github.com/carla-simulator/carla/issues/3270).