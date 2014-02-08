django-gunicorn-ubuntu-mysql
============================

Manual how to set up an Ubuntu server running django+mysql+nginx+gunicorn


Taken from:
<ul>
<li>https://www.digitalocean.com/community/articles/how-to-install-and-configure-django-with-postgres-nginx-and-gunicorn</li>
<li>http://www.saltycrane.com/blog/2008/07/how-set-django-mysql-ubuntu-hardy/</li>
</ul>
# Preparation
        sudo apt-get update
        sudo apt-get upgrade
        
        sudo apt-get install python-virtualenv
        sudo apt-get install python-django
        sudo apt-get install mysql-server
        
        sudo apt-get install python-mysqldb
        sudo apt-get install python-dev
        sudo apt-get install libmysqlclient-dev
        sudo apt-get install git
        sudo apt-get install nginx

        mkdir projects
        cd projects

# Get your app from GIT

        git clone THE_REPOSITORY_WITH_YOUR_APP
        cd YOUR_APP
        sudo virtualenv /opt/your_app
        source /opt/your_app/bin/activate
# Install all the requirements
        pip install -r requirements.txt
        sudo apt-get install python-dev
        sudo apt-get install libmysqlclient-dev
        sudo apt-get install libevent-dev
        sudo apt-get install libxml2-dev libxslt1-dev
        pip install gunicorn

        deactivate
# Set up MySQL database
        mysql -u root -p
        mysql> CREATE DATABASE your_app_db;
        mysql> GRANT ALL ON your_app_db.* TO 'root'@'localhost' IDENTIFIED BY 'root';
        mysql> quit

# Run server
        
        cd your_app
        gunicorn_django --workers=3 --bind localhost:8000
        #Restart:
        #git pull
        #pkill gunicorn
        
Push code on server via git:
<ul>
<li>http://bobbelderbos.com/2012/03/push-code-remote-web-server-git/</li>
<li>http://markdotto.com/2011/11/02/how-to-deploy-sites-via-github/</li>
</ul>
Install phpmyadmin running on nginx
<ul>
<li>http://www.lonelycoder.be/nginx-php-fpm-mysql-phpmyadmin-on-ubuntu-12-04/</li>
<li>http://howitmake.ru/blog/ubuntu/93.html</li>
</ul>
