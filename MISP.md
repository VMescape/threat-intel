# MISP Lab Setup

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

## Configuring Docker
- Cloning misp-docker
  * cd ~
  * git clone https://github.com/MISP/misp-docker
  * cd misp-docker
  * ls
- Configuring misp-docker
  * hostname -I
  * cp template.env .env
  * echo "BASE_URL=https://ip.address.goes.here" >>.env
- Running misp-docker
  * sudo docker compose up -d
   
## Accessing MISP
- Navigate to "https://ip.address.goes.here/" in browser
  * Default username: admin@admin.test
  * Default password: admin

## Configuring MISP
- Checking diagnostics
  * Administrator > Server Settings & Maintenance > Dianogistics
  * Examine the state of the MISP instance
- Adding Organisation
  * Administrator > List Organisations
  * Click notepad and pen icon
  * Change Organisation Identifier to org name and submit
- Create Users
  * Administrator > Add User
  * Configure as required
- Enable Taxonomies
  * Event Actions > List Taxonomies
  * Enable "tlp", "tlp", "admiralty-scale" and "workflow"
  * View enabled taxonomies, and select "enabled all" under the Active Tags column
- Enable Warninglists
  * Input Filters > Warninglists
  * Enable desired warninglists ("RFC 5735" recommended)
