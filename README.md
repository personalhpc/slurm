# Install and configure SLURM on Ubuntu 16.04 Personal HPC computers

```sh
sudo apt update
sudo apt install -y munge libmunge2
sudo apt install -y slurm-wlm slurm-wlm-basic-plugins
```

at this point one needs to create and edit the configuration file of slurm, called (in ubuntu 16.04). A default slurm.conf is given in this github repo. You have to modify it to make things work  :
1. First, open the configuration file with `sudo vim /etc/slurm-llnl/slurm.conf`
2. Look for keyword "phpc64a" and replace it everywhere (3 times) by the name of your server. If it is called "myserver" then replace phpc64a with myserver.  
3. Look for keyword "ubuntu" and replace it with the username of the administrator's login. If the administrator login is "toto", then replace "ubuntu" by "toto".

Save and quit, then (where you replace ubuntu by toto or whatever username you gave):
```sh
sudo chown ubuntu /var/log/slurm-llnl
sudo chown ubuntu /var/lib/slurm-llnl/slurmctld
sudo chown ubuntu /var/run/slurm-llnl
```


Then, start the master and slave deamons:

```sh
sudo /etc/init.d/slurmctld start
sudo /etc/init.d/slurmd start
```

to be checked with 

```sh
sinfo
```

