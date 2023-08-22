
 CMPE-282 
CLOUD SERVICES
Submitted To-Prof. Andrew Bond
    Project supervisor :- Prof. Andrew Bond


Rishikesh Andhare (016726203)

Steps:-
Create an Active Directory with a domain Name.
Create Ec2 Instance to host the virtual Machine as Windows.
Configured Public IPs and domain Name in Virtual Machine.
Populated Employees data(300k+) into local Database
Export the Employees data into output.csv file
Using the powershell in Virtual Machine populated the data into Active Directory 






Create and configured the Active directory in AWS with directory DNS name as “cloud-pramathanadig.com”

2) In Directory service , directory got created with the directory-name “cloud-pramathanadig.com” and type as Microsoft AD











4) Created EC2 instance , and selected Instance type as t2.large so that users more than 300k+ can be added and instance image as microsoft Windows OS.  






5) Using the Public IPv4 DNS, connected to the Remote Desktop Connection and using UserName and Password.

6) Using the Username and password connected to the EC2 Instance Windows virtual Machine.

7) Configure the DNS IP same as Active Directory in the Virtual Machine.


8) Configure the Domain Name “cloud-pramathanadig.com” in the virtual Machine which is the same in the Active Directory.

9) Restart the virtual Machine and login to it using the Credentials.
10) The Name of the Device got Changed and it got populated with the domain name.


11) Downloaded the necessary Active Directory tools and Install them in the Windows Virtual Machine .




12) In the beginning there will Only Admin User. and In the further steps we will populate it with other users


MYSQL Steps :-
Steps done to populate users into the local MySql database.
Populated with users from the sample user database https://github.com/datacharmer/test_db	into the local database.
Follow and run  all the queries  given in the employee.sql and all the required tables get created.
Populated the database “employees” with all the employees and department data.


Done Verification of all the data in the local Mysql database. And more than 300k+ users got populated in the local database.	



Extracted all the data into an output.csv file.

Then copy the output.csv file into the Host Virtual Machine.(Ec2 - Instance)

3)Run the Powershell ISE in Virtual Machine as Administrator  and write a script then run the script file .
SCRIPT:-
Import-Module activedirectory
#Store the data from ADUsers.csv in the $ADUsers variable
$ADUsers = Import-csv C:\Users\admin\Desktop\employees.csv
#Loop through each rows containing user details in the CSV file 
foreach ($User in $ADUsers)
{
#Read user data from each field in each row and assign the data to a variable as below	
	$Username 	= $User.userName
	$Password 	= $User.password
	$Firstname 	= $User.firstName
    $DisplayName= $User.displayName
	$Lastname 	= $User.lastName
	$OU 		= $User.OU
    $email      = $User.emailAddress
    $groups     = $User.memberOf


	#Check to see if the user already exists in AD
	if (Get-ADUser -F {SamAccountName -eq $Username})
	{
		 #If user does exist, give a warning
		 Write-Warning "A user account with username $Username already exist in Active Directory."
	}
	else
	{
		#User does not exist then proceed to create the new user account
		
        #Account will be created in the OU provided by the $OU variable read from the CSV file
		New-ADUser `
            -SamAccountName $Username `
            -UserPrincipalName $email `
            -Name "$Firstname $Lastname" `
            -GivenName $Firstname `
            -Surname $Lastname `
            -Enabled $True `
            -Path $OU `
            -DisplayName "$Lastname, $Firstname" `
            -Description $description `
            -AccountPassword (convertto-securestring $Password -AsPlainText -Force) -ChangePasswordAtLogon $False
	}
}

4) Once the script file is running and completed users will get added into the active directory and it will get displayed.



5) To verify and count how many Users get added into the active directory run the command “  (Get-AdUser -Filter *).Count” Into the powershell, we can see 300056 users got added(More than 300k+ for extra Credit)




References:-
https://docs.aws.amazon.com/directory-service/index.html
https://docs.aws.amazon.com/ec2/index.html
