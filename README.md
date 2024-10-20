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
# Updateing prices via REST API
Starting from version 0.9.0 goldmanager, supports the restapi provided by https://metalpriceapi.com for automatically updating metal prices.<br>
If enabled, goldmanager will also update the configured pricehistory range (METALPRICECOLLECTOR_FETCHHISTORYDAYS) on start up.<br>
For usage, you will need to obtain an api key from this provider and to configure the image environment accordingly.<br>
See the file compose-tls-priceupdate.yml as example configuration.<br>
## Relevant environment variables with examples:
METALPRICECOLLECTOR_APIKEY: apiKey #API key from metalpriceapi.com <br>
METALPRICECOLLECTOR_ENABLED: true #Enable automatic price update (default false)<br>
METALPRICECOLLECTOR_CURRENCY: USD #Currency see metalpriceapi.com currency symbols<br>
METALPRICECOLLECTOR_METALMAPPINGS: Gold=XAU,Silver=XAG #comma separated mapping from goldmanager metalname=rest api symbols<br>
METALPRICECOLLECTOR_FETCHHISTORYDAYS: 5  #number of days to fetch price history on startup (Note this uses 1 api call per mapped metal!), set to 0 to disable. This example causes goldmanager to update price history from the last 5 days after startup.<br>
METALPRICECOLLECTOR_FETCHINTERVALMINUTES: 60 #Interval in minutes to update prices: In this example the mapped prices will be updated every 60 minutes<br>


