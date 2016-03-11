## Description
<p>
There are several golang scripts that leverage with OpenVPN.</p>

<p>
1. vpn_init initializes MySQL database. it creates all necessary tables and inserts information into them.</br>
   usage : vpn_init db_host db_user db_password db_name auth_file</br>
   example : ./vpn_init mysql.host.com admin password users.txt</br>

   users.txt is a text file containing logins and passwords separated by :</br>
   
   Example:</br>
</br>
   user1:password1</br>
   user2.password2</br>
   ...</br>
   NOTE: your MySQL RDBMS should be reachable for vpn_init script with port 3306</br>
   </br>
</br>
2. auth - provides authentification for vpn users by password.</br>
   usage: put this string in OpenVPN configuration file:</br>

   auth-user-pass-verify "/etc/openvpn/auth/auth  db_host db_user db_password  db_name"  via-env</br>
</br>
</br>

3. logger - provides logging of users connections. this script stores information in database that was initialized before by vpn_init script.</br>

     usage:</br>
     client-connect "/etc/openvpn/auth/auth db_host db_user db_password  db_name"</br>
</br>
4. web - shows current information of connected users through web.</br>
	usage: ./web ip1 ip2 ipn</br>
	You can specify as many ips as you want.</br>
    Than you can go to any adress (http://ip1), and you should see information about all vpn servers.</br>
    NOTE: you should have configured management interface on every OpenVPN server like this:</br>
    </br>
    add this to your OpenVPN configuration file:  

    management port 5678
</p>
