github actions initial seteps

ssh -i id_ed25519 -T git@github.com
export GIT_SSH_COMMAND="ssh -i ~/.ssh/id_ed25519"

   git clone git@github.com:fazelshah/hprofile.git
   
     cd hprofile/
  
     unset GIT_SSH_COMMAND
    git config core.sshCommand "ssh -i ~/.ssh/id_ed25519 -F /dev/null"
    cat .git/config
    git config user.name fazelshah
    git config user.email fazelshah1@gmail.com

    cat .git/config
    


tar -czvf staging_public.tar.gz /home/girnarsfa/staging_public_html/

mysqldump -u your_username  --all-databases | gzip > all_databases_backup.sql.gz
mysqldump -u root -P 3306 --single-transaction --triggers --routines --events trustmark -p | gzip > /root/dbback/trustmark_01sept2022.sql.gz
mysqldump -v -u root -p'TupwfRYquKUuBk1KpZhfXPCQ8ByVWC' --databases masterdb_cars| gzip -c > dbdumpmaster.tar.gz
mysql login
gunzip
source path to dump
create user 'fazel'@'host' identified by 'fazel';
show grants for 'fazel'@'host';
GRANT SELECT, INSERT, UPDATE, DELETE, CREATE, DROP, REFERENCES, INDEX, ALTER, CREATE TEMPORARY TABLES, LOCK TABLES, EXECUTE, CREATE VIEW, SHOW VIEW, CREATE ROUTINE, ALTER ROUTINE, EVENT, TRIGGER ON trustmark_01sept2022.* TO 'trustmark_user'@'1.0.%';
drop user 'crmuser'@'localhost';
zcat dbdump.tar.gz | mysql -u root -pTupwfRYquKUuBk1KpZhfXPCQ8ByVWC
mysql -u root -p123 < dump.sql

 curl ifconfig.me(find public ip of ec2 instnace)

screen -S dumprestore
screen -ls
shift ad


 mysqldump -v -h 180.179.212.241 -uroot -p px7en4miVJ googleanalytics > googleanalytics.sql
CREATE TABLE new_table AS SELECT * FROM original_table;


###########################################################################################
#########################################################################################################


#####################################################################################################################################################################################################

######################################################################################################################################################################################################
graffna steps:

cat <<EOF | sudo tee /etc/yum.repos.d/influxdb.repo
[influxdb]
name = InfluxDB Repository - RHEL \$releasever
baseurl = https://repos.influxdata.com/rhel/\$releasever/\$basearch/stable
enabled = 1
gpgcheck = 1
gpgkey = https://repos.influxdata.com/influxdb.key
EOF

sudo yum install

systemctl start telegraf
systemctl status telegraf

wget -qO- https://repos.influxdata.com/influxdb.key | sudo tee /etc/apt/trusted.gpg.d/influxdb.asc >/dev/null
source /etc/os-release
echo "deb https://repos.influxdata.com/${ID} ${VERSION_CODENAME} stable" | sudo tee /etc/apt/sources.list.d/influxdb.list
sudo apt-get update && sudo apt-get install telegraf
cd /etc/telegraf

vi telegraf.conf

urls: http://1.0.1.134:8086
database: name of instance at two places
goto graffana
put url same as above and database

######################################################################################################################################################################################################
steps to change the instance types from t2 to t3 in asg (ena disabled to ena enabled servers)
1:create ami of existing server with no reboot enabled (this will be a backup ami )
1a: set one of the servers in asg to scalein mode
2. detach one instance from asg
3 stop the server which is detached
4: enable ena of this server using the command "aws ec2 modify-instance-attribute --instance-id instance_id --ena-support"
5: create an ami of this server
6: update the launch template of asg with this ami and new instance type
7: increase the number of instances in asg by one
8: check if the new instance in asg is of the instance type we wanted 
9: ask developers to deploy their code 
10: check from your end and  developers end if the server is receiving traffic
11: teminate the server which we have detached in step 2
12: terminate the older machine in asg and set back the min, desired and max to what it was at the beginnig




