# Docker

### 첫번째 도커 특강 1월 8일 cmd 실습 
실행 명령어 : docker run [OPTIONS] IMAGE [COMMAND] [ARG...]

```
C:\Users\hsjang\WebstormProjects\jihye\vuetest>docker version
Client: Docker Engine - Community
 Version:           19.03.5
 API version:       1.40
 Go version:        go1.12.12
 Git commit:        633a0ea
 Built:             Wed Nov 13 07:22:37 2019
 OS/Arch:           windows/amd64
 Experimental:      false

Server: Docker Engine - Community
 Engine:
  Version:          19.03.5
  API version:      1.40 (minimum version 1.12)
  Go version:       go1.12.12
  Git commit:       633a0ea
  Built:            Wed Nov 13 07:29:19 2019
  OS/Arch:          linux/amd64
  Experimental:     false
 containerd:
  Version:          v1.2.10
  GitCommit:        b34a5c8af56e510852c35414db4c1f4fa6172339
 runc:
  Version:          1.0.0-rc8+dev
  GitCommit:        3e425f80a8c931f88e6d94a8c831b9d5aa481657
 docker-init:
  Version:          0.18.0
  GitCommit:        fec3683

C:\Users\hsjang\WebstormProjects\jihye\vuetest>docker run ubuntu:latest
Unable to find image 'ubuntu:latest' locally
latest: Pulling from library/ubuntu
2746a4a261c9: Pull complete                                                                                                      4c1d20cdee96: Pull complete                                                                                                      0d3160e1d0de: Pull complete                                                                                                      c8e37668deea: Pull complete                                                                                                      Digest: sha256:250cc6f3f3ffc5cdaa9d8f4946ac79821aafb4d3afc93928f0de9336eba21aa4
Status: Downloaded newer image for ubuntu:latest

C:\Users\hsjang\WebstormProjects\jihye\vuetest>docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                               NAMES

C:\Users\hsjang\WebstormProjects\jihye\vuetest>docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
ubuntu              latest              549b9b86cb8d        2 weeks ago         64.2MB

C:\Users\hsjang\WebstormProjects\jihye\vuetest>docker rmi ubuntu:latest
Error response from daemon: conflict: unable to remove repository reference "ubuntu:latest" (must force) - container 19cfebba0f6e is using its referenced image 549b9b86cb8d

C:\Users\hsjang\WebstormProjects\jihye\vuetest>docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED              STATUS                          PORTS                               NAMES
19cfebba0f6e        ubuntu:latest       "/bin/bash"              About a minute ago   Exited (0) About a minute ago                                       sweet_shtern

C:\Users\hsjang\WebstormProjects\jihye\vuetest>docker run 19cfebba0f6e
Unable to find image '19cfebba0f6e:latest' locally
docker: Error response from daemon: pull access denied for 19cfebba0f6e, repository does not exist or may require 'docker login': denied: requested access to the resource is denied.
See 'docker run --help'.

C:\Users\hsjang\WebstormProjects\jihye\vuetest>docker rm 19cfebba0f6e
19cfebba0f6e

C:\Users\hsjang\WebstormProjects\jihye\vuetest>docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                               NAMES

C:\Users\hsjang\WebstormProjects\jihye\vuetest>docker run -d --name redis redis
Unable to find image 'redis:latest' locally
latest: Pulling from library/redis
8ec398bc0356: Pull complete                                                                                                      da01136793fa: Pull complete                                                                                                      cf1486a2c0b8: Pull complete                                                                                                      a44f7da98d9e: Pull complete                                                                                                      c677fde73875: Pull complete                                                                                                      727f8da63ac2: Pull complete                                                                                                      Digest: sha256:90d44d431229683cadd75274e6fcb22c3e0396d149a8f8b7da9925021ee75c30
Status: Downloaded newer image for redis:latest
141c418a63214809236a1d1e2896127cdd08c27112ed6f8f69355589ef51ebcd

C:\Users\hsjang\WebstormProjects\jihye\vuetest>docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                               NAMES
141c418a6321        redis               "docker-entrypoint.s…"   9 seconds ago       Up 8 seconds        6379/tcp                            redis

C:\Users\hsjang\WebstormProjects\jihye\vuetest>docker exec -it redis /bin/bash
root@141c418a6321:/data# ls
root@141c418a6321:/data# cd ..
root@141c418a6321:/# ls
bin  boot  data  dev  etc  home  lib  lib64  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
root@141c418a6321:/# ls -al
total 76
drwxr-xr-x   1 root  root  4096 Jan  8 06:47 .
drwxr-xr-x   1 root  root  4096 Jan  8 06:47 ..
-rwxr-xr-x   1 root  root     0 Jan  8 06:47 .dockerenv
drwxr-xr-x   2 root  root  4096 Dec 24 00:00 bin
drwxr-xr-x   2 root  root  4096 Nov 10 12:17 boot
drwxr-xr-x   2 redis redis 4096 Jan  3 01:29 data
drwxr-xr-x   5 root  root   340 Jan  8 06:47 dev
drwxr-xr-x   1 root  root  4096 Jan  8 06:47 etc
drwxr-xr-x   2 root  root  4096 Nov 10 12:17 home
drwxr-xr-x   1 root  root  4096 Jan  3 01:29 lib
drwxr-xr-x   2 root  root  4096 Dec 24 00:00 lib64
drwxr-xr-x   2 root  root  4096 Dec 24 00:00 media
drwxr-xr-x   2 root  root  4096 Dec 24 00:00 mnt
drwxr-xr-x   2 root  root  4096 Dec 24 00:00 opt
dr-xr-xr-x 146 root  root     0 Jan  8 06:47 proc
drwx------   1 root  root  4096 Dec 29 00:04 root
drwxr-xr-x   3 root  root  4096 Dec 24 00:00 run
drwxr-xr-x   2 root  root  4096 Dec 24 00:00 sbin
drwxr-xr-x   2 root  root  4096 Dec 24 00:00 srv
dr-xr-xr-x  13 root  root     0 Jan  8 06:47 sys
drwxrwxrwt   1 root  root  4096 Jan  3 01:29 tmp
drwxr-xr-x   1 root  root  4096 Dec 24 00:00 usr
drwxr-xr-x   1 root  root  4096 Dec 24 00:00 var
root@141c418a6321:/# redis-cli
127.0.0.1:6379> help
redis-cli 5.0.7
To get help about Redis commands type:
      "help @<group>" to get a list of commands in <group>
      "help <command>" for help on <command>
      "help <tab>" to get a list of possible help topics
      "quit" to exit

To set redis-cli preferences:
      ":set hints" enable online hints
      ":set nohints" disable online hints
Set your preferences in ~/.redisclirc
127.0.0.1:6379> set name TEST
OK
127.0.0.1:6379> keys *
1) "name"
127.0.0.1:6379> get name
"TEST"
127.0.0.1:6379> exit
root@141c418a6321:/# exit
exit

C:\Users\hsjang\WebstormProjects\jihye\vuetest>docker run -d --name redis2 -p 6379:6379 redis
9c390dbc4d3f94c936aab22cf6b4476e24bb41caba7df69d41713a8c72ab8b2e

C:\Users\hsjang\WebstormProjects\jihye\vuetest>docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                               NAMES
9c390dbc4d3f        redis               "docker-entrypoint.s…"   10 seconds ago      Up 9 seconds        0.0.0.0:6379->6379/tcp              redis2
141c418a6321        redis               "docker-entrypoint.s…"   7 minutes ago       Up 7 minutes        6379/tcp                            redis

C:\Users\hsjang\WebstormProjects\jihye\vuetest>docker run -d --name nginx2 -p 8090:80 -v /c/nginx:/usr/share/nginx/html nginx
c7937e930ef1acc694edcb49f2b954dbeb5ca150e6e297a0ea21ae516c142c4f

C:\Users\hsjang\WebstormProjects\jihye\vuetest>cd..

C:\Users\hsjang\WebstormProjects\jihye>cd..

C:\Users\hsjang\WebstormProjects>cd..

C:\Users\hsjang>cd..

C:\Users>cd.

C:\>cd nginx

C:\nginx>docker build -t mynginx:v1 .
Sending build context to Docker daemon  3.072kB
Step 1/2 : FROM nginx:alpine
alpine: Pulling from library/nginx
89d9c30c1d48: Pull complete                                                                                                      24f1c4f0b2f4: Pull complete                                                                                                      Digest: sha256:0e61b143db3110f3b8ae29a67f107d5536b71a7c1f10afb14d4228711fc65a13
Status: Downloaded newer image for nginx:alpine
 ---> a624d888d69f
Step 2/2 : COPY . /usr/share/nginx/html
 ---> 66451b1eeaca
Successfully built 66451b1eeaca
Successfully tagged mynginx:v1
SECURITY WARNING: You are building a Docker image from Windows against a non-Windows Docker host. All files and directories added to build context will have '-rwxr-xr-x' permissions. It is recommended to double check and reset permissions for sensitive files and directories.

C:\nginx>docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
mynginx             v1                  66451b1eeaca        33 seconds ago      21.5MB
redis               latest              9b188f5fb1e6        5 days ago          98.2MB
nginx               latest              f7bb5701a33c        10 days ago         126MB
ubuntu              latest              549b9b86cb8d        2 weeks ago         64.2MB
mysql               latest              d435eee2caa5        6 weeks ago         456MB
nginx               alpine              a624d888d69f        7 weeks ago         21.5MB

C:\nginx>docker run -d -p 8888:80 mynginx:v1
d4c89928d7d9fe4e66df9fe558436d668951f01dd1f0666953a8658417fac5c3

C:\nginx>docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED              STATUS              PORTS                               NAMES
d4c89928d7d9        mynginx:v1          "nginx -g 'daemon of…"   About a minute ago   Up About a minute   0.0.0.0:8888->80/tcp                confident_torvalds
c7937e930ef1        nginx               "nginx -g 'daemon of…"   12 minutes ago       Up 12 minutes       0.0.0.0:8090->80/tcp                nginx2
9c390dbc4d3f        redis               "docker-entrypoint.s…"   24 minutes ago       Up 24 minutes       0.0.0.0:6379->6379/tcp              redis2
141c418a6321        redis               "docker-entrypoint.s…"   31 minutes ago       Up 31 minutes       6379/tcp                            redis

C:\nginx>docker stop d4c89928d7d9
d4c89928d7d9

C:\nginx>docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                               NAMES
c7937e930ef1        nginx               "nginx -g 'daemon of…"   12 minutes ago      Up 12 minutes       0.0.0.0:8090->80/tcp                nginx2
9c390dbc4d3f        redis               "docker-entrypoint.s…"   24 minutes ago      Up 24 minutes       0.0.0.0:6379->6379/tcp              redis2
141c418a6321        redis               "docker-entrypoint.s…"   31 minutes ago      Up 31 minutes       6379/tcp                            redis

C:\nginx>docker c7937e930ef1
docker: 'c7937e930ef1' is not a docker command.
See 'docker --help'

C:\nginx>docker stop c7937e930ef1
c7937e930ef1

C:\nginx>docker stop 9c390dbc4d3f
9c390dbc4d3f

C:\nginx>docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                               NAMES
141c418a6321        redis               "docker-entrypoint.s…"   32 minutes ago      Up 32 minutes       6379/tcp                            redis

C:\nginx>docker stop 141c418a6321
141c418a6321

C:\nginx>docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                               NAMES

C:\nginx>docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS                          PORTS                               NAMES
d4c89928d7d9        mynginx:v1          "nginx -g 'daemon of…"   3 minutes ago       Exited (0) About a minute ago                                       confident_torvalds
c7937e930ef1        nginx               "nginx -g 'daemon of…"   13 minutes ago      Exited (0) About a minute ago                                       nginx2
9c390dbc4d3f        redis               "docker-entrypoint.s…"   25 minutes ago      Exited (0) 47 seconds ago                                           redis2
141c418a6321        redis               "docker-entrypoint.s…"   32 minutes ago      Exited (0) 22 seconds ago                                           redis

C:\nginx>docker rm d4c89928d7d9
d4c89928d7d9

C:\nginx>docker rm c7937e930ef1
c7937e930ef1

C:\nginx>docker rm 9c390dbc4d3f
9c390dbc4d3f

C:\nginx>docker rm 141c418a6321
141c418a6321

C:\nginx>docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                               NAMES
```
