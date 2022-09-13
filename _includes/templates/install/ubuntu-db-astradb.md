{% capture hybrid-info %}
ThingsBoard team recommends to use Hybrid database approach if you do plan to have 1M+ devices in production or high data ingestion rate (> 5000 msg/sec).
In this case, ThingsBoard will be storing timeseries data in AstraDB while continue to use PostgreSQL for main entities (devices/assets/dashboards/customers).  
{% endcapture %}
{% include templates/info-banner.md content=hybrid-info %}

##### PostgreSQL Installation

{% include templates/install/postgres-install-ubuntu.md %}

{% include templates/install/create-tb-db.md %}

##### AstraDB create database

{% include templates/install/astradb-setup.md %}

##### ThingsBoard Configuration

Edit ThingsBoard configuration file 

```bash 
sudo nano /etc/thingsboard/conf/thingsboard.conf
``` 
{: .copy-code}

Add the following lines to the configuration file. Don't forget **to replace** "PUT_YOUR_POSTGRESQL_PASSWORD_HERE" with your **real postgres user password**:

```bash
# DB Configuration 
export DATABASE_TS_TYPE=cassandra
export SPRING_JPA_DATABASE_PLATFORM=org.hibernate.dialect.PostgreSQLDialect
export SPRING_DRIVER_CLASS_NAME=org.postgresql.Driver
export SPRING_DATASOURCE_URL=jdbc:postgresql://localhost:5432/thingsboard
export SPRING_DATASOURCE_USERNAME=postgres
export SPRING_DATASOURCE_PASSWORD=PUT_YOUR_POSTGRESQL_PASSWORD_HERE
``` 
{: .copy-code}

Add the following parameters to configure your ThingsBoard instance to connect to AstraDB. **Replace** *PUT_YOUR_CLIENT_ID_HERE* and *PUT_YOUR_CLIENT_SECRET_HERE* with your *Client ID* and *Client Secret* from the downloaded file with your credentials:

```bash

export DATABASE_TS_TYPE: "cassandra"
export CASSANDRA_KEYSPACE_NAME=thingsboard
export CASSANDRA_CLOUD_SECURE_BUNDLE_PATH: "/usr/share/thingsboard/conf/secure-connect-thingsboard.zip"
# dbadmin
export CASSANDRA_CLOUD_CLIENT_ID: "PUT_YOUR_CLIENT_ID_HERE"
export CASSANDRA_CLOUD_CLIENT_SECRET: "PUT_YOUR_CLIENT_SECRET_HERE"
```
{: .copy-code}