#######################################################################################################################################################################################################



######################################################################################################################################################################################################

ncdu /



 scp -r shared deployer@172.10.7.167:/home/deployer/Gaadi-inspection-prod-asg/prod/
 
 scp ec2-user@3.110.105.69:/var/lib/jenkins/jenkins.tar.gz /home/fazel/Music/


######################################################################################################################################################################################################




####################################################################################################################################################################################################






#####################################################################################################################################################################################################


                    
                    
########################################################################################################################################################################################################







#########################################################################################################################################################################################################



#######################################################################################################################################################################################################

aws ec2 modify-instance-attribute --instance-id i-076411150e9f6db06  --ena-support



1. m5.large - 2018 Nov. 

modinfo ena

ethtool -i eth0 

2. Power of the instance then run this command from aws CLI - aws ec2 modify-instance-attribute --instance-id i-076411150e9f6db06  --ena-support (change the instance type only)
3. change the instance into AMD and run the machine.
4. check all services and tool


#######################################################################################################################################################################################################

How to mount remote directory in linux
install sshfs on system on which you want to have remote directory mounted
copy publich key of ssshfs system to remote server
sshfs -o nonempty  cardekho@1.0.28.84:/var/www/html/ /var/www/html

######################################################################################################################################################################################################


timedatectl set-timezone Asia/Kolkata
########################################################################################################################################################################################################

server {
    listen 80;
    server_name user-profile.cardekho.com;
       error_log  /var/log/nginx/user-profile.cardekho.com.error_log  warn;
    access_log  /var/log/nginx/user-profile.cardekho.com.log;
  underscores_in_headers on;

   real_ip_header X-Forwarded-For;
   set_real_ip_from 0.0.0.0/0;

    client_max_body_size 50M;


  location /{
#    add_header X-Frame-Options "SAMEORIGIN";
    proxy_set_header   X-Real-IP $remote_addr;
    proxy_set_header   Host      $http_host;

    proxy_pass         http://eureka/;
    http://127.0.0.1:3046;

        real_ip_header X-Forwarded-For;
        set_real_ip_from 0.0.0.0/0;

          }


}

Connecting NGINX to PHP FPM

location / {
     index  index.php;
   }

location ~ [^/]\.php(/|$) {
    fastcgi_split_path_info ^(.+?\.php)(/.*)$;
    if (!-f $document_root$fastcgi_script_name) {
        return 404;
    }

    # Mitigate https://httpoxy.org/ vulnerabilities
    fastcgi_param HTTP_PROXY "";

    fastcgi_pass 127.0.0.1:9000;
    fastcgi_index index.php;

    # include the fastcgi_param setting
    include fastcgi_params;

    # SCRIPT_FILENAME parameter is used for PHP FPM determining
    #  the script name. If it is not set in fastcgi_params file,
    # i.e. /etc/nginx/fastcgi_params or in the parent contexts,
    # please comment off following line:
    # fastcgi_param  SCRIPT_FILENAME   $document_root$fastcgi_script_name;
}

########################################################################################################################################################################################################

