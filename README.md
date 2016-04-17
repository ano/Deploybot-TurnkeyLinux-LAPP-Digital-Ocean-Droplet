#Pre-requisites
- Digital Ocean Account
- Deploybot Account
- Google Chrome Browser
- Docker UI Chrome App
# Deploybot-TurnkeyLinux-LAPP-Digital-Ocean-Droplet
Spinning Up a Turnkeylinux LAPP Stack on Digital Ocean using Deploybot
#Overview
In this tutorial we will look at setting up a docker host using Digital Oceans Docker Droplet. Once this host is setup we'll then pull down a Turnkeylinux LAPP docker container and spin that up. We'll then log into that container and do some stuff.

#Digital Ocean: Setup Docker Droplet 
Set up a Digital Ocean Droplet with Docker. Once the droplet has spun up, get your password from your email and then log into deploybot. 

#Deploybot: Connect Deploybot to Github and Digital Ocean Accounts 
Step 1: Connect to your Digital Ocean Account
Step 2: Connect to a repository, on your first go you will need to connect up your Github Account. Set the Application path to /var/www/
Step 3: Create a Deployment by putting the following commands in deploybots settings

> Run commands after new version becomes active

```bash
echo "DOCKER_OPTS='-H tcp://0.0.0.0:2375 -H unix:///var/run/docker.sock'" >> /etc/default/docker  
sudo service docker restart

docker pull turnkeylinux/lapp-14.1
docker pull turnkeylinux/lamp-14.1
```
Step 4: Install Docker UI Chrome App https://github.com/felixgborrego/docker-ui-chrome-app
Step 5: Map the host and docker image files to /var/www/
Step 6: Spin up a container from the app
