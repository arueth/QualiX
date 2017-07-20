# QualiX
This repository contains the scripts and files to run dockerized QualiX with Docker Swarm. 
See [QualiX-Dockerfile](https://github.com/arueth/QualiX-Dockerfile) for the files used to build the [qualix](https://hub.docker.com/r/arueth/qualix/) image.

# Requirements
* Docker CE or EE 17.03.0 or greater, Docker version 1.12.0+ may work but have not been tested.
* A configured Docker Swarm

# How-To

### Deploy the QualiX stack
    bin/docker_stack_deploy.sh

### Remove the QualiX stack
    bin/docker_stack_rm.sh

### Verify QualiX is running
1. Browse to ```http://<DOCKER SWARM HOST>/remote/#/```
2. Browse to ```https://<DOCKER SWARM HOST>/remote/#/```
3. Verify the Connections screen is displayed

### Enable Remote Connections from CloudShell Portal
1. Open the ServerUniversalSettings.xml file on all Quali Server nodes

    ```C:\ProgramData\QualiSystems\Settings\Global\ServerUniversalSettings.xml```

2. In the  ```<ConfigurationSection name="LinkApplications">``` section remove all of the keys
3. Add the following keys for the connection types that you want to enable, replacing the placeholders:

  #### CloudShell 8.0.x+
    Placeholders:
    <CLOUDSHELL PORTAL HOST> = Hostname or IP address of the Quali CloudShell Portal
    <DOCKER SWARM HOST> = Hostname or IP address of the Docker Swarm

  ##### HTTP
    <key name="Telnet" pattern="http://<CLOUDSHELL PORTAL HOST>/Qx/connect?qualix=<DOCKER SWARM HOST>&amp;qualixType=http&amp;telnet{qid}&amp;qtoken={qtoken}&amp;hostname={Address}&amp;protocol=telnet&amp;port=23&amp;username={User}&amp;password=secure" icon-key="Telnet" />
    <key name="SSH"    pattern="http://<CLOUDSHELL PORTAL HOST>/Qx/connect?qualix=<DOCKER SWARM HOST>&amp;qualixType=http&amp;ssh{qid}&amp;qtoken={qtoken}&amp;hostname={Address}&amp;protocol=ssh&amp;port=22&amp;username={User}&amp;password=secure" icon-key="SSH" />
    <key name="RDP"    pattern="http://<CLOUDSHELL PORTAL HOST>/Qx/connect?qualix=<DOCKER SWARM HOST>&amp;qualixType=http&amp;rdp{qid}&amp;qtoken={qtoken}&amp;hostname={Address}&amp;protocol=rdp&amp;port=3389&amp;username={User}&amp;password=secure&amp;security=any&amp;ignore-cert=true" icon-key="RDP" />
    <key name="VNC"    pattern="http://<CLOUDSHELL PORTAL HOST>/Qx/connect?qualix=<DOCKER SWARM HOST>&amp;qualixType=http&amp;vnc{qid}&amp;qtoken={qtoken}&amp;hostname={Address}&amp;protocol=vnc&amp;port=5901&amp;username={User}&amp;password=secure" icon-key="VNC" />

  ##### HTTPS
    <key name="Telnet" pattern="https://<CLOUDSHELL PORTAL HOST>/Qx/connect?qualix=<DOCKER SWARM HOST>&amp;qualixType=https&amp;telnet{qid}&amp;qtoken={qtoken}&amp;hostname={Address}&amp;protocol=telnet&amp;port=23&amp;username={User}&amp;password=secure" icon-key="Telnet" />
    <key name="SSH"    pattern="https://<CLOUDSHELL PORTAL HOST>/Qx/connect?qualix=<DOCKER SWARM HOST>&amp;qualixType=https&amp;ssh{qid}&amp;qtoken={qtoken}&amp;hostname={Address}&amp;protocol=ssh&amp;port=22&amp;username={User}&amp;password=secure" icon-key="SSH" />
    <key name="RDP"    pattern="https://<CLOUDSHELL PORTAL HOST>/Qx/connect?qualix=<DOCKER SWARM HOST>&amp;qualixType=https&amp;rdp{qid}&amp;qtoken={qtoken}&amp;hostname={Address}&amp;protocol=rdp&amp;port=3389&amp;username={User}&amp;password=secure&amp;security=any&amp;ignore-cert=true" icon-key="RDP" />
    <key name="VNC"    pattern="https://<CLOUDSHELL PORTAL HOST>/Qx/connect?qualix=<DOCKER SWARM HOST>&amp;qualixType=https&amp;vnc{qid}&amp;qtoken={qtoken}&amp;hostname={Address}&amp;protocol=vnc&amp;port=5901&amp;username={User}&amp;password=secure" icon-key="VNC" />

  #### CloudShell 7.0.x - 7.1.x
    Placeholders:
    <DOCKER SWARM HOST> = Hostname or IP address of the Docker Swarm

  ##### HTTP
    <key name="Telnet" pattern="http://<DOCKER SWARM HOST>/remote/#/client/c/telnet{qid}?qtoken={qtoken}&amp;hostname={Address}&amp;protocol=telnet&amp;port=23&amp;username={User}&amp;password={Password}" icon-key="Telnet" />
    <key name="SSH"    pattern="http://<DOCKER SWARM HOST>/remote/#/client/c/ssh{qid}?qtoken={qtoken}&amp;hostname={Address}&amp;protocol=ssh&amp;port=22&amp;username={User}&amp;password={Password}" icon-key="SSH" />
    <key name="RDP"    pattern="http://<DOCKER SWARM HOST>/remote/#/client/c/rdp{qid}?qtoken={qtoken}&amp;hostname={Address}&amp;protocol=rdp&amp;port=3389&amp;username={User}&amp;password={Password}&amp;security=any&amp;ignorecert=true" icon-key="RDP" />
    <key name="VNC"    pattern="http://<DOCKER SWARM HOST>/remote/#/client/c/vnc{qid}?qtoken={qtoken}&amp;hostname={Address}&amp;protocol=vnc&amp;port=5901&amp;username={User}&amp;password={Password}" icon-key="VNC" /> 

  ##### HTTPS 
    <key name="Telnet" pattern="https://<DOCKER SWARM HOST>/remote/#/client/c/telnet{qid}?qtoken={qtoken}&amp;hostname={Address}&amp;protocol=telnet&amp;port=23&amp;username={User}&amp;password={Password}" icon-key="Telnet" />
    <key name="SSH"    pattern="https://<DOCKER SWARM HOST>/remote/#/client/c/ssh{qid}?qtoken={qtoken}&amp;hostname={Address}&amp;protocol=ssh&amp;port=22&amp;username={User}&amp;password={Password}" icon-key="SSH" />
    <key name="RDP"    pattern="https://<DOCKER SWARM HOST>/remote/#/client/c/rdp{qid}?qtoken={qtoken}&amp;hostname={Address}&amp;protocol=rdp&amp;port=3389&amp;username={User}&amp;password={Password}&amp;security=any&amp;ignorecert=true" icon-key="RDP" />
    <key name="VNC"    pattern="https://<DOCKER SWARM HOST>/remote/#/client/c/vnc{qid}?qtoken={qtoken}&amp;hostname={Address}&amp;protocol=vnc&amp;port=5901&amp;username={User}&amp;password={Password}" icon-key="VNC" />

