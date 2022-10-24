# Stop and Start AWS resources by Tag
 

> This is a simple PHP script that uses the PHP SDK for AWS to stop and restart all Amazon EC2 instances and Amazon RDS databases within all regions **based on a set of tags**.
> 
> This enables scenarios such as shutting off your development environment servers at the end of the day and restarting them the next morning. 
> The script will look in every AWS region for instances that match the specified tags.

  
------------
#### About  the stopinator.php script:

The script takes the following arguments:

-   **-t**: A set of tags in the following format: `name=value;name=value` The script converts these tags into the format expected by the AWS PHP call `Ec2::DescribeInstance()`. If this optional parameter is absent, the script will identify and shut down all running Amazon EC2 instances in the account.
-   **-s**: A Boolean parameter; no arguments are required. When this parameter is present, instances identified by **-t** are started instead of stopped.
  


## Stopping  ERPProject Development Process
> To make it simple, I will assume that you are Stopping ERPProject Development Process EC2s.
> 
> *You can change this tags with yours*

Use the stopinator.php script to bring down your development environment for the **ERPSystem** project.

From the Linux shell, run the stopinator.php script:

```bash 
./stopinator.php -t"Project=ERPSystem;Environment=development"
```
If no arguments are supplied, stopinator script stops every Amazon EC2 and Amazon RDS instance running in an account.

The output should look like this, indicating number of instances will be stopped in your current AWS region:
```shell
Region is us-east-1 
	No instances to stop in region 
Region is us-west-1 
	No instances to stop in region 
Region is us-west-2 
	Identified instance i-9552ba9f 
	Identified instance i-d35fb7d9 
Stopping all identified instances... 
[…] 	
	No instances to stop in region 
Region is sa-east-1 
	No instances to stop in region
```
You can return to the EC2 Management Console window and verify that there is instances are stopping or have already been stopped


## Starting  ERPProject Development Process
>  I will assume that you changed your mind and need to start the ERPProject Development Process EC2.
> 
> *Remember you can change this tags with yours*

restart your instances with the following command:
```bash 
./stopinator.php -t"Project=ERPSystem;Environment=development" -s
```
  
Return to the EC2 Management Console window and verify that the instances that were previously shut down are now restarting.


 

## END
> I hope this was helpful to you :D

  
