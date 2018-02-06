# Using Cron Jobs to Schedule tasks
Cron Job allows us to automate commands or scripts on our server to complete repetitive tasks at scheduled time according to our desire.

We can write cron jobs in crontab. Crontab can be opened using the command `crontab -e` in Linux terminal, edit(`i`) and save(`Esc` `:` `wq`).  
##### Cronjob example:  
`* * * * * /home/user/Desktop/task.sh`
- this cron job will run 'task.sh' in every minute 

These asterisks represent the interval of repetition with which tasks are processed. In order, the asterisks represent:
1. Minute
2. Hour
3. Day of month
4. Month
5. Day of week   

* **Minutes** are specified as a number from `0 to 59`. **Hours** are specified as numbers from `0 to 23`. **Days of the month** are specified as numbers from `1 to 31`. **Months** are specified as numbers from `1 to 12`. **Days of the week** are specified as numbers from `0 to 7`, with Sunday represented as either/both 0 and 7.

* Some of the schedules that can be used to run cron jobs are listed below:
  - `* * * * * /home/user/Desktop/task.sh` (run in every minute)
  - `*/3 * * * * /home/user/Desktop/task.sh` (run in every 3 minute)
  - `55 23 30 4,6,9,11        * /home/user/Desktop/task.sh`   
    `55 23 31 1,3,5,7,8,10,12 * /home/user/Desktop/task.sh`    
    `55 23 28 2               * /home/user/Desktop/task.sh`     
    (run on the last day of the month - 3 separate cronjobs have been written)
  - `0 0 0 0 1,3 /home/user/Desktop/task.sh` (run on every Monday and Wednesday)    
 
- We can write a script in the `/home/user/Desktop/task.sh` file to be run using the cronjob

  ##### Example:
  ###### content of task.sh file:
  ```
  #parameters
  export USER="root" && \
  export PASSWORD="mysql_password" && \
  export DATABASE="db_name" && \
  export TABLE1="teacher" && \
  export TABLE2="user" && \
  export now="$(date +"%Y_%m_%d")" && \

  #log in to mysql
  mysql -u "$USER" -p "-p$PASSWORD" "$DATABASE" -e "SELECT "teacher.id","user.username","teacher.receivableAmount","user.email","user.phone_number" FROM "$TABLE1" LEFT JOIN "$TABLE2" ON "teacher.id"="user.id" WHERE "receivableAmount" IS NOT NULL" > /home/user/Desktop/"$now".csv
  mail -s "Monthly Report of Teachers" username@gmail.com -A /home/user/Desktop/"$now".csv
  ```
  
 - This script is for retrieve data from the databases, extract those data into a .csv file and finally to mail the created .csv file to the specified email.    
 - Emails can be sent by installing and configuring **SSMTP**.
    - To install SSMTP run `sudo apt-get install ssmtp`
    - Open configuration file:    
        `sudo vim /etc/ssmtp/ssmtp.conf`
    - Configure the following lines with your Gmail credentials    
        
       ```
       mailhub=smtp.gmail.com:587
       AuthUser=username@gmail.com
       AuthPass=gmailpassword
       UseTLS=YES
       UseSTARTTLS=YES
       ```
