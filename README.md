<h1 align="center">Expo CLI - Docker</h1>
<h4 align="center">Sample set up of Expo within a Docker environment</h4>

# Table of Contents
- [Requirements](#requirements)
- [Common Issues and Workarounds](#common-issues-and-workarounds)
    - [Metro Bundler](#metro-bundler)
    - [Local Area Network (LAN) Host Name](#lan)
- [Additional Resources](#additional-resources)

## Requirements
- [Docker] Engine version 18.06.0+
- [Docker-Compose] version 1.22.0+

## Common Issues and Workarounds
### Metro Bundler
```bash
Could not get status from Metro bundler. connect ECONNREFUSED 127.0.0.1:19003
Connecting to Metro bundler failed.
```

__Workaround__: Removing the `.expo` directory `rm -rf .expo` and 
killing processes within the Docker container that
relate to the __expo or yarn commands or the project directory__
`ps au` will display all processes and `kill -9 PID`
will kill the process(es).

```bash
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root       261  0.2  2.6 882240 54408 pts/1    Sl+  06:52   0:03 node /usr/local/bin/yarn ios
root       272  0.0  0.0   4280   748 pts/1    S+   06:52   0:00 /bin/sh -c expo start --ios
root       273  0.0  1.5 563424 31140 pts/1    Sl+  06:52   0:00 /usr/local/bin/node /expo_docker/CoolAppInit/nod
root       280  8.2  8.7 1006040 178688 pts/1  Sl+  06:52   2:11 /usr/local/bin/node /usr/local/bin/expo-cli star
root       324 14.7  8.6 998796 175856 pts/1   Sl+  06:52   3:54 /usr/local/bin/node /expo_docker/CoolAppInit/nod

```

### Local Area Network (LAN) Host Name<a id="lan"></a>

One can only connect to the Expo Server
when providing the host machine's IP address or host name<br/>
`MY_LAN_IP=123.456.789.1 docker-compose up -d`


## Additional Resources
- [React Native]
- [Expo]
- [Expo Documentation]


[Expo]:https://expo.io/
[Expo Documentation]:https://docs.expo.io/
[React Native]:https://reactnative.dev/docs/environment-setup
[Docker]: https://docs.docker.com/engine/reference/builder/#usage
[Docker-Compose]: https://docs.docker.com/compose/compose-file/