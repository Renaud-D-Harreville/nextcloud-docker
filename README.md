# nextcloud-docker
Nextcloud installation with docker and docker compose

This repository is intended to share one possibility to host a complete and secure nextcloud server.

At first i wanted to get a secure and stable nextcloud self-hosted server, and i forced myself with those constraints :

* Stability and easily management that can offer docker containers
* Security of both data and server, mainly served with https protocol.
* Extendable domain sites : because i didn't want to get my domain to be exclusive for nextcloud, i would like to add other web sites using my domain.
* OnlyOffice integration. We will see that with first three points, this constraint is easy to get ! (And that was exactly what i wanted to with thos 3 first points : easy management, but not to ommit security, and easy extendability !)

How do this work ? How do we get all those constraints ? 

First, we want the use of docker because it is more stable when multiple application are on the same server, and it can very easily manage with docker compose. So we start by searching the rights docker images and if possible some examples of their possible docker compose configuration.

At first we get a nextcloud + mariadb + nginx configuration, that will enable us to get an unsecure but working docker compose nextcloud server. that can be access through the server IP adress. This is approximatively what we can found on the src/nextcloud directory (you will see an additional clamav image in it, that i will explain later).

For the security, we want https protocol, and this can be achieved with the letsencrypt docker image. But to make it work we must get a valid domain (you will probably have to buy one), and a correct DNS configuration to point your domain adress to your server IP. More information on the Letsencrypt site web.

Now that we have https enable, our server is secure. But we want it to be extandable, and by that i mean i want the possibility to add another web site on my server (not just the nextcloud one). So, we have one IP adress, accessible through just one port (443 because we want https for all our web sites !). This is here we will cut in two part our application : one part for web back end (nextcloud application for example), and another part to proxy https requests. This result to the two directories src/https-reverse-proxy and src/nextcloud. 

Sorry, I didn't understant how this works ? ...
No worries, i will try to explain the two configuration later ! :)



