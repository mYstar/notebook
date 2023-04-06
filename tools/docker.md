- `docker pull <repo>:latest`: downloads the latest image of a repo from docker hub
- `docker images`: lists all pulled images
- `docker stop <container>`: stops a specific running container (use: `docker-compose` to automate this)
- `docker ps -a` or `docker container list`: infos about (running) containers
- `docker rm <container>`: removes a container from docker hub
  - `--volumes`: remove volumes
  - `--link`: remove links
- `docker rmi <image>`: delete docker images from the system
- `docker exec <container> <command>`: executes a command in a container
    - `-d` detached mode
    - `-it` interactive terminal

# docker-compose
- `docker-compose up/down`: start/stop an image according to the *docker-compose.yml*
    - option `-d`: detached mode

# docker-compose.yml
- settings for deployment of the image
- `volumes:`: `<local file>:<container-file>` maps a local file/dir to another place in the container