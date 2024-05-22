# MISP

## Download Host OS
- Ubuntu Desktop 24.04 LTS

## Recommended Install Method
- Docker Compose stack

## Container Architecture
- Docker
  * misp-core (nginx, PHP, cakePHP)
  * misp-modules (python)
  * db (mariadb)
  * redis (valkey)
  * mail (postfix)

## Configuring Ubuntu
- Update Ubuntu
  * sudo apt update
  * sudo apt full-upgrade
  * sudo apt autoremove
- Install Git
  * sudo apt install git
  * git version
- Install Docker
  * sudo snap install docker
  * sudo docker run hello-world

    
