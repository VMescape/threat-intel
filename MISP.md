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
- Enable Feeds
  * Sync Actions > Feeds > Load Default Feed Metadata
  * Click notepad and pen icon "CIRCL OSINT Feed"
  * Check Enabled
  * Click Modify, under additional sync parameters add: {"last": "30d"}
  * Update and submit
- Remote Servers
  * Sync Actions > Remote Servers
  * New Servers
  * Set the following:
     - Base URL: https://misp.ctidiags.com/
     - Instance name: CTIDiags MISP
     - Organisation Type: External organisation
     - External Organisation: CTIDiags
     - Authkey: A 40 character long string
  * Check the following:
     - Push, Pull, Unpublish Event
  * Click "Modify" black button under "Push rules"
  * Click on "Select some tags" gray text in middle top bar
  * Type "false" and click"workflow:todo=review-for-false-positive" tag
  * Click the ▶ button to move it into the right hand "Blocked tags" box
  * Update and submit
- Scheduled Tasks (deprecated) 
  * Administrator > Scheduled Tasks
  * Update "fetch_feeds" frequency hour to "24"
  * Update "catch_feeds" frequency hour to "24"
  * Click Update all button
- Enable Workflows
  * Administration > Server Settings & Maintenance
  * Plugin > Action
  * Change "Plugin.Action_services_enable" to true, and click the ✔
  * Ensure "Plugin.Action_services_url" set to "http://misp-modules", and click the ✔
  * Click on "Workflow" blue text
  * Change "Plugin.Workflow_enable" to true, and click the ✔
-
