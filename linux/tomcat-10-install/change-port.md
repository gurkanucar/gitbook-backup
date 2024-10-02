# change port

```bash
sudo sed -i 's/port="8080"/port="<PORT>"/g' /opt/tomcat/conf/server.xml
sudo sed -i 's/address="127.0.0.1"/address="0.0.0.0"/g' /opt/tomcat/conf/server.xml

sudo ufw allow <PORT>
```
