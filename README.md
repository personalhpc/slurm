# Install and configure SLURM on Ubuntu 16.04 Personal HPC computers

```sh
sudo apt update
sudo apt install -y munge libmunge2
sudo apt install -y slurm-wlm slurm-wlm-basic-plugins
sudo chown ubuntu /var/log/slurm-llnl
sudo chown ubuntu /var/lib/slurm-llnl/slurmctld
sudo chown ubuntu /var/run/slurm-llnl
```

at this point one needs to create and edit the configuration file of slurm, called (in ubuntu 16.04) `sudo vim /etc/slurm-llnl/slurm.conf`
An example is given with this folder.
Then, start the master and slave deamons:

```sh
sudo /etc/init.d/slurmctld start
sudo /etc/init.d/slurmd start
```

to be checked with 

```sh
sinfo
```

