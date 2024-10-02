# increase file upload limit

```bash
sudo nano /opt/tomcat/webapps/manager/WEB-INF/web.xml

#edit this
 <multipart-config>
      <!-- 50 MiB max -->
      <max-file-size><EDIT_HERE></max-file-size>
      <max-request-size><EDIT_HERE></max-request-size>
      <file-size-threshold>0</file-size-threshold>
    </multipart-config>

```
