## EC2 User-data
```
#!/bin/bash -ex
yum -y update
yum -y install httpd php mysql php-mysql git
systemctl enable httpd
systemctl start httpd
cd /var/www/html
git clone https://github.com/MamNonDevOps/php-testing-scaling.git
rsync -a php-testing-scaling/* .
rm -rf php-testing-scaling
chown apache:root /var/www/html/rds.conf.php
```
## EC2 User-data Stress CPU
```
#!/bin/bash -ex
amazon-linux-extras install epel -y
yum install stress -y
```

```
stress --cpu 2 --timeout 60
```
