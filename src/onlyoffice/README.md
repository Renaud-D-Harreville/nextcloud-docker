# Configure and launch onlyoffice document server

configure these environment variable in the src/onlyoffice/docker-compose.yml file :

      - JWT_SECRET=<strong_secret_key>
      - VIRTUAL_HOST=onlyoffice.<mydomain.com>
      - LETSENCRYPT_HOST=onlyoffice.<mydomain.com>
      - LETSENCRYPT_EMAIL=<email>
 
> As always make sure you have correctly configured your DNS server to point your onlyoffice.mydomain.com adress to you server IP.

Now, launch the onlyoffice document server with : 

    docker-compose up --build -d
    
# Configure onlyoffice (application side)

Start by enabling the ONLYOFFICE app, and go to setting -> ONLYOFFICE.
type your domain adress and the secret key you put on the *src/onlyoffice/docker-compose.yml* file (JWT_SECRET variable).

Save it, this is OK !
