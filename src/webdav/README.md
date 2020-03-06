## Configure docker-compose file :

Go to the webdav directory and edit the docker-compose.yml file :

    SERVER_NAMES: webdav.<mydomain.com>
    USERNAME: <random_username>
    PASSWORD: <random_strong_password>
    VIRTUAL_HOST: webdav.<mydomain.com>
    LETSENCRYPT_HOST: webdav.<mydomain.com>
    LETSENCRYPT_EMAIL: <email>

You will recognize the three last variable used by the nginx-proxy and letsencrypt companion containers launched.

*Still, make sure your webdav.mydomain.com> address is correctly configured on your DNS : it will redirect to your remote server IP !

Launch your WebDav server :

    docker-compose up --build -d

Check if your server is correclty avaible by going to webdav.mydomain.com adress on a web browser. You will be prompted for a user login and password. type them, and check if you can access to your files (certainly empty by the way, but if you don't have any errors, this is certainly all good !)

## Configure Nextcloud to connect to your webdav server :

Start by enabling the 'external storage support' app in the app management page. Then, in the settings page, go to the external storages management.

You can add as many folders as you want in here, for differents groups if you want to !

![webdav-configuration picture](resources/webdav-configuration.PNG)
