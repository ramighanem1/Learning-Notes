# Node.js server

Implement a server steps :
- Run this command to create a new package.json file in your project folder. 
    
        npm init -y 

- Create a new JavaScript file server.js in the project folder and add the following code:

        const express = require('express');
        const app = express();
        const port = 3000;

        app.get('/', (req, res) => {
        res.send('Hello World!');
        });

        app.listen(port, () => {
        console.log(`Server listening at http://localhost:${port}`);
        });

start the server

    npm start 

# Automatically restart their Node.js server
if we need to  automatically restart their Node.js server whenever changes are made to our code use Nodemon

first install the package by running the following command :

    npm install -g nodemon

start your Node.js server with this command

    nodemon


This will start your server and watch for any changes to the code. If a change is detected, Nodemon will automatically restart the server with the updated code.


# dotenv :
Node.js useful tool when working with configuration values or sensitive information that you don't want to hard-code into your code.

To use dotenv in your Node.js project, you need to follow these steps:

Install the dotenv module in your project by running the following command in your terminal:
    
    npm install dotenv
    
Create a .env file in the root directory of your project and add your environment variables in the format KEY=VALUE, one per line. 

For example:

make file .env

    PORT=3000
    DB_USER=myusername
    DB_PASSWORD=mypassword

Note that you should never commit this file to your version control system since it can contain sensitive information (use **.gitignore file**).

Load the environment variables into your Node.js 

    require('dotenv').config();

This will read the .env file and set the environment variables in the process.env object.

Access your environment variables in your Node.js application using the process.env object. For example:

    const port = process.env.PORT || 3000;
    const dbUser = process.env.DB_USER;
    const dbPassword = process.env.DB_PASSWORD;
    Note that the || operator is used to provide a default value (3000) for the port variable in case it is not defined in the .env file.

That's it! Now you can easily manage your environment variables in a separate file and avoid hard-coding them into your code.



# Database : 

to start the server using this command

    pg_ctl -D /home/linuxbrew/.linuxbrew/var/postgresql@14 start


Note: you need to start the server each time you reboot your machine, so you will need to run the command again if you are unable to connect

we can use a shortcut command that will make the proccess easier for you by creating an allias.

    echo 'alias sqlstart="pg_ctl -D /home/linuxbrew/.linuxbrew/var/postgresql@14 start"' >> ~/.profile
    echo 'alias sqlstop="pg_ctl -D /home/linuxbrew/.linuxbrew/var/postgresql@14 stop"' >> ~/.profile

now you can easily start the server using this short command

    sqlstart >>> this command will start the server
    sqlstop >>> this command will stop the server

comands :

    psql -> open shell
    \l ->  List all databases
    \c <Database-name> -> connect to this Database 
    \dt -> List database tables 
    \d <table-name> -> Describe a table
    \q -> Quit

    psql -d <Database-name> -f schema.sql


node.js code for Database

    // by default we cant see the req.body content so we use this middleware function  
    server.use(express.json());

    //Database - > 1. importing the pg 
    const pg = require('pg');

    //2. create obj from Client
    const client = new pg.Client(process.env.DATABASE_URL);

    .env -> DATABASE_URL=postgersql://localhost:5432/<Database-name>

    //3. connect the server with movies database
    client.connect()
    .then(()=>{
        server.listen(PORT, () => {
            console.log(`listening on ${PORT} : I am ready`);
        });  
    }) 