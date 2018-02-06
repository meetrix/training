Amazon Web Services offers reliable, scalable, and inexpensive cloud computing services.

Refer the original documentation for more details:
          https://aws.amazon.com/documentation

##### 1. CREATE AN EC2 INSTANCE
Create an instance by giving all details (AMI, type, storage, security group, ...)

Allocate a new elastic IP address

Associate with an elastic IP, so you can access the instace via ssh

##### 2. CHANGE INSTANCE TYPE 
Stop the server

Change the type as required (like from t2.micro to t2.medium)

Start server

##### 3. DETACH A VOLUME 
Mostly required when recovering data from a volume
Stop the server of volume (remeber its path: dev/sda1)

Detach it

Stop server where the volume will be attached

Attach it (remeber the path attaching: dev/xvdf)

Start the server

Use following commands to access and retrieve data from the volume attached:

		            lsblk                                        //to see partitions
		            sudo mkdir /newvolume                        //create mountpoint
		            sudo mount /dev/xvdf1 /newvolume/ -t ext4    //mount
		            now you can see content by cd /newvolume
		            sudo umount /dev/xvdf1                       //unmount volume

##### 4. ROUTING TRAFFIC TO AN AMAZON EC2 INSTANCE
Create a record set with required DNS name (nxtbase.de) in Route53 using private IP of instance

Change Web server config files in server appropriately (apache2, nginx)

Restart the Web server

##### 5. CREATE AN AMI
The usage of an existing ec2 instance for reusability of snapshot

Create an image from the EC2 instance you needed

You can see it from AMIs

##### 6. CHANGE SECURITY GROUP
Changing the security group of an instance according to security puposes

Either you can change the security group associated or you can add another group for the same instance

##### 7. ADD RULES TO A SECURITY GROUP 
To ensure the secure maintainence of the instances

Basically inbound and outbound rules can be added

Specially, inbound rules should be secured to avoid attacks by ruling with your IP (wifi ip), type, protocol and ports

##### 8. MERGE INSTANCES
