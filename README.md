# Postgres Setup

## Windows
1. Open up your Ubuntu Terminal
2. Update your Ubuntu packages: `sudo apt update`
3. Now, type `sudo apt install postgresql postgresql-contrib`. You may have to type in `Y`, to allow it to proceed. This will install postgres on your Ubuntu machine.
4. Confirm installation and get the version number: `psql --version`
5. Afterwards, you'll probably have to start the postgres database. You can do so by running `sudo service postgresql start`. Afterwards, you can check the status by running `sudo service postgresql status`.
6. Afterwards, you'll need to set up a password for the postgres user so you can log into the database. You can do this by running `sudo passwd postgres`. NOTE: make this something very easy to remember. You won't see anything in terminal but rest assured, it's taking in your input.
7. Close and reopen your terminal.
8. Now we are going to create a new user: `sudo -u postgres createuser [replace this with your username]`
9. Now, connect to the postgres service and open the psql shell: `sudo -u postgres psql`
10. Once you have successfully entered the psql shell, you will see your command line change to look like this: `postgres=#`
11. Now we'll add a password for the user you created earlier: `alter user [username] with encrypted password '[password]';`. Replace the username with the username you created earlier, and make your password short and memorable. NOTE: Keep the quotation marks around your password!
12. Let's make our user a superuser: `ALTER USER [username] WITH SUPERUSER;`
13. You can now exit your psql shell by typing in `\q` and hitting enter
14. You will download a GUI application called [tableplus](https://tableplus.com/) from their website. Make sure to download the corresponding version for your OS.
15. After installing and opening the application, click the "Create A New Connection..." towards the bottom of the window. You will see a prompt to select your database type. Select Postgresql.
16. Now you'll enter the credetials to access your database. Enter the name as "postgres". For Host, enter "localhost" or "127.0.0.1". For Port, enter "5432". For the user field enter the username you specified earlier in step 8. In the password field, enter the password you created for that user in step 11. Lastly, enter the name of the database as "postgres". Click the test button and if everything is successful, all of the fields should be highlighted green! At that point click connect and you should be able to see view the GUI client for you database. If you want, you can click the `SQL` button and write your own sql queries.

## Mac

1. Go to [https://postgresapp.com/](https://postgresapp.com/)
2. Click on the downloads tab
3. You should see something like "Postgres.app with PostgreSQL [version]". Click on this link to download Postgres to your mac.
4. After it's finish downloading, install the program, and run it.
5. Now you'll have to initialize your database. Click the Initialize button on the right hand side.
6. Open up a terminal window (hint: you can press `command` + `space` and type in terminal) and paste this inside `sudo mkdir -p /etc/paths.d &&
echo /Applications/Postgres.app/Contents/Versions/latest/bin | sudo tee /etc/paths.d/postgresapp`
7. To test that this command works, you'll have to restart your terminal.
8. In your terminal type in `createdb example`. You should not get an error after the command runs. Now let's see it in action!
9. You will download a GUI application called [tableplus](tableplus.com) from their website. Make sure to download the corresponding version for your OS.
10. After installing and opening the application, click the "Create A New Connection..." towards the bottom of the window. You will see a prompt to select your database type. Select Postgresql.
11. Now you'll enter the credetials to access your database. Enter the name as "postgres". For the user field enter "postgres" and in the database field enter "example". Click the test button and if everything is successful, all of the fields should be highlighted green! At that point click connect and you should be able to see view the GUI client for you database. If you want, you can click the `SQL` tab and write your own sql queries.


## Video Walkthrough
If you'd like, you can follow along using this [video](https://us02web.zoom.us/rec/play/U0ghC07ndSiayEEc1D86cvrNIiBIQhmyT7JU8sqrYJ928FHhZhKfq7OeYK73u1aRp6Qjb34kf32xoARm.7BAFARTMcCax8YDy?continueMode=true&_x_zm_rtaid=euzsucDSTBKnY0bdQQBC5A.1648070136259.165c763c787813cfbdcf7752e530272c&_x_zm_rhtaid=405).

* For Windows users, start at 1 hour and 9 minutes time stamp 01:09:00.
* For Mac users, start at 1 hour and 27 minutes time stamp 01:27:00.
