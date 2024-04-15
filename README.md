# Postgres Setup

Welcome! This guide will help you set up **PostgreSQL** (often shorted to just Postgres) on your Windows or Mac computer. 

Postgres is a database management system. Uses for database systems include:

- Storing data.
- Searching for specific information within the data.
- Allowing multiple people to look at and change the data at the same time.
- Managing who is allowed to see the data and who can change it.
- Managing rules about the data. A rule might say November has 30 days. This means if someone enters November 31 as a date, this date will be rejected.

**Table of Contents**
- [Windows Postgres Installation](#windows-postgres-installation)
- [Mac Postgres Installation](#mac-postgres-installation)
- [Interacting with Databases](#interacting-with-databases)
  - [Play Around With `psql`](#play-around-with-psql)
  - [Tableplus](#tableplus)
- [Important Commands / Configuration](#important-commands--configuration)
- [Troubleshooting](#troubleshooting)

## Windows Postgres Installation 

1. Open up your Ubuntu Terminal
2. Make sure your Ubuntu packages are up to date by running the command: `sudo apt update`
3. Now, install Postgres by running the command: `sudo apt install postgresql postgresql-contrib`. You may have to type in `Y`, to allow it to proceed.
4. Confirm the installation and check the version number by running the command: `psql --version` and you should see a version number appear!
5. Check the status of your PostgreSQL server by running the command: `sudo service postgresql status`. It should say it is "down".
6. Turn on PostgreSQL. You can do so by running `sudo service postgresql start`. Check the status of postgres and it should be "online" on port 5432.

    > Check out the [Important Commands / Configuration](#important-commands--configuration) section of this page for more commands like this.

7. In order to access your Postgres databases, you'll need a user account (called a "role"). By default, the installation process creates a user called `postgres` which you can use. 
9.  Now, connect to the Postgres service as the `postgres` user and open the `psql` shell by running the command: `sudo -u postgres psql`
10. Once you have successfully entered the `psql` shell, you will see your command line change to look like this: `postgres=#`
11. Now we'll add a password for the `postgres` user. Run the command: `ALTER USER postgres WITH ENCRYPTED PASSWORD 'your password';`.

    > Replace the password with something short and memorable (e.g. `'123'` is fine). NOTE: Keep the quotation marks around your password and the semicolon!

Now, let's play around with Postgres! Jump down to the [⬇️ Interacting with Databases ⬇️](#interacting-with-databases) section.


## Mac Postgres Installation

1. Go to [https://postgresapp.com/](https://postgresapp.com/)
2. Click on the downloads tab
3. You should see something like "Postgres.app with PostgreSQL [version]". Click on this link to download Postgres to your Mac.
4. After it's finished downloading, install the program, and run it.
5. Now, you'll have to initialize your database. Click the Initialize button on the right-hand side. The Postgres app should now say **Running**
6. To let us use Postgres CLI commands, open up a terminal window and run this command `sudo mkdir -p /etc/paths.d &&
echo /Applications/Postgres.app/Contents/Versions/latest/bin | sudo tee /etc/paths.d/postgresapp`
1. Restart your terminal
2. In your terminal, type in `createdb example`. You should not get an error after the command runs. Now let's see it in action!
1. In order to access your Postgres databases, you'll need a user account (called a "role"). By default, the installation process creates a user called `postgres` which you can use. 
9.  Now, connect to the Postgres service as the `postgres` user and open the `psql` shell by running the command: `psql -U postgres`
10. Once you have successfully entered the `psql` shell, you will see your command line change to look like this: `postgres=#`
11. Now we'll add a password for the `postgres` user. Run the command: `ALTER USER postgres WITH ENCRYPTED PASSWORD 'your password';`.

    > Replace the password with something short and memorable (e.g. `'123'` is fine). NOTE: Keep the quotation marks around your password and the semicolon!

Next, let's play around with Postgres!

## Interacting with Databases

### Play Around With `psql`

Before you exit the `psql` terminal, let's learn a little bit about it. If you already exited it you can get back in through your terminal:

* **Windows:** `sudo -u postgres psql`
* **Mac:** `psql -U postgres`

The `psql` terminal is a way to manage your Postgres databases using a command-line interface. There are a few useful commands to know so you can get around. Try these out:

* `\l` 
  * This lists all of the databases. By default, you are given one called `postgres` and two protected ones called `template0` and `template1`.
* `CREATE DATABASE test;` 
  * Remember the semicolon!
  * This will create a new database managed by Postgres. Use the `\l` command again to see the updated list.
* `\c test` 
  * to connect to your new `test` database. You should see the command line prompt change to `test=#`
* `CREATE TABLE table_1 ();`
  * Remember the semicolon!
  * This will create a table with no columns
* `CREATE TABLE table_2 ( id INT, name TEXT );`
  * Remember the semicolon!
  * This will create a table with 2 columns called `id` and `name`. `id` values must be integers and `name` values can be any text.
* `SELECT * FROM table_2;` to see all rows from the `table_2` table.
  * Remember the semicolon!

You can now exit your psql shell by typing in `\q` and hitting enter

### Tableplus

Interacting with Postgres through the command-line interface may make you feel like a pro, but let's face it, it isn't the best. Tableplus is a GUI (graphical user interface) that makes viewing your databases much nicer.

1. Download [tableplus](https://tableplus.com/) from their website. Make sure to download the corresponding version for your OS.
2. After installing and opening the application, click the "Create A New Connection..." towards the bottom of the window. You will see a prompt to select the type of database you want to connect to. Select **Postgresql**.
3. Now, you'll enter the configurations for this connection:
    - The name of the connection is up to you. You can call it `marcy` or `postgres` if you'd like. In the future, if you ever want to connect to a different database server, you would set up a new connection and give it a descriptive name.
    - For Host, enter `localhost` or `127.0.0.1` (these are equivalent)
    - For Port, enter `5432`.
    - For the user field, enter `postgres`.
    - In the password field, enter the password you created for user `postgres` in step 10.
    - Leave the remaining fields blank

4.  Click the **test** button, and if everything is successful, all of the fields should be highlighted green! At that point, click **connect**, and you should be able to view the GUI client for your database. If you want, you can click the `SQL` button and write your own SQL queries.

    > **Note:** If you get a `Could not connect to server: Connection refused` error, this means you have to first start your postgres server.
    > 
    > **Windows**: in the terminal using the command `sudo service postgresql start`.
    >
    > **Mac**: Click the Start button so that the Red X turns into a Green checkmark.

    <img width="234" alt="Screen Shot 2022-10-11 at 4 19 14 PM" src="https://user-images.githubusercontent.com/30392423/195190310-8f4ed82c-bebd-4fb5-bc96-3fcaa2ed9848.png">

## Important Commands / Configuration

### Checking your Postgres server status
**For Windows users**, check your Postgres server status in your terminal:
- `sudo service postgresql status` - to see if your server is running 
- `sudo service postgresql start` - to start your postgresql server
- `sudo service postgresql restart` - to restart your postgresql server

**For Mac users**, check your Postgres server status through the Postgres application.
![Mac Postgres App](https://github.com/The-Marcy-Lab-School/postgres-setup/assets/111444562/e79795b0-8f95-4fe4-a1ff-2cc550748458)

### Connecting to the PSQL terminal

To connect to your Postgres server as the `postgres` user:
* **For Windows Users**: `sudo -u postgres psql`
* **For Mac Users**: `psql -U postgres`  

### Using the PSQL terminal

In your `psql` terminal:
- `\du` to see a list of users
- `\q` to quit
- `\l` to see a list of databases
- `\c database_name` to connect to a database
- `\dt` to see a list of tables in the connected database

And you can also run any SQL commands from the `psql` terminal (remember the semicolon!):

- `CREATE DATABASE db_name;` to create a new database 
- `SELECT * FROM table;` to see all rows from the given table
- `ALTER USER username WITH ENCRYPTED PASSWORD 'password';` to set a password (use single quotes)

### Tableplus Postgres Server Connection Configuration
- Host/Socket: `127.0.0.1` or `localhost`
- Port: `5432`
- User: Enter your username or `postgres`
- Database: `postgres` (the default will be the same as the user value)

## Troubleshooting

1. If you can't connect to your database because of `FATAL: password authentication failed for user <username>`, ask your instructor for help. They will do the following:

  * Find and edit your `pg_hba.conf` using `vim`: `sudo vim /etc/postgresql/12/main/pg_hba.conf` (where `12` is the version number) 
  * Alternately, find notepad or notepad++ in your start menu, right click, choose "Run as administrator", then use File->Open to open `pg_hba.conf` that way.
  * Update the `"host"` line for user `"postgres"` on host `"127.0.0.1/32"` from `"md5"` to `"trust"`. 
    * You can add the line if it isn't there; just insert `host all postgres 127.0.0.1/32 trust` before any other lines. (You can ignore comments, lines beginning with #).
  * Restart the PostgreSQL service: `sudo service postgresql restart`
  * Connect using `sudo -u postgres psql` / `psql`
  * Run `ALTER USER postgres PASSWORD 'fooBarEatsBarFoodBareFoot';` (don't forget the `;`!)
  * Remove the line you added to `pg_hba.conf` or change it back
  * Restart PostgreSQL again to bring the changes to effect.
  * Try connecting again
