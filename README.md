# Postgres Setup

## Windows
- Open up your Ubuntu Terminal
- Update your Ubuntu packages: `sudo apt update`
- Now, type `sudo apt install postgresql postgresql-contrib`. You may have to type in `Y`, to allow it to proceed. This will install postgres on your Ubuntu machine.
- Confirm installation and get the version number: `psql --version`
- Afterwards, you'll probably have to start the postgres database. You can do so by running `sudo service postgresql start`. Afterwards, you can check the status by running `sudo service postgresql status`.
- Afterwards, you'll need to set up a password for the postgres user so you can log into the database. You can do this by running `sudo passwd postgres`. NOTE: make this something very easy to remember. You won't see anything in terminal but rest assured, it's taking in your input.
- Close and reopen your terminal.
- Now we are going to create a new user: `sudo -u postgres createuser [replace this with your username]`
- Now, connect to the postgres service and open the psql shell: `sudo -u postgres psql`
- Once you have successfully entered the psql shell, you will see your command line change to look like this: `postgres=#`
- Now we'll add a password for the user you created earlier: `alter user [username] with encrypted password '[password]';`. Replace the username with the username you created earlier, and make your password short and memorable. NOTE: Keep the quotation marks around your password!
- You can now exit your psql shell by typing in `\q` and hitting enter
- You will download a GUI application called [tableplus](tableplus.com) from their website. Make sure to download the corresponding version for your OS.
- After installing and opening the application, click the "Create A New Connection..." towards the bottom of the window. You will see a prompt to select your database type. Select Postgresql.
- Now you'll enter the credetials to access your database. Enter the name of the database as "Example DB". For the user field enter the username you specified earlier and in the password field enter the password you created for that user. Click the test button and if everything is successful, all of the fields should be highlighted green! At that point click connect and you should be able to see view the GUI client for you database. If you want, you can click the `sql` tab and write your own sql queries.

## Mac

- Go to [https://postgresapp.com/](https://postgresapp.com/)
- Click on the downloads tab
- You should see something like "Postgres.app with PostgreSQL [version]". Click on this link to download Postgres to your mac.
- After it's finish downloading, install the program, and run it.
- Now you'll have to initialize your database. Click the initialize button on the right hand side.
- Open up a terminal window (hint: you can press `command` + `space` and type in terminal) and paste this inside `sudo mkdir -p /etc/paths.d &&
echo /Applications/Postgres.app/Contents/Versions/latest/bin | sudo tee /etc/paths.d/postgresapp`
- To test that this command works, you'll have to restart your terminal.
- In your terminal type in `createdb example`. You should not get an error after the command runs. Now let's see it in action!
- You will download a GUI application called [tableplus](tableplus.com) from their website. Make sure to download the corresponding version for your OS.
- After installing and opening the application, click the "Create A New Connection..." towards the bottom of the window. You will see a prompt to select your database type. Select Postgresql.
- Now you'll enter the credetials to access your database. Enter the name of the database as "Example DB". For the user field enter `postgres` and in the database field enter example. Click the test button and if everything is successful, all of the fields should be highlighted green! At that point click connect and you should be able to see view the GUI client for you database. If you want, you can click the `sql` tab and write your own sql queries.

If you'd like, you can follow along at the 1:09 mark from class to watch us do it live. [video](https://us02web.zoom.us/rec/play/U0ghC07ndSiayEEc1D86cvrNIiBIQhmyT7JU8sqrYJ928FHhZhKfq7OeYK73u1aRp6Qjb34kf32xoARm.7BAFARTMcCax8YDy?continueMode=true&_x_zm_rtaid=euzsucDSTBKnY0bdQQBC5A.1648070136259.165c763c787813cfbdcf7752e530272c&_x_zm_rhtaid=405)