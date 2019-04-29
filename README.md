fab-server setup
================
![fab-server](images/fab-server-v2.png)

## Dev VM
This is the VM that contains the Contrail developer sandbox Docker container. Here are the steps to get into the dev VM as root user: 
```
$ cd /root/fab-server-setup/dev_vm
$ vagrant ssh
$ su
password: vagrant
```
Once inside the dev VM as root, here are the steps to get into developer sandbox Docker container and run `scons` to build Contrail
```
$ docker exec -it contrail-developer-sandbox bash
$ cd /root/contrail
$ scons
```

To start the sandbox VM if it is down. 
```
$ docker restart contrail-developer-sandbox
```

## Contrail all_in_one VM
Here are the steps to create target VM loaded with Contrail nightly build:
1. Destroy the existing vagrant VM
```
$ cd /root/fab-server-setup/all_in_one
$ vagrant destroy
```
2. Go to https://hub.docker.com/r/opencontrailnightly/contrail-openstack-neutron-init/tags/ and copy the tag name for the nightly build. Or you can use tag name `latest` for the latest nightly build.
3. Run `create_contrail_vm.sh` script to spawn the VM loaded with the nightly build
```
$ cd /root/fab-server-setup/all_in_one
$ sh create_contrail_vm.sh <tag name>
```

#### How do I access the VM?
To access the VM from the fab-server:
```
$ cd /root/fab-server-setup/all_in_one
$ vagrant ssh
$ su
password: vagrant
```

## Debug API server
Here is WIKI for debugging API server container: https://github.com/jnpr-tjiang/fab-server-setup/wiki/Debug-API-server
