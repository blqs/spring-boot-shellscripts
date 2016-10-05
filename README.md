# spring-boot-shellscripts
Bash scripts for spring boot applications like start/stop/status/logs executed from one place
Spring boot applications should be placed inside one directory (configured)

### Installing

1. Copy this script to directory with spring boot apps
  * as example /opt/spring-boot
2. Edit configuration at /opt/spring-boot/spring-boot-cfg
```
spring_boot_scripts= [custom scripts which should be added to default script - check spring-boot-mongo]
JAVA_CMD= [path to java]
```
3. Place your spring boot app inside /opt/spring-boot/
  * each spring boot app should have dedicated directory
  * each directory should contain just one file ending with .jar
  * if you have custom java opts place it inside spring app directory in java_opts file

### Usage
###### Help
```
user@host ~$ spring-boot
Additional scripts are used: mongo
Usage: ./spring-boot status
Usage: ./spring-boot [app_name] start|stop|status|logs|logfile
Available apps: app1 app2 app3
```

###### Status
```
user@host ~$ spring-boot status
Additional scripts are used: mongo
All spring-boot related apps on this server!
Status /opt/spring-boot/app1/app1-0.0.1.jar [app1]                                          [Running]
Status /opt/spring-boot/app2/app2-0.0.3.jar [app1]                                          [Running]
Status /opt/spring-boot/app3/app1-0.0.1-SNAPSHOT.jar [app1]                                 [Not running]
Status mongod [mongodb]                                                                     [Running]
```

###### Start
```
user@host ~$ spring-boot app3 start
Additional scripts are used: mongo
Starting /opt/spring-boot/app3/app3-0.0.1-SNAPSHOT.jar [app3]                              [OK]
```
You cannot start second time the same app
```
user@host ~$ spring-boot app3 start
Additional scripts are used: mongo
Starting /opt/spring-boot/app3/app3-0.0.1-SNAPSHOT.jar [app3]                              [Already running!]
```

###### Stop
```
user@host ~$ spring-boot app3 stop
Additional scripts are used: mongo
Stopping /opt/spring-boot/app3/app3-0.0.1-SNAPSHOT.jar [app3]                              [OK]
```
