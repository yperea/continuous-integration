# Installing Tomcat as a Service on Linux Ubuntu

## Steps
1. Create the init script in /etc/init.d/tomcat

```sudo nano /etc/init.d/tomcat```

2. Copy and paste the information below. Verify the path for startup.sh and shutdown.sh
```
#!/bin/bash

### BEGIN INIT INFO
# Provides: tomcat
# Required-Start: $network
# Required-Stop: $network
# Default-Start: 2 3 4 5
# Default-Stop: 0 1 6
# Short-Description: Start/Stop Tomcat server
### END INIT INFO

PATH=/sbin:/bin:/usr/sbin:/usr/bin

start() {
sh /opt/tomee/bin/startup.sh
}

stop() {
sh /opt/tomee/bin/shutdown.sh
}

case $1 in
start|stop) $1;;
restart) stop; start;;
*) echo "Run as $0 "; exit 1;;
esac
exit 0
```
3. Save the changes and close the file

4. Change the permissions

```sudo chmod 755 /etc/init.d/tomcat```

5. Update symlinks

```sudo update-rc.d tomcat defaults```

Now tomcat will start when your system starts and you can control it with service tomcat <stop|start|restart>.

----

Extracted from http://www.linuxandubuntu.com/home/how-to-run-tomcat-server-at-startup-on-ubuntu-server.