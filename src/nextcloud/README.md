
## More details about Nextcloud configuration

Here i will tell a bit more about some details i have ommited in the main README.md file about the nextcloud configuration on both server and application sides. 

For example, i will add informations about : 

* Clamav antivirus
* Volume management
* Networks (in the https-reverse-proxy directory)

# Clamav configuration (application side)

So we have added the clamav antivirus, but maybe you have some trouble to correcly configure it ! 
So, here is the configuration you want :) 

![clamav configuration picture](/resources/clamav-configuration.PNG)

# Volume management

As i explained on the main tutorial, i initially would like to manage my application with docker, and by that, i mean completely manage with docker ! 
This means that i didn't wanted to have data stored inside docker containers because i will be lost easily when upgrading the application.

So i've tried to place all sensible data in docker volumes. All those data in the nextcloud application correspond to the /var/www/html directory. This is why i created a volume named nextcloud (renamed nextcloud_app further down in the yml file).

I also wanted to externalize the /var/www/html/data directory that contains all of our uploaded documents (this is basically what we clearly don't want to lose...), so created a special volume for it too !

Note that the nextcloud volume is also used by the nginx server because it needed it to serve pages. 

There is another additional volume in the docker-compose file for the database, shared with the nextcloud application. This way, we can upgrade MariaDB and don't lose our data in the BDD.
This is very convenient i think ! :)