chmod 700 .ssh
touch .ssh/authorized_keys
chmod 600 .ssh/authorized_keys
#######################################################################################################################################################################################################
[root@ip-1-0-225-129 logrotate.d]# cat f8-gateway.conf 
/home/deployer/f8-gateway.log {
  #size 50k
  su root root
  daily
  missingok
  rotate 5
  compress
  delaycompress
  notifempty
  copytruncate
  dateext
  dateformat -%Y-%m-%d-%s
}
########################################################################################################################################################################################################
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "VisualEditor0",
            "Effect": "Allow",
            "Action": "s3:ListBucket",
            "Resource": [
                "arn:aws:s3:::aws-sam-cli-managed-sam-pipeline-artifactsbucket-178ve3vdi6o6/*",
                "arn:aws:s3:::aws-sam-cli-managed-cardetection-artifactsbucket-eeylhfmrwxg5/*",
                "arn:aws:s3:::aws-sam-cli-managed-cardetection-artifactsbucket-5hcyc360k44p/*"
            ]
        },
        {
            "Sid": "VisualEditor1",
            "Effect": "Allow",
            "Action": "s3:*",
            "Resource": [
                "arn:aws:s3:::aws-sam-cli-managed-sam-pipeline-artifactsbucket-178ve3vdi6o6",
                "arn:aws:s3:::aws-sam-cli-managed-cardetection-artifactsbucket-5hcyc360k44p",
                "arn:aws:s3:::aws-sam-cli-managed-cardetection-artifactsbucket-eeylhfmrwxg5",
                "arn:aws:s3:::aws-sam-cli-managed-sam-pipeline-artifactsbucket-178ve3vdi6o6/*",
                "arn:aws:s3:::aws-sam-cli-managed-cardetection-artifactsbucket-eeylhfmrwxg5/*",
                "arn:aws:s3:::aws-sam-cli-managed-cardetection-artifactsbucket-5hcyc360k44p/*"
            ]
        }
    ]
}






########################################################################################################################################################################################################
> git clone https://github.com/edenhill/librdkafka.git
>cd librdkafka
>./configure
>make && make install
>sudo pecl install rdkafka-4.1.0
>locate php.ini
> vim /etc/php.ini
extension=rdkafka.so
> service httpd restart

########################################################################################################################################################################################################
<VirtualHost 0.0.0.0:80>
    DocumentRoot /home/prod/girnarsoft-central-dealer
    ServerName dealercentralapi.gaadi.com
    ServerAlias dealercentralapi.gaadi.com
   RewriteEngine On
    <Directory /home/prod/girnarsoft-central-dealer>
    Options -Indexes +IncludesNOEXEC +FollowSymLinks

<Limit GET HEAD POST PUT DELETE OPTIONS>
    Require all granted
</Limit>

   </Directory>


ProxyPreserveHost On
      ProxyPass / http://localhost:3000/
      ProxyPassReverse / http://localhost:3000/

    ErrorLog /var/log/dealercentralapi.gaadi.com-error_log
    CustomLog /var/log/dealercentralapi.gaadi.com_access_log common
    DirectoryIndex index.html index.htm index.php index.php4 index.php5
</VirtualHost>

#######################################################################################################################################################################################################
girnarsoft-gaadi-sfa-prod
ln -sfT /home/deployer/sfa/production/releases/20230213164730 /home/deployer/sfa/production/current
######################################################################################################################################################################################################
"EC2 Dashboard" has started on 5542807245. Attendees from "EC2 Dashboard" have been added to this meeting. They can't view chat messages that are sent before they join. 

Meetings using the same meeting ID at the same time are merged.
[February 21, 2023, 8:14 PM] Dubey, Ajeet: Steps
1. https://newrelic.com/pricing create Free account with office Email ID
2. Admin Login to EC2 instance and execute the script
ex - curl -Ls https://download.newrelic.com/install/newrelic-cli/scripts/install.sh | bash && sudo NEW_RELIC_API_KEY=<<API kEY>> NEW_RELIC_ACCOUNT_ID=<<AWS Accound ID>> /usr/local/bin/newrelic install
3. View the details on the dashboard.




aws ec2 describe-instances --query "Reservations[*].Instances[*].{Instance:InstanceId,Type:InstanceType,Name:Tags[?Key=='Name']|[0].Value,Status:State.Name}" --region us-east-1 | jq -r '.[] | map({Instance,Type,Name,Status}) | (first | keys_unsorted) as $keys | map([to_entries[] | .value]) as $rows | $keys,$rows[] | @csv'



#######################################################################################################################################################################################################
newrelic

