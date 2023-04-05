# Network-Info-Dump-bash-script-in-Linux





#COPY AND PASTE OF THE SCRIPT FROM THE NOTEPAD FILE

#!/bin/bash

#Name of Output File

network_output="network_info_$(date).txt"

#Header Info

echo "NETWORK INFORMATION" > "$network_output"
echo "***********************" >> "$network_output"
echo "     " >> "$network_output"

#IP Info

echo "Ip Addresses & Associated Interfaces:" >> "$network_output"
echo "---------------------------------------------" >> "$network_output"
ip addr show >> "$network_output"
echo "" >> "$network_output"

#DNS Info

echo "DNS Server:" >> "$network_output" 
echo "------------" >> "$network_output"
grep "nameserver" /etc/resolv.conf >> "$network_output"
echo "      " >> "$network_output"

#Open Ports

echo "Ports Open:" >> "$network_output"
echo "-------------------" >> "$network_output"
sudo netstat -tuln >> "$network_output"
echo "      " >>  "$network_output"

#Firewall Rules
echo "FireWall Rules:" >> "$network_output"
echo "------------------" >> "$network_output"
sudo iptables -S >> "network_output"
echo "     " >> "$network output"

#Sending over contents 
cat "$network_output"
