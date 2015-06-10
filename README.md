# Usefull linux commands

Here you will find collection of most and frequently used commands on linux. Those will be help full for them who are new with linux operating system.  I belive this snippet can save huge time for those who are in need of creating development environment in linux for web development.  

##Broadband and wifi setup
	sudo pppoeconf 

To enable wifi need to edit this file
	sudo gedit /etc/NetworkManager/system-connections/wifi-hostspot
	(type = ap)

## To update, upgrade and dist upgrade
	sudo apt-get update
	sudo apt-get upgrade
	sudo apt-get dist-upgrade

##To install unijoy support:
	sudo apt-get install ibus-m17n m17n-db m17n-contrib ibus-gtk
	ibus-daemon -xdr

##To isntall sass:
	sudo apt-get install ruby-full
	sudo apt-get install gem
	sudo gem install sass

##To install git
	sudo apt-get install git

##To install gulp
	sudo apt-get install npm
	sudo npm install --global gulp

##To install LAMP and phpmyadmin
	sudo apt-get install tasksel
	sudo tasksel
	sudo apt-get install phpmyadmin

##To enable rewrite mode on and Restart apache2
	a2enmod rewrite
	/etc/init.d/apache2 restart
	or
	service apache2 restart

Need to edit bellow file
	sudo gedit /etc/apache2/sites-available/000-default.conf

	DocumentRoot /var/www/html
	<Directory "/var/www/html">
		AllowOverride All
	</Directory>

##www and WordPress directory and files permision setup

	sudo chown -R www-data:www-data /var/www
	sudo find /var/www . -type d -exec chmod 755 {} +
	sudo find /var/www . -type f -exec chmod 644 {} +

##To install skype

To enable it, launch Software & Updates from the Unity Dash, go to Other Software tab. Check the first two boxes which say “Canonical Partners” and “Canonical Partners(Source Code)”.

	sudo apt-get update
	sudo apt-get install skype skype-bin

Skype indicator to work properly:

	sudo apt-get install sni-qt:i386

##To install google chrome
	sudo wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
	sudo dpkg -i google-chrome-stable_current_amd64.deb
	sudo apt-get -f install
	sudo rm google-chrome-stable_current_amd64.deb

##To install sublime text
	sudo add-apt-repository ppa:webupd8team/sublime-text-3
	sudo apt-get update
	sudo apt-get install sublime-text-installer

##To install filezilla
	sudo apt-get install filezilla

##To install dropbox
	cd ~ && wget -O - "https://www.dropbox.com/download?plat=lnx.x86_64" | tar xzf -
	~/.dropbox-dist/dropboxd

##Others
	sudo apt-get install synaptic vlc 
	sudo apt-get install gimp gimp-data gimp-plugin-registry gimp-data-extras 
	sudo apt-get install bleachbit flashplugin-installer 
	sudo apt-get install unrar zip unzip p7zip-full p7zip-rar rar mpack
	sudo apt-get install openjdk-7-jre oracle-java8-installer

##To clean up
	sudo apt-get -f install && sudo apt-get autoremove &&
	sudo apt-get -y autoclean && sudo apt-get -y clean

##Simple Screen Recorder
	pactl unload-module module-loopback
	pactl load-module module-loopback


##Linux obuntu installation in google chromebook

###To see detail list of availabe version of obuntu
	sh -e ~/Downloads/crouton -t list

###To see detail list of availabe released version of obuntu
	sh -e ~/Downloads/crouton -r list

###To start installation
	sudo sh -e ~/Downloads/crouton -t cinnamon -r raring


## Good Luck!