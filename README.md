# Deploying your DB

### Follow the steps below to deploy your DB to ElephantSQL, and manage the deployed DB using Postico, [download Postico 2 here](https://eggerapps.at/postico2/)

1. Visit [ElephantSQL](https://elephantsql.com/), click on **Get a managed database today**, choose the free plan **Tiny Turtle**, signin with GitHub, add a name to your new instance, select **US-East-1 (Northern Virginia)**, review and then select **Create Instance**

2. Click on your new instance to open its details. Now open Postico, select new server, in the Nickname box I would recommend adding the name we assigned to the db in ElephantSQL, then copy what's in the server box in ElephantSQL's detail page minus the portion in the parenthesis (ex. raja.db.elephantsql.com) and paste it into the `Host` box in Postico, enter what is in the User & Default database value into the `Database` and `User` boxes in Postico, copy and paste the password box into the `password` box in Postico. Hit **connect**

3. Use the SQL Query box in the upper half of Postico to create your table and seed the table. You can reference your schema and seed files. You may need to disconnect from the server and reconnect to see the tables and data that you created. You can check your tables from the Browser section of the instance in ElephantSQL

4. To connect your deployed DB to your back-end server, in the .env file add a variable `CONNECTION_STRING=` and assign it the URL value in the details of your instance in ElephantSQL. In your **dbConfig.js** file add `const connectionstring = process.env.CONNECTION_STRING` and below add `const db = pgp(connectionstring)`.
Make sure you are importing dotenv and pgp.
Your dbConfig.js file should look something like this:
```js
const pgp = require("pg-promise")();
require("dotenv").config();

const connectionstring = process.env.CONNECTION_STRING
const db = pgp(connectionstring);

module.exports = db;
```


**ElephantSQL will be shut down Jan 27th 2025**

