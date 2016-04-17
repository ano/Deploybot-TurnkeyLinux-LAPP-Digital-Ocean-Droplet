# Deploybot-TurnkeyLinux-LAPP-Digital-Ocean-Droplet
Spinning Up a Turnkeylinux LAPP Stack on Digital Ocean using Deploybot
#Overview
In this tutorial we will look at setting up a docker host using Digital Oceans Docker Droplet. Once this host is setup we'll then pull down a Turnkeylinux LAPP docker container and spin that up. We'll then log into that container and do some stuff.

#Setup Droplet
Set up a Digital Ocean Droplet with Docker. Once the droplet has spun up, get your password from your email and then log in. 

#Spin Up TurnkeyLinux
Log in as root. 

Note that on your first log in you will have to retype your password and then set a new password of your own by tying it in and then typing it in again to confirm it. 

Now that your logged in run
```
docker pull turnkeylinux/lapp-14.1
```

Spin Up a Turnkeylinux LAPP instance
```
CID=$(docker run -i -t -d -p 80:80 -p 443:443 -p 12322:12322 -p 12321:12321 -p 12320:12320 -p 44:22 -p 5432:5432 turnkeylinux/lapp-14.1 )
CIP=$(docker inspect -format='{{.NetworkSettings.IPAddress}}' $CID)
```
