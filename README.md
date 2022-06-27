# Launch an app automatically
A very basic example of creating a bash script that could launch a 3. party application.
Requires some knowledge of Wago controllers. 


## Create script

Log in as root and create a script in init.d called here "startmyapp", and make it executable:
```
touch /etc/init.d/startmyapp
chmod +x /etc/init.d/startmyapp
```

Edit and add the fallowing lines. Change path and 3. party "APP" to wathever application on what path that should be started.
E.g. /home/apps/bin:
```
#!/bin/sh
PATH=/home/apps/bin:$PATH
NAME=myapp
APP start --name $NAME > /home/apps/mylog.log 2>&1
exit 0
```

Create a symlink in rc.d:
```
ln -s /etc/init.d/startmyapp /etc/rc.d/S99_zz_startmyapp
```

## Test

Run the script /etc/init.d/startmyapp or restart the controller. 
Check logfile for output. 
