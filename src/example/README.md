# Simple example on how to add additionnal web site

This is a simple and basic docker-compose.yml file to explain how you can add an additional web site usin our architecture configuration.

There are 3 major parts that are necessary in your docker-compose.yml file you will need to connect your web site to the nginx-proxy.

## Environnement part


    environment:
      - VIRTUAL_HOST=nginx.<mydomain.com>
      - LETSENCRYPT_HOST=nginx.<mydomain.com>
      - LETSENCRYPT_EMAIL=<email>
    
As always, do not forget to add the 'nginx.mydomain.com' on your DNS configuration ! 
Note that you can obviously change the 'nginx' with the name you want to for your web site. For example it can be 'mybeautifulwebsite.mydomain.com'. This will change nothing (but just configure your DNS with that domai :p )
    
## Docker Network part 

Because we have to communicate with the reverse proxy launched previously (on the main README.md part), we have to connect our docker container to the same reverse-proxy container through a docker network.
So just add this at the end of your docker service part (as seen on the example !) :

    networks:
      - reverse-proxy

## Network definition

And to finish, we must explain that our network is an external one, and explicitly name it. This is done within the network part of the docker-compose file specification : 

