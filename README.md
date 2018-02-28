# google-cloud-compute-auto-manage-snapshots
A project to take and manage daily snapshots of all your gcp instances

# Function
Take one snapshot of every instance in your project once every day
Then as time goes delete snapshots.

# Cleaning of old snapshots
All snapshots are kept for 7 days. After 7 Days snapshots made on Tuesdays and Fridays are kept the rest gets removed. After 31 days snapshots made on Tuesdays are kept the rest gets removed. After 100 days all the snapshots are cleared.

# How to use
1. Create an instance on GCP give it read/write access to compute engine
1. ssh in to the instance:
1. cd /opt
1. git clone https://github.com/callesg/google-cloud-compute-auto-manage-snapshots
1. crontab -e


create cronjob entrys:
```cronjob
25      01      *       *       *       /usr/bin/php /opt/google-cloud-compute-auto-manage-snapshots/manage_snapshots.php take
25      05      *       *       *       /usr/bin/php /opt/manage_snapshots/manage_snapshots.php free_old
```

It will use the rights given to the GCP instance so no credential configuration is required. 
