Install and fire up the Sandbox using the instructions 
here: 
https://mapr.com/products/mapr-sandbox-hadoop/download/
http://maprdocs.mapr.com/home/SandboxHadoop/c_sandbox_overview.html. 

Use an SSH client such as Putty (Windows) or Terminal (Mac) to login. See below for an example:
use userid: user01 and password: mapr.

For VMWare use:  $ ssh user01@ipaddress 

For Virtualbox use:  $ ssh user01@127.0.0.1 -p 2222 

You can build this project with Maven using IDEs like Eclipse or NetBeans, and then copy the JAR file to your MapR Sandbox, or you can install Maven on your sandbox and build from the Linux command line, 
for more information on maven, eclipse or netbeans use google search. 

After building the project on your laptop, you can use scp to copy your JAR file from the project target folder to the MapR Sandbox:

use userid: user01 and password: mapr.
For VMWare use:  $ scp  nameoffile.jar  user01@ipaddress:/user/user01/. 

For Virtualbox use:  $ scp -P 2222 nameoffile.jar  user01@127.0.0.1:/user/user01/.  

Copy the data file from the project data folder to the sandbox using scp to this directory /user/user01/data/uber.csv on the sandbox:

For Virtualbox use:  $ scp -P 2222 data/*.csv  user01@127.0.0.1:/user/user01/data/. 

This example runs on MapR 5.2.1 with Spark 2.1  

You can run these examples in the spark shell by copy pasting  the code from the scala file in the spark shell after launching:
 
$spark-shell --master local[2]


Or you can run the applications with these steps:

Step 1: First compile the project: Select project  -> Run As -> Maven Install

Step 2: Copy the jar and data to the sandbox 

To run the  standalone :

spark-submit --class payment.ETLPayment --master local[2] mapr-spark-payment-1.0.jar /user/user01/data/payments.csv

See the MapR-DB shell doc here https://maprdocs.mapr.com/home/ReferenceGuide/mapr_dbshell.html

You can run the notebooks by importing the json file into Zeppelin.

You can view the Zeppelin notebook with the viewer here 

https://www.zepl.com/viewer/github/caroljmcdonald/mapr-spark-openpayment/blob/master/notebooks/MapRSparkPayment.json

