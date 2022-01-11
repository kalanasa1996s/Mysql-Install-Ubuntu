# Mysql-Install-Ubuntu
Install MySQL on Ubuntu

1. Install mysql server

        sudo apt install mysql-server
        
2.Configuring MySQL - Run the security script

        sudo mysql_secure_installation

3.Adjusting User Authentication and Privileges

        step 1:

        sudo mysql
        
       mysql> SELECT user,authentication_string,plugin,host FROM mysql.user;
        
        Output
          +------------------+-------------------------------------------+-----------------------+-----------+
          | user             | authentication_string                     | plugin                | host      |
          +------------------+-------------------------------------------+-----------------------+-----------+
          | root             |                                           | auth_socket           | localhost |
          | mysql.session    | *THISISNOTAVALIDPASSWORDTHATCANBEUSEDHERE | mysql_native_password | localhost |
          | mysql.sys        | *THISISNOTAVALIDPASSWORDTHATCANBEUSEDHERE | mysql_native_password | localhost |
          | debian-sys-maint | *CC744277A401A7D25BE1CA89AFF17BF607F876FF | mysql_native_password | localhost |
          +------------------+-------------------------------------------+-----------------------+-----------+
          4 rows in set (0.00 sec)

          
          step 2:
          
         mysql> ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';

         mysql> FLUSH PRIVILEGES;
          
         mysql> SELECT user,authentication_string,plugin,host FROM mysql.user;
          
          
          Output
            +------------------+-------------------------------------------+-----------------------+-----------+
            | user             | authentication_string                     | plugin                | host      |
            +------------------+-------------------------------------------+-----------------------+-----------+
            | root             | *3636DACC8616D997782ADD0839F92C1571D6D78F | mysql_native_password | localhost |
            | mysql.session    | *THISISNOTAVALIDPASSWORDTHATCANBEUSEDHERE | mysql_native_password | localhost |
            | mysql.sys        | *THISISNOTAVALIDPASSWORDTHATCANBEUSEDHERE | mysql_native_password | localhost |
            | debian-sys-maint | *CC744277A401A7D25BE1CA89AFF17BF607F876FF | mysql_native_password | localhost |
            +------------------+-------------------------------------------+-----------------------+-----------+
            4 rows in set (0.00 sec)
          
          mysql> exit
          
          
          
