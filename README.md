# Introduction To Amazon Aurora

This lab introduces you to Amazon Aurora and provides you with a basic understanding of how to use Aurora. You will follow the steps to create an Aurora instance and then connect to it.

Aurora is a type of database made by Amazon that works like MySQL (a popular database). It runs fast and is very reliable, like expensive databases, but it’s easier to use and cheaper, like free ones. It can be up to five times faster than regular MySQL, and you usually don’t need to change your existing MySQL apps to use it.

To complete the objective of the lab, let us follow these steps:

# STEP 1: CREATE AN AURORA INSTANCE

1.1 At the top of the AWS Management Console, in the search bar, search for and choose RDS.

1.2 In the left navigation menu, choose In the left navigation menu, choose **Databases**.

1.3 Choose Create database and then configure the following options:

   * For **Choose a database creation method**, choose **Standard create**.

   * For **Engine type**, choose **Aurora (MySQL Compatible)**.

   * For **Engine version**, choose the version specified as the **default for major version 8.0.**

   * For **Templates**, choose **Dev/Test**.

1.4 In the **Settings** section, configure the following options:

  * For **DB cluster identifier**, enter _aurora._

  * For **Master username**, enter _admin_.

  * For **Master password**, enter _admin123_.

  * For **Confirm password**, enter _admin123_.

1.5 In the **Instance configuration** section for the **DB instance class** section, choose **Burstable classes (includes t classes)**, and choose **db.t3.medium** from the dropdown list.

1.6 In the **Availability & durability** section for **Multi-AZ deployment**, choose **Don't create an Aurora Replica**.

 Note:  Amazon RDS Multi-AZ deployments provide enhanced availability and durability for DB instances, making them a natural fit for production database workloads. When you provision a Multi-AZ DB instance, Amazon RDS automatically creates a primary DB instance and synchronously replicates the data to a standby instance in a different Availability Zone.

Since this is a lab environment, you do not need to perform a multi-AZ deployment.

1.6 In the **Connectivity** section, configure the following options and leave any not mentioned with their default value:




<img width="701" height="172" alt="image" src="https://github.com/user-attachments/assets/3e225130-7863-4d80-88a7-332047fc3f5f" />



1.7 In the **Monitoring** section, clear the check box for **Enable Enhanced monitoring**.

1.8 Expand **Additional configuration** section. For **Initial database name**, enter _world_

1.9 In the **Encryption** section, clear the check box for **Enable encryption**.

**Note:** You can encrypt your Amazon RDS instances and snapshots at rest by enabling the encryption option for your RDS DB instance. Data that is encrypted at rest includes the underlying storage for a DB instance, its automated backups, read replicas, and snapshots.

1.10 In the **Maintenance** section, clear the check box for **Enable auto minor version upgrade**.

1.11 Scroll to the bottom of the screen, and then choose **Create database.**

 * **Task complete**: You have successfully created an Aurora instance


# STEP 2: CONNECT TO AN AMAZON EC2 LINUX INSTANCE

2.1 At the top of the AWS Management Console, in the search bar, search for and choose _EC2_.

2.2 In the left navigation menu, choose **Instances**.

2.3 Next to the instance labelled **Command Host**, select the check box, and then choose **Connect**.

2.4 For **Connect to instance**, choose **Session Manager**.

2.5 Choose **Connect** to open a terminal window.

**Task complete**: You have successfully connected to the Amazon EC2 instance named Command Host.

# STEP 3: CONFIGURE THE AMAZON EC2 LINUX INSTANCE TO CONNECT TO AURORA

 3.1 **Command**: To install the MariaDB client, run the following command. The MariaDB client is what you use in later steps to connect to the Aurora instance that you just created.






 
<img width="299" height="27" alt="image" src="https://github.com/user-attachments/assets/6be61f9f-9f8c-4a70-850c-43d9a79640dd" />








<img width="676" height="530" alt="image" src="https://github.com/user-attachments/assets/102a84a5-f355-44e9-9c15-617fe658b0b2" />





3.2 Using a different browser tab, go back to the AWS Management Console and in the search bar, search for and choose _RDS_.

3.3 In the left navigation menu, choose **Databases**.

3.4 Wait for **aurora-instance-1** to display  **Available** > Choose **aurora**

3.5 Choose the **Connectivity & security** tab, and in the **Endpoints** section, copy the **Endpoint name** for the **Writer instance** to your text editor.

3.6 **Copy edit**: In the following command, replace _<endpoint_goes_here>_ with the endpoint that you copied to your text editor.






<img width="554" height="68" alt="image" src="https://github.com/user-attachments/assets/ee67258d-236e-4643-88a9-a0894f89dc1e" />








<img width="732" height="341" alt="image" src="https://github.com/user-attachments/assets/8ed05dd5-93fe-4433-97c0-8f9fac4007df" />







3.7  **Command:** Return to the **Session Manager** browser tab that was used to connect to the **Command Host**. To connect to the Aurora instance, run the command you had copied in the previous step.

 





<img width="683" height="281" alt="image" src="https://github.com/user-attachments/assets/6e7e4749-696c-4902-8e51-cc8480b5836d" />





**Task complete**: You have successfully configured the Amazon EC2 Linux instance to connect to Aurora.


# STEP 4: CREATE A TABLE AND INSERT AND QUERY RECORDS

4.1 **Command**: To list the available databases, run the following command.







<img width="527" height="77" alt="image" src="https://github.com/user-attachments/assets/4665f37a-e6b5-49f6-8e28-2b038b39b9a7" />







<img width="725" height="430" alt="image" src="https://github.com/user-attachments/assets/1ccf5d17-1262-4f81-bd36-0bbdc57656b6" />



4.2 To switch to the **world** database that you created in Task 1 when you provisioned the Aurora instance, run the following command.








<img width="470" height="73" alt="image" src="https://github.com/user-attachments/assets/c4e75654-668a-43a2-9c7a-e2f765df48c0" />







<img width="728" height="224" alt="image" src="https://github.com/user-attachments/assets/ebdec70f-8a7e-4e7f-a4da-747d785a06d0" />




4.3 **Command**: To create a new table in the **world** database, run the following command.






<img width="691" height="491" alt="image" src="https://github.com/user-attachments/assets/0ba2013f-a767-49bd-bbdc-f3284cd3a4d6" />






<img width="732" height="246" alt="image" src="https://github.com/user-attachments/assets/8eb4bfd1-f5f5-4a2a-9a9a-541bafec4798" />



4.4  **Command**: To insert new records into the **country** table that you just created, run the following commands.







<img width="1077" height="375" alt="image" src="https://github.com/user-attachments/assets/93e7a015-8ffc-47ca-ba5f-2da0e98e43b3" />







<img width="731" height="222" alt="image" src="https://github.com/user-attachments/assets/49a77874-6a24-4c64-9111-b7bd3e8f00d3" />




4.5  **Command**: To query the table, run the following **SELECT** statement.






<img width="650" height="89" alt="image" src="https://github.com/user-attachments/assets/d445a58c-eb9e-45ea-b5a5-f6e7955925c2" />







<img width="729" height="154" alt="image" src="https://github.com/user-attachments/assets/5979c0a8-c91e-4fc3-9d84-7d89d6cf7c77" />






**Task complete**: You have successfully created a table named _country_, inserted data into the table, and queried records returning two results.


# Well Done!!

You have now successfully:

 * Created an Aurora instance.

 * Connected to a pre-created Amazon EC2 instance.

 * Configured the Amazon EC2 instance to connect to Aurora.

 * Queried the Aurora instance.
