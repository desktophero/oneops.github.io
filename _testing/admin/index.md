---
title: "Testing and Debugging"
id: "testing-and-debugging"
---
As an admin become familiar with OneOps architecture

# Testing
* Build a *test* environment where you can test any new OneOps code changes and also validate any or new *pack* changes your organization might do.

# Debugging

## UI not coming up
  * Make sure the **apache** is up if running *display* in apache.
  * Run `nc -v host port` to see if the ports are not blocked. Do this for any of the  services.

## Deployments failing
  * Check if all consumers can connect to messaging bus.
  * All the oneops webapps( adapter,transistor) expose health check /rest/<context>/ecv/status.. so check if all web contexts are up.

## Inductor not coming up
* Make sure the *auth-key* is same which you used for setting up the cloud.


### UI does not come up on AWS image.
Most likely the rails server didn't start properly, try to ssh to your vm and do

```bash
 sudo service display start
 # check the logs
 tail -f /opt/oneops/log/rails.log
```   


## Deployment fails on AWS image

1. Update [cookbooks](https://github.com/oneops/circuit-oneops-1/tree/master/components/cookbooks) to latest and greatest.

``` bash
cd /home/oneops/build/circuit-oneops-1
git remote -v
  #  if its like git@oogit:/oneops/circuit-oneops-1 (fetch), replace with https
sudo git remote set-url origin https://github.com/oneops/circuit-oneops-1.git  
# Get the latest
sudo git pull
#If there are merge conflicts, resolve them  or want to overwrite with the latest
#This *replaces* all the cookbooks used by inductor to the latest in sync with github
sudo git reset --hard origin/master
## refer ls -la /opt/oneops/inductor

#For *shared cookbooks*, we can do the same
cd /home/oneops/build/oneops-admin
sudo git pull
## If conflicts and want to overwrite
sudo git reset --hard origin/master
sudo cp -r /home/oneops/build/oneops-admin/lib/shared /opt/oneops/inductor
```
