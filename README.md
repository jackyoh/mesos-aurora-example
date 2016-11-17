Install Preparation
```
yum install -y python2 wget
Install java
```

Install scheduler
```
wget -c https://apache.bintray.com/aurora/centos-7/aurora-scheduler-0.15.0-1.el7.centos.aurora.x86_64.rpm

sudo yum install -y aurora-scheduler-0.15.0-1.el7.centos.aurora.x86_64.rpm
```


Install the client
```
wget -c https://apache.bintray.com/aurora/centos-7/aurora-tools-0.15.0-1.el7.centos.aurora.x86_64.rpm

sudo yum install -y aurora-tools-0.15.0-1.el7.centos.aurora.x86_64.rpm
```

Install worker component
```
wget -c https://apache.bintray.com/aurora/centos-7/aurora-executor-0.15.0-1.el7.centos.aurora.x86_64.rpm

sudo yum install -y aurora-executor-0.15.0-1.el7.centos.aurora.x86_64.rpm
```

Run aurora scheduler server
```
mesos-log initialize --path=/var/lib/aurora/scheduler/db

systemctl start aurora
```

Run aurora observer
Port:1338
```
./thermos_observer
```

Aurora client test command
```
aurora job list devcluster
aurora job killall devcluster/root/devel/hello_world
aurora job create devcluster/root/devel/hello_world hello_world.aurora
```

Configuration aurora
```
vi /etc/aurora/clusters.json
```
