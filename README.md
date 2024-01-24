Welcome to my ARR Stack!

I have created this simple ARR Stack for most if not all, be forewarned its based on linux so windows and mac will need to adapt 
it to your own use case. It contains Bazarr, Lidarr, Radarr, Sonarr, Readarr, Prowlarr, Overseer, Flaresolverr, Transmission, Unpackerr, Watchtower and a reverse proxy: Caddy. The transmission container has both transmission and OpenVPN in the container. I use linuxserver.io images with the eception of Overseerr, Flareresolverr, Unpackerr, Watchtower and Caddy. 

There are two files you will download docker-compose.yaml and a .env file.

This will install these apps in docker. But before you run docker compose up -d you must modify the compose file to fit your needs. I have noted what you need to change as best I can. where it says "<path/for/media>,<path/for/downloads> and <path/for/config>" enter the directories/folders for each service.

If you are already using the ports for other apps change ONLY the left side of XXXX:XXXX.

There is a .env file that needs modifying to your use case. this file goes in the the docker folder where your compose file resides. For example I put my compose files in /home/georgew/docker, so tree looks like this:
    /home/georgew/docker/dockercompose.yaml
    /home/georgew/docker/.env

I have listed the apps and their websites as well as docker hub pages w/ some exceptions:

Bazarr: https://www.bazarr.media/  Subtitle Management  https://hub.docker.com/r/linuxserver/bazarr <br>
Lidarr: https://lidarr.audio/  Music Management  https://hub.docker.com/r/linuxserver/lidarr <br>
Radarr: https://radarr.video/  Movie Management  https://hub.docker.com/r/linuxserver/radarr
Sonarr: https://sonarr.tv/  TV Series Management  https://hub.docker.com/r/linuxserver/sonarr
Readarr: https://readarr.com/  EBook Management  https://hub.docker.com/r/linuxserver/readarr
Prowlarr: https://prowlarr.com/  Indexer Management (torrents and usenet)  https://hub.docker.com/r/linuxserver/prowlarr
Overseerr: https://overseerr.dev/  Media Requester for Plex  https://hub.docker.com/r/sctx/overseerr
Transmission: https://transmissionbt.com/  Bittorrent Client w/OpenVPN  https://github.com/haugene/docker-transmission-openvpn
Caddy: https://caddyserver.com/  Caddy Reverse Proxy using labels  https://github.com/lucaslorentz/caddy-docker-proxy
Flaresolverr: https://github.com/flaresolverr/FlareSolverr/pkgs/container/flaresolverr  FlareSolverr is a proxy server to bypass Cloudflare and DDoS-GUARD protection.
Watchtower: https://github.com/containrrr/watchtower  Docker Container/image updater
Unpackerr: https://github.com/Unpackerr/unpackerr RAR and ZIP file unpacker

You must have Docker and Docker Compose installed. For info check docker.com
    https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-compose-on-ubuntu-20-04

You must have your own domain name
     get one from Cloudflare: https://www.cloudflare.com or Namecheap: https://www.namecheap.com/
     
Have DNS entries in your DNS provider. I use cloudflare.com. You want an "A" record for each service EXCEPT: flaresolverr, unpackerr, caddy and watchtower these do NOT need DNS records (you wont be accessing them at all. they work in the background) A "CNAME" for your domain

You must have ports 80 & 443 open on server and router

You must create docker network caddy:
    command line: docker network create caddy

Once your compse file and .env file are ready, on command line enter: "docker compose up -d" and it will start pulling the images and presto your on to the next step. Please consult the Trash Guides for help in settings for your apps https://trash-guides.info/ and Servarr Wiki: https://wiki.servarr.com/.
I unfortunately do not have the time to walk everyone through setting up each application. Remember folks Google is your friend :)
