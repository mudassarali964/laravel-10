## Make sure Docker Desktop is running on your machine

## Configure a shell alias
- To make sure this is always available, you may add this to your shell configuration file in your home directory, such as ~/.zshrc or ~/.bashrc, and then restart your shell.

Steps: 
if you are using bash run in your terminal

=> nano ~/.bash_profile

and then add alias - alias sail='[ -f sail ] && bash sail || bash vendor/bin/sail',

=> source ~/.bash_profile

## .env Database setting

DB_CONNECTION=mysql
DB_HOST=mysql
DB_PORT=3306
DB_DATABASE=laravel_cashier
DB_USERNAME=root
DB_PASSWORD=

## Run the project in the docker via sail

sail build --no-cache
sail up -d
sail artisan migrate:fresh --seed

====================================================
## Only for update the database credentials from env 
====================================================

=> If we need to change the database credentials from .env file, then we should follow the given steps:

1- Run the given commands:
	sail stop
	sail down => Will untagged (not remove), all the images and volume related to the container
	sail down -v => Will remove all the containers volume

2- Manually removed all the images related to the container
3- Then change the database credentials in the .env file
3- Finally Run these commands:
	- sail build --no-cache
	- sail up -d

====================================================


