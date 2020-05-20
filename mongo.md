    sudo systemctl status mongodb
    sudo systemctl stop mongodb
    sudo systemctl disable mongodb
    sudo systemctl status mongodb
  
    ps -ef | grep mongo
    ps -ef | grep mongod
  
    sudo systemctl daemon-reload
    sudo systemctl status mongod
    sudo systemctl enable mongod
    sudo systemctl restart mongod

https://docs.mongodb.com/manual/tutorial/install-mongodb-on-ubuntu/


Start MongoDB.
You can start the mongod process by issuing the following command:

sudo systemctl start mongod
If you receive an error similar to the following when starting mongod:

Failed to start mongod.service: Unit mongod.service not found.
Run the following command first:

sudo systemctl daemon-reload
Then run the start command above again.

2
Verify that MongoDB has started successfully.
sudo systemctl status mongod
You can optionally ensure that MongoDB will start following a system reboot by issuing the following command:

sudo systemctl enable mongod
3
Stop MongoDB.
As needed, you can stop the mongod process by issuing the following command:

sudo systemctl stop mongod
4
Restart MongoDB.
You can restart the mongod process by issuing the following command:

sudo systemctl restart mongod
You can follow the state of the process for errors or important messages by watching the output in the /var/log/mongodb/mongod.log file.

5
Begin using MongoDB.
Start a mongo shell on the same host machine as the mongod. You can run the mongo shell without any command-line options to connect to a mongod that is running on your localhost with default port 27017:

mongo
For more information on connecting using the mongo shell, such as to connect to a mongod instance running on a different host and/or port, see The mongo Shell.

To help you start using MongoDB, MongoDB provides Getting Started Guides in various driver editions. See Getting Started for the available editions.

Uninstall MongoDB Community Edition
To completely remove MongoDB from a system, you must remove the MongoDB applications themselves, the configuration files, and any directories containing data and logs. The following section guides you through the necessary steps.

WARNING

This process will completely remove MongoDB, its configuration, and all databases. This process is not reversible, so ensure that all of your configuration and data is backed up before proceeding.

1
Stop MongoDB.
Stop the mongod process by issuing the following command:

sudo service mongod stop
2
Remove Packages.
Remove any MongoDB packages that you had previously installed.

sudo apt-get purge mongodb-org*
3
Remove Data Directories.
Remove MongoDB databases and log files.

sudo rm -r /var/log/mongodb
sudo rm -r /var/lib/mongodb

