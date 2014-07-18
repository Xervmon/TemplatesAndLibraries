boxonline:
----------

Assumptions:
------------
1. Ansible Framework is installed on the Host machine which orchestrates playbooks.
2. The image of target server is Amazon Linux category.
2. Apache, php and mysql are installed in the same server.(Alternatively you can create different server to install mysql. Don't forget to add that server's hostname in the inventory file)

Instructions:
-------------
1. Clone the repository or download the zip file and extract.

2. cd boxonline-master/

3. Open inv file with any text editor. put the target server's hostname in the ec2_server section.

4. ansible-playbook -v -i inv --private-key path_to_privatekey main.yml
5. Step #4 would install all the dependencies. The default installation would have not root user right privileges.
   a. You would need ro sudo rm -fr /var/lib/mysql and then restart the server (sudo service mysql restart), 
       this is mysql output after cleaning which solved the 

      Initializing MySQL database: Installing MySQL system tables...
      
    OK
    Filling help tables...
    OK
  
  To start mysqld at boot time you have to copy
  support-files/mysql.server to the right place for your system
  PLEASE REMEMBER TO SET A PASSWORD FOR THE MySQL root USER !
  To do so, start the server, then issue the following commands:
  /usr/bin/mysqladmin -u root password 'new-password'
  /usr/bin/mysqladmin -u root -h ip-10-117-75-88 password 'new-password'
  
  Alternatively you can run:
  /usr/bin/mysql_secure_installation
  
  which will also give you the option of removing the test databases and anonymous user created by default. This is    
  strongly recommended for production servers.
  
  See the manual for more instructions.
  You can start the MySQL daemon with:
  cd /usr ; /usr/bin/mysqld_safe &
  You can test the MySQL daemon with mysql-test-run.pl
  cd /usr/mysql-test ; perl mysql-test-run.pl
  
TODO:
-----
1. Add Debian support and test.
2. Memcached installation is successful but configuring memcache is failing.
