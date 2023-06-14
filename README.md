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

   Here, server 1 means the server on which we want to do port forwarding, and server 2 is the destination server: </br></br>

   `sysctl net.ipv4.ip_forward=1`</br></br>
   `iptables -t nat -A PREROUTING -p tcp --dport 22 -j DNAT --to-destination IP SERVER 1`</br></br>
   `iptables -t nat -A PREROUTING -j DNAT --to-destination IP SERVER 2`</br></br>
   `iptables -t nat -A POSTROUTING -j MASQUERADE`</br></br>
    
 
  
  
 - Use the following commands to prevent ip forwarding from being interrupted after server reboot</br></br>
     First, we create a local with the following command and put the commands in it and save it: </br></br>

    `sudo nano /etc/rc.local`</br></br></br>

     `#! /bin/bash`</br></br>
     `sysctl net.ipv4.ip_forward=1`</br></br>
     `iptables -t nat -A PREROUTING -p tcp --dport 22 -j DNAT --to-destination IP SERVER 1`</br></br>
     `iptables -t nat -A PREROUTING -j DNAT --to-destination IP SERVER 2`</br></br>
     `iptables -t nat -A POSTROUTING -j MASQUERADE`</br></br>
     `exit 0`</br></br></br>

      Now we need to give local full access, which will run automatically every time our local server is restarted</br>

      `sudo chmod +x /etc/rc.local`</br></br></br>

    
 

  <p align="center">Congratulations, you have successfully created a tunnel through IP forwarding.</p>
  <b><p align="center"></p>Written by Ali Atabak (ReXo)</p></b> 
