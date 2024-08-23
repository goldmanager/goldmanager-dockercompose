# goldmanager-dockercompose
Docker-Compose template for Goldmanager.
# First time set up
Run <i>docker compose up -d</i><br>
<br>
Please be aware that on initial start up it may take a while (about 10 minutes) until the goldmanager container is reachable on the exposed port (e.g. 8080/8443) since it waits for initial setup of the mariadb container even if docker compose signals that both containers are up and running.<br>
You can monitor the initial setup status by executing <i>docker logs goldmanager</i> and/or <i>docker logs mariadb</i>.
# Update images
To update started instances run <br>
<i>docker compose pull</i><br>
<i>docker compose down</i><br>
<i>docker compose up -d</i><br>
# Security aspects
The default user name is admin, default password is 'admin1password!'.<br>
Please change the password after first login and/or create a new user and disable or delete user admin!<br>
<br>
To enable TLS, you can refer to the example in "compose-tls.yaml", you will need to provide a PKCS12 keystore file which is named in the example as "tls.pfx".



