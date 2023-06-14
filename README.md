# Tunneling between two VPS using IPtable method

<h3><p align="center">Rules</p></h3>

This article is only an educational article and its use in an inappropriate way and violation of the rules is the responsibility of the user .
 
 
  
<h3><p align="left">Prerequisite</p></h3>
  
- !Before doing anything, you must have purchased two <b>VPS with different locations and both IPs should be <b>healthy and clean</b>.</br></br>
 

  
<h3><p align="left">Steps</p></h3></br>

- Getting root access on the server
   
   `sudo sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config && sudo systemctl restart ssh && sudo passwd`</br></br>
    
 
 - Installing iptables on the server`</br>

    $sudo apt install iptables</br></br>
 
 - Server port forwarding</br>

   Here, server 1 means the server on which we want to do port forwarding, and server 2 is the destination server: </br>
   `pip install -r requirements.txt`</br></br>
 
  
  
 - Now run the bot
  
    `python ReportBot.py`</br></br>
 

  <p align="center">The last update of the robot is on 08/18/2022 and from now on no update will be published for this robot and it may not work anymore.</p>
  <b>Made by Ali Atabak (ReXo)</b> 
