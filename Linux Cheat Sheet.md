# LINUX

## FILE AND DIRECTORY COMMANDS
1. List all files in a long listing (detailed) format

	ls -al


2. List all files by name only

	ls

3. Display the present working directory

	pwd

4. Create a directory

	mkdir directory_name

5. Remove (delete) file

	rm file

6. Remove the directory and its contents recursively

	rm -r directory_name

7. Force removal of file 

	rm -f file_name

8. Forcefully remove directory recursively

	rm -rf directory_name

9. Copy file1 to file2

	cp file1 file2

10. Copy source_directory recursively to destination. If destination exists, copy source_directory into destination, 
otherwise create destination with the contents of source_directory.

	cp -r source_directory destination

11. Rename or move file1 to file2. If file2 is an existing directory, move file1 into directory file2

	mv file1 file2

12. Create symbolic link to linkname

	ln -s /path/to/file linkname

13. Create an empty file.

	touch file

14. View the contents of file

	cat file

15. can run last command with root permission

	sudo !!

16. can exit root from 
 
	su <user_name> ==> su supuni

17. Display the last 10 lines of file and "follow" the file as it grows.

	tail -f file

########## example----

	tail -f prod.log ==> can view all logs

	tail -1000 prod.log ==> show last 1000 lines 

	tail -1000 prod.log | grep CRITICAL (show only critical errors)

#########Remove process from always start when computer on

1. show all the uploaded processes
	ls /etc/init.d/


2. remove it by

	sudo update-rc.d -f <process_name>.remove

3. start services and stop

	service <process_name> stop

	service <process_name> start

## PROCESS MANAGEMENT

1. Display your currently running processes

	ps

2. Display all the currently running processes on the system.

	ps aux

3. Display process information for processname

	ps aux | grep processname

4. Display cpu usage memory usage

	top

5. Kill process with process ID of pid

	kill pid


##### How to repair BIOS selection

1.verify that secure-boot disabled

2.Insert Ubuntu CD and select try with Ubuntu cd

3.open terminal

4.sudo apt-add-repository ppa:yannubuntu/boot-repair

5.sudo apt-get update

6.sudo apt-get install -y boot-repair

7.boot-repair

### SSH LOGINS

1. Connect to host as user

	ssh user@host

2. Normal Method

	ssh -i <path to file> user@host_name
	
	ssh -i .ssh/id_rsa.pub ubuntu@siplo.lk

### FILE TRANSFERS

1. Secure copy file.txt to the /tmp folder on server

	scp file.txt server:/tmp

2. Copy *.html files from server to the local /tmp folder.

scp server:/var/www/* .html /tmp

	scp root@192.168.8.125:/usr/share/freeswitch/conf/vanilla/vars.xml  /home/pi/
	
local machine to server

	scp /home/supuni/ubuntu/jitsi-images/  meetrix:/home/ubuntu

3. Copy all files and directories recursively from server to the current system's /tmp folder.

	scp -r server:/var/www /tmp


### DIRECTORY NAVIGATION

1. To go up one level of the directory tree.

	cd ..

2. Go to the $HOME directory

	cd

3. Change to the /etc directory

	cd /etc

### SYSTEM INFORMATION

1. Show the current date and time

	date

2. Show this month's calendar

	cal

3. Display USB devices

	lsusb -tv

### FILE PERMISSIONS

        PERMISSION      EXAMPLE

         U   G   W
        rwx rwx rwx     chmod 777 filename
        rwx rwx r-x     chmod 775 filename
        rwx r-x r-x     chmod 755 filename
        rw- rw- r--     chmod 664 filename
        rw- r-- r--     chmod 644 filename

# NOTE: Use 777 sparingly!

        LEGEND
        U = User
        G = Group
        W = World

        r = Read
        w = write
        x = execute
        - = no access

### NETWORKING

1. Display all network interfaces and ip address

	ifconfig -a

2. Send ICMP echo request to host

ping ip_address


### ARCHIEVES

1. Compress an Entire Directory or a Single File

	tar -czvf name-of-archive.tar.gz  /path/to/directory-or-file
	
2. Extract an Archive

	tar -xzvf archive.tar.gz  /to which folder 
	

### SEARCH

1. Search for pattern in file

	grep pattern <file_name>

2. Search recursively for pattern in directory

	grep -r pattern <directory_name>

3. Find files and directories by name

	locate name

4. Find files in /home/john that start with "prefix".

	find /home/john -name 'prefix*'

5. Find files larger than 100MB in /home

	find /home -size +100M

#### OTHER IMPORTANT COMMANDS

1. can view image sizes

	identify <jpg_name>.jpg

######### ImageMagick is a suite of command-line utilities for resizing, converting

convert howtogeek.png howtogeek.jpg //converting between format

convert howtogeek.png -quality 95 howtogeek.jpg //specify compression level

convert example.png -resize 200x100 example.png //resize image

convert example.png -resize 200x100! example.png // not considering ratio

convert example.png -resize 200 example.png // consider only width

convert example.png -resize x100 example.png // consider only height

convert howtogeek.jpg -rotate 90 howtogeek-rotated.jpg // rotate image

