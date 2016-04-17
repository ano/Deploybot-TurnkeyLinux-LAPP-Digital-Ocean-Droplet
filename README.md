# Deploybot-TurnkeyLinux-LAPP-Digital-Ocean-Droplet
Put this code in your deploybot instance
#The short version
Put the following commands in deploybots settings

> Run commands after new version is uploaded

```bash
docker kill $(docker ps -q)
docker rm $(docker ps -a -q)
```

> Run commands after new version becomes active

```bash
docker pull turnkeylinux/lapp-14.1
CID=$(docker run -i -t -d -p 80:80 -p 443:443 -p 12322:12322 -p 12321:12321 -p 12320:12320 -p 2222:22 -p 5432:5432 turnkeylinux/lapp-14.1)
CIP=$(docker inspect -format='{{.NetworkSettings.IPAddress}}' $CID)
docker logs $CID | grep "Random initial root password"
docker exec -t -i $CID /bin/bash
echo "root:4qasshole"|chpasswd
```

#The long version
Spinning Up a Turnkeylinux LAPP Stack on Digital Ocean using Deploybot
#Overview
In this tutorial we will look at setting up a docker host using Digital Oceans Docker Droplet. Once this host is setup we'll then pull down a Turnkeylinux LAPP docker container and spin that up. We'll then log into that container and do some stuff.


#Digital Ocean 
Step 1: Setup Docker Droplet
Set up a Digital Ocean Droplet with Docker. Once the droplet has spun up, get your password from your email and then log in. 

#Deploybot 
Step 1: Connect to your Digital Ocean Account
Step 2: Connect to a repository, on your first go you will need to connect up your Github Account
Step 3: Create a Deployment
```
docker pull turnkeylinux/lapp-14.1
```

Spin Up a Turnkeylinux LAPP instance
```
CID=$(docker run -i -t -d -p 80:80 -p 443:443 -p 12322:12322 -p 12321:12321 -p 12320:12320 -p 2222:22 -p 5432:5432 turnkeylinux/lapp-14.1)
CIP=$(docker inspect -format='{{.NetworkSettings.IPAddress}}' $CID)
docker logs $CID | grep "Random initial root password"
docker exec -t -i $CID /bin/bash
echo "root:4qasshole"|chpasswd
```
