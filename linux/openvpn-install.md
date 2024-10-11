---
description: >-
  credit:
  https://zacs-tech.com/how-to-install-openvpn-access-server-on-ubuntu-22-04
---

# OpenVpn Install

Run the following commands:

```bash
sudo apt update && sudo apt upgrade -y
echo "deb [signed-by=/etc/apt/keyrings/openvpn-as.gpg.key] http://as-repository.openvpn.net/as/debian $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/openvpn-as.list
wget --quiet -O - https://as-repository.openvpn.net/as-repo-public.gpg | sudo tee /etc/apt/keyrings/openvpn-as.gpg.key
sudo apt install apt-transport-https ca-certificates
sudo apt update
sudo apt install -y openvpn-as
```

After installation completed open admin ui (protocol must be https):

`https://your_server_ip_or_domain_name:943/admin`\
Also dont forget to allow port 943 using ufw.

To get connection config open `https://your_server_ip_or_domain_name:943` then login and retrieve configuration.



Not that, while using nginx and openvpn first you have to change host in openvpn access erver admin page then you should set http->https in nginx .
