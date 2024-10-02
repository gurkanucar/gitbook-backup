# Tomcat 10 Install

Run scripts below:

<pre class="language-bash"><code class="lang-bash"># Create tomcat group and user
sudo groupadd tomcat
sudo useradd -s /bin/false -g tomcat -d /opt/tomcat tomcat

# Download and extract Tomcat
cd /tmp
<strong>wget https://dlcdn.apache.org/tomcat/tomcat-10/v10.1.28/bin/apache-tomcat-10.1.28.tar.gz
</strong>sudo mkdir /opt/tomcat
sudo tar xzvf apache-tomcat-10.1.28.tar.gz -C /opt/tomcat --strip-components=1

# Set permissions

sudo chmod -R 777 /opt/tomcat \
        &#x26;&#x26; sudo chown -R tomcat:tomcat /opt/tomcat/ \
        &#x26;&#x26; sudo chmod -R g+r /opt/tomcat/conf \
        &#x26;&#x26; sudo chmod +x /opt/tomcat/bin \
        &#x26;&#x26; sudo chmod g+x /opt/tomcat/conf



# Create systemd service file
cat &#x3C;&#x3C;EOL | sudo tee /etc/systemd/system/tomcat.service
[Unit]
Description=Apache Tomcat Web Application Container
After=network.target

[Service]
Type=forking
WorkingDirectory=/opt/tomcat/webapps

Environment=JAVA_HOME=/usr/lib/jvm/java-17-openjdk-amd64
Environment=CATALINA_PID=/opt/tomcat/temp/tomcat.pid
Environment=CATALINA_HOME=/opt/tomcat
Environment=CATALINA_BASE=/opt/tomcat
Environment=CATALINA_OPTS=-Xms512M -Xmx1024M -server -XX:+UseParallelGC
Environment=JAVA_OPTS=-Djava.awt.headless=true -Djava.security.egd=file:/dev/v/urandom

ExecStart=/opt/tomcat/bin/startup.sh
ExecStop=/opt/tomcat/bin/shutdown.sh

User=tomcat
Group=tomcat
UMask=0007
RestartSec=10
Restart=always

[Install]
WantedBy=multi-user.target
EOL

# Reload systemd and start Tomcat
sudo systemctl daemon-reload
sudo systemctl enable tomcat
sudo systemctl start tomcat

# Open port 8080 in the firewall
sudo apt install ufw -y
sudo ufw allow 8080

# Add user to tomcat-users.xml
sudo sed -i '/&#x3C;\/tomcat-users>/i \
&#x3C;role rolename="tomcat"/>\n\
&#x3C;role rolename="admin-gui"/>\n\
&#x3C;role rolename="manager"/>\n\
&#x3C;role rolename="manager-gui"/>\n\
&#x3C;role rolename="manager-script"/>\n\
&#x3C;role rolename="manager-jmx"/>\n\
&#x3C;role rolename="manager-status"/>\n\
&#x3C;user username="admin" password="pass123" roles="tomcat,admin-gui,manager,manager-gui,manager-script,manager-jmx,manager-status"/>\
' /opt/tomcat/conf/tomcat-users.xml


# Comment out &#x3C;Valve> tags in context.xml files
sudo sed -i ':a;N;$!ba;s/&#x3C;Valve className="org.apache.catalina.valves.RemoteAddrValve"[^>]*\/>/&#x3C;!-- &#x26; -->/g' /opt/tomcat/webapps/manager/META-INF/context.xml
sudo sed -i ':a;N;$!ba;s/&#x3C;Valve className="org.apache.catalina.valves.RemoteAddrValve"[^>]*\/>/&#x3C;!-- &#x26; -->/g' /opt/tomcat/webapps/host-manager/META-INF/context.xml


# Set additional permissions and restart Tomcat
sudo chown -R tomcat /opt/tomcat/webapps/ /opt/tomcat/work/ /opt/tomcat/temp/ /opt/tomcat/logs/
sudo chmod +x /opt/tomcat/conf/
sudo systemctl restart tomcat

</code></pre>
