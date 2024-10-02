---
description: >-
  https://askubuntu.com/questions/652556/uncomplicated-firewall-ufw-is-not-blocking-anything-when-using-docker
---

# linux docker port ufw deny problem

To deny port via ufw firewall in linux we have to make some configurations in docker:

<pre class="language-bash"><code class="lang-bash"><strong># update daemon.json
</strong><strong>sudo nano /etc/docker/daemon.json
</strong>
{
"iptables": false
}

#update etc/default/docker
sudo nano /etc/default/docker

DOCKER_OPTS="--iptables=false"

sudo systemctl restart docker

</code></pre>
