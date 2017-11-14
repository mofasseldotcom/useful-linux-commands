# Usefull linux commands

Here you will find collection of most and frequently used commands on linux. Those will be help full for them who are new with linux operating system.  I belive this snippet can save huge time for those who are in need of creating development environment in linux for web development.  

##Broadband and wifi setup

	sudo pppoeconf 

###To enable wifi sharing:
	Create a WiFi connection first
	* Connection name will be "wifi-hotspot" (or anything)
	* Set one SSID, in my case it is "webitbuzz"
	* WiFi Security >> Choose "WPA & WPA2 Personal" from Security dropdown
	* Set a Password, in my case "0123456789"
	* IPV4 Settings >> Shared to other computers and Save	

	Now you will see a file named wifi-hotspot in path bellow:

	sudo gedit /etc/NetworkManager/system-connections/wifi-hotspot

	Just change type=infrastructure to "mode = ap" and save
	Now you are ready to go.

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
	sudo apt-get install php-mbstring php7.0-mbstring php-gettext

##To enable rewrite mode on and Restart apache2

	sudo a2enmod rewrite
	sudo /etc/init.d/apache2 restart
	or
	sudo service apache2 restart

###Need to edit bellow file

	sudo gedit /etc/apache2/sites-available/000-default.conf

	DocumentRoot /var/www/html
	<Directory "/var/www/html">
		AllowOverride All
	</Directory>

###To set private domain name instead of localhost

	sudo gedit /etc/hosts
	127.0.0.1 	localhost
	127.0.0.1 	newname.tld // Copy above line and edit it as you want

##www and WordPress directory and files permision setup

	sudo chown www-data:www-data /var/www -R // to change user and group ownership
	sudo chmod 755 /var/www -R // To change user permission where r=7 w=7 e=5
	sudo find /var/www . -type d -exec chmod 755 {} + // Directory specific permission change
	sudo find /var/www . -type f -exec chmod 644 {} + // File specific permission change
	sudo adduser username www-data // adds your username to www-data group
	sudo usermod -a -G www-data username // adds your username to www-data group

## Changing Server Document Root from /var/www to /home/username/Sites/public_html

Step 1: Edit and replace bellow file

	sudo gedit /etc/apache2/apache2.conf

	<Directory /home/user/Sites/public_html/>
		Options Indexes FollowSymLinks
		AllowOverride None
		Require all granted
	</Directory> 

Step 2: Edit and replace bellow file

	sudo gedit /etc/apache2/sites-available/000-default.conf

	DocumentRoot /home/user/Sites/public_html
	<Directory "/home/user/Sites/public_html">
		AllowOverride All
	</Directory>

Step 3: Restart apache2

	sudo service apache2 restart

Extra step 4: To upload plugins or add media without facing issues edit and replace bellow file

	sudo gedit /etc/apache2/envvars

	export APACHE_RUN_USER=username
	export APACHE_RUN_GROUP=username

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

##To Solve microphone input issue

	sudo gedit /etc/modprobe.d/alsa-base.conf
	"options snd-hda-intel model=auto" // Put it bottom of the alsa-base.conf file
	hdajackretask // select show unconnected pins and choose microphone from pin 18
	alsamixer //adjust pcm and capture


##To loopback microphone sound to speaker

	pactl unload-module module-loopback
	pactl load-module module-loopback


### Way to generate SSH Key to make passwordless secure SSH Connection with cpanel

	ssh-keygen -t rsa -b 4096 -C "your_email@example.com"

	* Above command will ask you to set your passpress

	* You will see id_rsa & id_rsa.pub key is generated

	* Upload id_rsa.pub key into cpanel .ssh folder using command bellow
	
	scp /home/localuser/.ssh/id_rsa.pub cpaneluser@domain.tld:/home/cpaneluser/.ssh/authorized_keys

	* It will ask for cpanel password
	* Above command will upload and authorize your id_rsa.pub key in order to work properly

	* Now you can connect your cpanel server using command bellow

	ssh cpaneluser@domain.tld // it will ask for passpress for onetime in each computer login session


##Linux obuntu installation in google chromebook

###To see detail list of availabe version of obuntu

	sh -e ~/Downloads/crouton -t list

###To see detail list of availabe released version of obuntu

	sh -e ~/Downloads/crouton -r list

###To start installation

	sudo sh -e ~/Downloads/crouton -t cinnamon -r raring


## Good Luck!