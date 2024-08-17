# goldmanager-dockercompose
Docker-Compose template for Goldmanager.
# First time set up
Run docker compose up -d
# Update images
To update started instances run <br>
docker compose pull<br>
docker compose down<br>
docker compose up -d<br>
# Security aspects
The default user name is admin, default password is 'admin1password!'.<br>
Please change the password after first login and/or create a new user and disable or delete user admin!<br>
<br>
To enable TLS, you can refer to the example in "compose-tls.yaml", you will need to provide a PKCS12 keystore file which is named in the example as "tls.pfx".



