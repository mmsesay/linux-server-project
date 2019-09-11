# linux-server-project
This is the udacity linux server configuration project

## Login using the SSH
1. Create a file into this folder ```sudo touch ~/.ssh/<keyname>```
2. Edit the file and paste the ssh key I submitted. ```sudo vim ~/.ssh/<keyname>```
3. Open your terminal and type in change the permission to the file ```chmod 600 ~/.ssh/<keyname>```
4. Now login using the ssh. Type: ```ssh -i ~/.ssh/<keyname> grader@18.195.116.250``` or ```ssh grader@18.195.116.250```

## Server Details
- IP address : 18.195.116.250
- SSH PORT : 2200
- HOSTED APPLICATION URL : http://18.195.116.250/
- Passphrase : udacity
- Note: your grader password is: grader


## Installed 
1. **Apache2** ```sudo apt-get install apache2```
2. An application handler - **mod_wsgi**```sudo apt-get install python-setuptools libapache2-mod-wsgi```
3. **Postgresql**```sudo apt-get install postgresql```
4. **sqlalchemy** : command: ```sudo easy_install sqlalchemy```
5. **pip** : command ```sudo apt-get install python-pip```
6. **flask-login** : command: ```pip install flask-login```
7. **oauth2client** : visit-> https://oauth2client.readthedocs.io/en/latest/ or type: ```pip install --upgrade oauth2client```
8. **httplib2** : command: ```pip install httplib2```
9. **requests** : command: ```pip install requests``` or ```easy_install requests```
10. **Dependencies** ```sudo pip install -r requirements.txt```
11. **psycopg2** ```sudo apt-get -qqy install postgresql python-psycopg2```

## Configuration Changes 
1. **Firewall**
    ```sudo ufw allow 2200/tcp ```
    ```sudo ufw allow 80/tcp```
    ```sudo ufw allow 123/udp```
    ```sudo ufw enable```
2. **Apache2**: ```sudo nano /etc/apache2/sites-available/FlaskApp.conf```
    <VirtualHost *:80>
        ServerName 18.184.54.64
        ServerAdmin maej_01@hotmail.com
        WSGIScriptAlias / /var/www/FlaskApp/flaskapp.wsgi
        <Directory /var/www/FlaskApp/FlaskApp/>
            Order allow,deny
            Allow from all
        </Directory>
        Alias /static /var/www/FlaskApp/FlaskApp/static
        <Directory /var/www/FlaskApp/FlaskApp/static/>
            Order allow,deny
            Allow from all
        </Directory>
        ErrorLog ${APACHE_LOG_DIR}/error.log
        LogLevel warn
        CustomLog ${APACHE_LOG_DIR}/access.log combined
    </VirtualHost>

## Thid party resources
- Amazon LightSail