# Installation

This app requires a 64 bit linux environment to run. If you're on OS X or Windows, I've included a vagrant file to easily spool up a 64bit Ubuntu vm.

## Create a VM (Only if not on a 64bit Debian/Ubuntu machine)
[Install Vagrant](http://docs.vagrantup.com/v2/installation/index.html)

[Install Virtualbox](https://www.virtualbox.org/wiki/Downloads) (you can also use VMWare)

Create and start the VM
```
cd </my/project/location>
vagrant up
```

Login to the VM
```
vagrant ssh
```
It's worth noting that your code is shared from your host (OS X, Windows, etc) and placed in the `/vagrant` directory of the VM.


## Install app dependencies
```
cd /vagrant
npm install
```

# Usage

## Launch the server

Start the server with the devellopement environment spec. "debug  - not minified file - ...""
```
sails lift
```

Start the server with the production environment spec.  "No debug - minified file  -  ..."
```
sails lift --prod
```


You can configure by environment some server infos like:
1. Port used
2. log level
3. models connection

Create a database, like "pcars" and be sure your mysql user have all grant access to it, when you will lift the app all table will be created.

Edit the file in: /config/connection.js with your database-infos into 'Mysql' object or if you want to use an other adaptater like mongoDB, don't forget to change the adaptater used into /config/models.js and /config/env/production.js


> !!! IMPORTANT SECURITY  REPLACEMENT !!!

Edit the file in /config/session.js, and change the secret security key

- Clan/team website infos

Edit the file in /config/personnalConfig.js and change sitename/siteurl to your infos, and pagination limit if you want.

## Usage

### Launch the server

> !!! CLOSE THE PROJECT CARS DEDICATED SERVER FIRST, BEFORE LIFT !!!

The better way to run the app, is like pcars dedicated server, with screen on linux:

	screen
	cd /Path/to/the/Project
	sails lift --prod

 - Press ctrl­+a  to detach from the screen.
 - Press ctrl+­d to leave the screen

command line:

lift the server with the production environment spec.  " No debug - minified file  -  ...".
```
    sails lift --prod
```

lift the server with the development environment spec. "debug  - not minified file - ..."
```
    sails lift
```

You can configure by environment some server infos like:
 1. Port used
 2. log level
 3. models connection

### First lift and admin account

> If the 80 port is already used by "apache-..." try to lift the server
> with another port

- First go to: http://yourdomain.com:port_specified_in_environment/signup

- Create an account and close the server with ctrl+c

- Go to /config/route.js and comment lines:
	`//'get /signup': { view: 'user/signup' },
    //'post /signup': 'UserController.signup',
	`
For this first release, all account have acces to admin panel http://yourdomain.com:port_specified_in_environment/login.
*On near future, admin access will be granted with role rules.*

- Lift the server again, and click to the arrow down on the top menu and click on admin.
- Go to server and start the listener all Tracks, Groups, and Cars will be updated
- Run the Project Cars dedicated server!

## What'is Events?

> NEED TO BE FIX

The events were created, so that when the session that matches the specifications of it , all will be recorded associated with the event. This will ensure fair competition conditions when hotlap for example.

- Go to admin panel, create one, and when you create a session in game be sure you are using the same conditions. the listener match if is identical:
-  servername,
- weather conditions *slot1, slot2, slot3, slot4*,
- date Ingame,
- between start and end date,
- DamageType,
- TireWearType,
- FuelUsageType,
- Track,
- Car group,
- DateProgression,
- ForecastProgression

## I don't love design can i modify it?

You will find in the Assets folder all Js/Css/Fonts/Less/Images used and all pages files are into /views. Your are allow to do all you want.


PS: The app is still in beta, if you found a bug, report them here or in [Project-cars forum thread](http://forum.projectcarsgame.com/showthread.php?33757-Project-Cars-Dedicated-Server-Live-App)
