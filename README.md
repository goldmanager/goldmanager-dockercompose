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
The default user name is admin, default password is 'adminpassword!'.<br>
Please change the password after first login and/or create a new user and disable or delete user admin!<br>
<br>
To enable TLS, you need to provide a ssl certificate and a private key inside a PKCS12 Keystore:
<br>
volumes:
    - ./path/to/local/keystore.p12:/path/in/container/keystore.p12<br>

change the host mapping ports<br>
ports:<br>
      - "8443:8443"<br>
<br>
Add the environment variables for Spring-Boot SSL configuration:<br>
<br>
 environment:<br>
 ..<br>
      - SERVER_SSL_KEY_STORE=/path/in/container/keystore.p12<br>
      - SERVER_SSL_KEY_STORE_PASSWORD=your-password<br>
      - SERVER_SSL_KEY_STORE_TYPE=PKCS12<br>
      - SERVER_SSL_KEY_ALIAS=myalias<br>


