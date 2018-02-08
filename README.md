# DOCKER DISCOVERY

---

# 1: Install

 ````
  curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

  sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

  sudo apt update

  apt-cache policy docker-ce

  sudo apt install -y docker-ce

  sudo systemctl status docker

  sudo usermod -aG docker ${USER}


  # Clean Docker

  docker system prune -a
  ````
  
  
# 2: Setup a dev environment on docker (example)

 ## Run an Ubuntu-LAMP container
  ````
  docker run -d --name [name] -p 81:80 -v /home/${USER}/docker-mirror:/var/www/html nickistre/ubuntu-lamp
  ````

 ## Execute the console
  ````
  docker exec -it [container] bash
  ````

 ## Updates
  ````
  apt-get update

  apt-get upgrade

  apt-get autoremove
 ````

 ## Setup Adminer
  ````
  mkdir /usr/share/adminer

  wget "http://www.adminer.org/latest.php" -O /usr/share/adminer/latest.php

  ln -s /usr/share/adminer/latest.php /usr/share/adminer/adminer.php

  echo "Alias /adminer.php /usr/share/adminer/adminer.php" | tee /etc/apache2/conf-available/adminer.conf

  a2enconf adminer.conf

  service apache2 restart


  # Update Adminer

  wget "http://www.adminer.org/latest.php" -O /usr/share/adminer/latest.php


  # Uninstall

  a2disconf adminer.conf

  service apache2 restart

  rm /etc/apache2/conf-available/adminer.conf

  rm -Rf /usr/share/adminer
  ````
  
 ## Install Composer
 ````
 curl -sS https://getcomposer.org/installer | php
 
 sudo mv composer.phar /usr/local/bin/composer.phar
 
 vim ~/.bashrc
 alias composer='/usr/local/bin/composer.phar'
 
 source ~/.bashrc
 ````

 ## Change MySQL password
  ````
  SET PASSWORD FOR '[user]'@'localhost' = PASSWORD('[password]');

  FLUSH PRIVILEGES;
  ````

 ## Setup Git
  ````
  apt-get install git
  ````

 ## Add Vim & Nano
  ````
  apt-get install vim

  apt get install nano
  ````
