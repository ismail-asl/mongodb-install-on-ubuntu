# mongodb-install-on-ubuntu

MongoDB installtion on linux ubuntu https://docs.mongodb.com/manual/tutorial/install-mongodb-on-ubuntu/
	
# Install the MongoDB packages

  ```
  Import the public key used by the package management system.
    wget -qO - https://www.mongodb.org/static/pgp/server-5.0.asc | sudo apt-key add -

  Create a list file for MongoDB
    echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/5.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-5.0.list
	
	Start MongoDB
		sudo systemctl start mongod
  
  Start MongoDB
		sudo systemctl start mongod
  
  Update apt
    sudo apt-get update
  
  Reload local package database
    sudo apt-get install -y mongodb-org
  
	Verify that MongoDB has started successfully.
		sudo systemctl status mongod
	
	You can optionally ensure that MongoDB will start following a system reboot by issuing the following command:
		sudo systemctl enable mongod
	
	Stop MongoDB
		sudo systemctl stop mongod
	
	Restart MongoDB.
		sudo systemctl restart mongod
		
	Begin using MongoDB
		mongosh 
```    

  # Installation Issues:
    * Signature missing:
      Sometimes we get this error when we type "sudo apt-get update". This is because of missing key. For retreiving that,
      we need to type: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys [missing_key]
      
    * unrecoverable fatal error [Unknown System user mongodb in statoverride file.].
      Run all the following commands:
        > sudo rm /var/lib/dpkg/statoverride
        > sudo rm /var/lib/dpkg/lock
        > sudo dpkg --configure -a
        > sudo apt-get -f install
         
# Uninstall MongoDB Community Edition
	Stop MongoDB
		sudo service mongod stop
	
	Remove Packages
		sudo apt-get purge mongodb-org*
	
	Remove Data Directories
		sudo rm -r /var/log/mongodb
		sudo rm -r /var/lib/mongodb
