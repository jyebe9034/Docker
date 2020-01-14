### cmd창을 열어 아래와 같이 진행하면 됨. 

```
C:\Users\jihye>docker images
REPOSITORY             TAG                 IMAGE ID            CREATED             SIZE
hannahlim/cheers2019   latest              9d9ef7500dff        23 hours ago        4.01MB
<none>                 <none>              e77b23d84780        23 hours ago        356MB
mysql                  latest              ed1ffcb5eff3        2 weeks ago         456MB
golang                 1.11-alpine         e116d2efa2ab        4 months ago        312MB

C:\Users\jihye>docker run 9d9ef7500dff
panic: exec: "infocmp": executable file not found in $PATH

goroutine 1 [running]:
main.main()
        /project/cheers.go:259 +0x9b9

C:\Users\jihye>docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                               NAMES
5a2ad1aa6054        mysql               "docker-entrypoint.s…"   17 hours ago        Up 17 hours         0.0.0.0:3306->3306/tcp, 33060/tcp   mysql_test

C:\Users\jihye>
```