curl -Ls https://download.newrelic.com/install/newrelic-cli/scripts/install.sh | bash && sudo  NEW_RELIC_API_KEY=NRAK-RPAEBCTAYVCOZEM5QB6IS7I0GEF NEW_RELIC_ACCOUNT_ID=3895939 /usr/local/bin/newrelic install -n php-agent-installer
Akeel Ahmad
3:29 PM
68be1cf9d5927f8ac903bd2befcd4429354eNRAL
Akeel Ahmad
3:32 PM
sudo yum install newrelic-php5
Akeel Ahmad
3:34 PM
68be1cf9d5927f8ac903bd2befcd4429354eNRAL
######################################################################################################################################################################################################
server {
    listen 80;
    #listen 443 ssl;
    server_name api-gateway.gaadi.com;
       error_log  /var/log/nginx/api-gateway.gaadi.com.cardekho.com.error_log;
    access_log  /var/log/nginx/api-gateway.gaadi.com.cardekho.com.log;
  underscores_in_headers on;
#ssl_certificate     /etc/nginx/ssl/STAR_gaadi_com.crt;
# ssl_certificate_key    /etc/nginx/ssl/STAR_gaadi_com.key;
#ssl_protocols       TLSv1 TLSv1.1 TLSv1.2;
    #ssl_ciphers         HIGH:!aNULL:!MD5;
   real_ip_header X-Forwarded-For;
   set_real_ip_from 0.0.0.0/0;

    client_max_body_size 50M;


  location /{
#    add_header X-Frame-Options "SAMEORIGIN";
    proxy_set_header   X-Real-IP $remote_addr;
    proxy_set_header   Host      $http_host;

    proxy_pass         http://mwh2ouq1a4.execute-api.ap-south-1.amazonaws.com/;

        real_ip_header X-Forwarded-For;
        set_real_ip_from 0.0.0.0/0;

#auth_basic "Restricted Content";
        #auth_basic_user_file /etc/nginx/.htpasswd;

          }


}

########################################################################################################################################################################################################


#################################################################################################################################################################################################################







###################################################################################################################################################################################################


#######################################################################################################################################################################################################

db.createUser({
  user: "girnarcare",
  pwd: "Gyt6t%gghGTy",
  roles: [{ role: "readWrite", db: "chatbot-girnar" }]
})
mongodb://girnarcare:Gyt6t%gghGTy@52.66.176.188:27017/chatbot-girnar


########################################################################################################################################################################################################

db.createUser({
  user: "chatbot",
  pwd: "mypassword123",
  roles: [{ role: "readWrite", db: "admin" }]
})
 mongo -u chatbot -p --authenticationDatabase admin
 image1.pricedekho.com.edgesuite.net
 
 ####################################################################################################################################################################################################
  db.createUser(
  {
    user: "useradmin",
    pwd: "admin@32RED",
    roles: [ { role: "userAdminAnyDatabase", db: "admin" } ]
  }
)

 mongo -u useradmin -p --authenticationDatabase admin
 #########################################################################################################################################################################################################
 gcsfuse --implicit-dirs pricedekho-imageperver-live-bucket /root/bucket
 
 
 ######################################################################################################################################################################################################
 
 sudo sh -c "echo -n 'rajendra:' >> /etc/nginx/.htpasswd"
  sudo sh -c "openssl passwd rajendra@123 >> /etc/nginx/.htpasswd"
  
  
  ####################################################################################################################################################################################################

  
  ###############################################################################################################################################################################################
 
  #####################################################################################################################################################################################################
  sudo sh -c "echo -n 'noc:' >> /etc/nginx/.htpasswd"
sudo sh -c "openssl passwd noc@3214Fdr >> /etc/nginx/.htpasswd"
########################################################################################################################################################################################################
Kubectl => Owner of Restaurant 
Master => One restaurant (Vaishali)
API Server => Waiter 
Controller Manager => Restaurant Manager
etcd => Keep data related Kitchen lines ( Line1 Veg, Line2 - Non veg)
Scheduler => 
Node => Veg section/Non veg Section
kublet => Talk to Central Kitchen 
Service => Delivery table (pick up orders)
