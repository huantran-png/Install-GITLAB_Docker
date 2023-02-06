# Install_GitLab_Server_By_ Docker
## 1/ Requiments
- OS: Debian 11.x
- Resources: Ram 4GB, CPU 4 cores
- Tools: Docker, GitLab image, SSH, 

## 2/ Install Docker using repository
*Step1: Update the apt package index and install packages to allow apt to use a repository over HTTPS:*
>`sudo apt-get update`
>`sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release`

*Step2:Add Docker’s official GPG key*
>`sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg`

*Step3:Use the following command to set up the repository*
>echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

## 2/ Intall GitLab Docker Image
*Step1: Set path to /srv/gitlab*

>`export GITLAB_HOME=/srv/gitlab`

*Step2: Install using Docker Engine*

>`sudo docker run --detach \`

>` --hostname localhost \`

>`  --publish 443:443 --publish 80:80 --publish 22:22 \`

>`  --name gitlab \`

>`  --restart always \`

>`  --volume $GITLAB_HOME/config:/etc/gitlab \`

>`  --volume $GITLAB_HOME/logs:/var/log/gitlab \`

>`  --volume $GITLAB_HOME/data:/var/opt/gitlab \`

>`  --shm-size 256m \`

>`  gitlab/gitlab-ce:latest`

*Step3:Login*
*URL: http://localhost.com OR http://Ip_address.com*

>Account: root

Password default of root 

> `sudo docker exec -it gitlab grep 'Password:' /etc/gitlab/initial_root_password`