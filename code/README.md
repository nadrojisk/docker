# VSCode in a Browser

## Setup
Sample docker-compose to start your own code-server! 
Change, your PUID, GUID to your user, change the volume and run a ```docker-compose up -d``` in the same directory as your docker-compose.yml and go to $ip:5443! That's it!

```
---
version: "3"
services:
  code-server:
    image: vincentchu37/code-server:latest
    container_name: code-server
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=America/Chicago
    volumes:
      - /home/vincent/code:/home/coder/
    ports:
      - 5443:8080
    restart: unless-stopped
```

FAQ: 
1. What is the PUID and GUID? That's the user id and group id of the user that your want to mount your volume in. In the example docker-compose user 'vincent' would have the user id of 1000 and group id 1000. So if you want to pass a directory owned by bob, do a ```id``` and change the PUID and PGID to his id.
2. Where do I find a list of timezones? Here you go, https://en.wikipedia.org/wiki/List_of_tz_database_time_zones (column TZ database name)
3. What is the volume? That is where all the data for code and configs for the code-server is stored. In the example, the 'home' for the code-server is /home/vincent/code in the physical machine.
4. Why do you need PHP and unzip? Why don't you?
5. How often do you keep code-server updated with upstream? I have email notifications on for releases so I tend to get around to it within a week. 

Updating your code server instance
1. Pull latest via your docker compose ```docker-compose pull```
2. Update container with the latest image```docker-compose up -d```
3. That's it!

## Languages
* Python3
* Rust
* PHP
