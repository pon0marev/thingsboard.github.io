You'll need to set up AstraDB on DataStax. 
Follow [this](https://docs.datastax.com/en/astra-serverless/docs/manage/db/manage-create.html) guide, to create the database. Use "thingsboard" as the database name and keyspace.


Following [this](https://docs.datastax.com/en/astra-serverless/docs/manage/org/manage-tokens.html) guide, you need to generate a token with the **Database Administrator** role to install the Thingsboard schema. Save the credentials to a file. Later you will need the "Client ID" and the "Client Secret".

To establish a secure connection, follow [this](https://docs.datastax.com/en/astra-serverless/docs/connect/drivers/connect-java.html#_downloading_secure_connect_bundle) instruction and download the "secure connect bundle".

Copy the *secure-connect-thingsboard.zip* into the configuration folder and change the owner to **thingsboard**.
```bash
sudo cp ~/Downloads/secure-connect-thingsboard.zip /usr/share/thingsboard/conf/secure-connect-thingsboard.zip
sudo chown thingsboard:thingsboard /usr/share/thingsboard/conf/secure-connect-thingsboard.zip
```
{: .copy-code}

