# Prerequisite
1. Python2
2. Java
```sh
yum install -y python2 wget
Install java
```

# Install scheduler
```sh
wget -c https://apache.bintray.com/aurora/centos-7/aurora-scheduler-0.15.0-1.el7.centos.aurora.x86_64.rpm
sudo yum install -y aurora-scheduler-0.15.0-1.el7.centos.aurora.x86_64.rpm
```

# Install the client
```sh
wget -c https://apache.bintray.com/aurora/centos-7/aurora-tools-0.15.0-1.el7.centos.aurora.x86_64.rpm

sudo yum install -y aurora-tools-0.15.0-1.el7.centos.aurora.x86_64.rpm
```

# Install worker component
```sh
wget -c https://apache.bintray.com/aurora/centos-7/aurora-executor-0.15.0-1.el7.centos.aurora.x86_64.rpm

sudo yum install -y aurora-executor-0.15.0-1.el7.centos.aurora.x86_64.rpm
```

# Run aurora scheduler server
```sh
mesos-log initialize --path=/var/lib/aurora/scheduler/db

systemctl start aurora
```

# Run aurora observer
Port: 1338
```sh
./thermos_observer
```

# Aurora client test command
```sh
aurora job list devcluster
aurora job killall devcluster/root/devel/hello_world
aurora job create devcluster/root/devel/hello_world hello_world.aurora
```

# Configuration aurora
```
vi /etc/aurora/clusters.json
```
# /etc/sysconfig/aurora-scheduler
```
-mesos_master_address='172.17.0.2:5050'
-receive_revocable_resources=true
```
Run tomcat aurora 
```
aurora job create devcluster/root/devel/hello tomcat.aurora
```
