
# How to install Splunk Enterprise in linux server

Enter the below commands in respective command prompt.

## Step-1 : Become root user
Login as "root" user using below command
```bash
Type : sudo su 

```
## Step-2 : Create new user (eg:splunk), directories & permissions

Create user & group

```bash
Type : useradd splunk

Type : groupadd splunk

```
Create directory
```bash
Type : mkdir /opt/splunk
```

Change the ownership of the created directory to the new user **"splunk"** (hereafter will be called as splunk user)

```bash
Type : chown -R splunk:splunk /opt/splunk/
```


If you want to Verify the ownership of the directory
```bash
Type : ll /opt/splunk
```

Install **"wget"**
```bash
Type : yum install wget
```

## Step-3 : Splunk Enterprise Installation

Switch to splunk user 
```bash
Type : sudo su - splunk
```

Navigate to splunk user home directory
```bash
Type : cd /home/splunk
```

Download Splunk (Based on the version you want, you can get this command from https://www.splunk.com/en_us/download/splunk-enterprise/thank-you-enterprise.html)
```bash
wget -O splunk-9.0.1-82c987350fde-Linux-x86_64.tgz "https://download.splunk.com/products/splunk/releases/9.0.1/linux/splunk-9.0.1-82c987350fde-Linux-x86_64.tgz"
```

Extract the tar package
```bash
Type : tar -xvf splunk-9.0.1-82c987350fde-Linux-x86_64.tgz -C /opt/
```

Navigate to Splunk bin directory
```bash
Type : cd /opt/splunk/bin
```

Start the Splunk with accepting license
```bash
Type :  ./splunk start --accept-license
```

**Note:** In above step installer will ask you to create username and password, please keep these credentials safe (These are the admin credentials which you will use to Manage Splunk)

At this point, open your browser and check the link: http://<....public_ip_address....>:8000

Splunk login screen will popup..

## Step-4: Configure Splunk to run at boot time

Exit from splunk user & sign in as **root** user
``` bash
exit
sudo su 
```

Enable boot start
``` bash
/opt/splunk/bin/splunk enable boot-start -username splunk
```

That's it... you have successfully installed Splunk on Linux..!!

Happy Splunking..!!



-Thilakraj Shekar