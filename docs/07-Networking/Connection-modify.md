Supose you want to make some changens in available network profile with the following parameter:
Configure your Host Name, IP Address, Gateway and DNS.

Host name : saminfo.local
hostname : abc.com
IP Address : 172.168.130.38
Subnet : 255.255.255.0
Gateway : 172.168.130.1
DNS : 172.168.130.1

## Follow this steps
##### Step 1: check all devices status first.
  `# nmcli dev status`
##### Step 2: select any connection profile that you want to modify. and make changes for IP addresses and Gateway(e.g "static" as a profile name for this practical)
  `# nmcli con mod static ipv4.addresses 172.168.130.38/24 ipv4.gateway 172.168.130.1 ipvr.method manual `
##### Step 3: Add DNS Configuration
  `# nmcli con mod static ipv4.dns 172.168.130.1`
##### Step 4: replicate all changes on the network.
  `# nmcli con up static`
##### Step 5: set hostname to saminfo.local
  `# hostnamectl`
  `# hostnamectl set-hostname saminfo.local`
  `# hostname`
  
  
##Done 
  
