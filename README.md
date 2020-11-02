# TEAM TASK NO 1 

# ✴️ Whenever client uploads the file ( for ex - f.txt) of size 50MB and the replication is 3.
# ✴️ Does client takes the entire data to master or does master provides the IP addresses of Datanodes so that client can upload the file to the Datanodes.
# ✴️ Question: Who is the one uploading the file?
# ✴️ Answer: Client gets the IP from Master and uploads the file to DataNode.



# SOLUTION :

# First we go inside /etc/hadoop directory to configure hadoop configuration files.
![Screenshot 2020-11-02 09 48 09](https://user-images.githubusercontent.com/61896468/97840252-b431b600-1d09-11eb-8631-f89817903f64.png)
# Here in slave hdfs-site.xml file we have put our dn directory to share with master.
![Screenshot 2020-11-02 13 05 59](https://user-images.githubusercontent.com/61896468/97841618-37540b80-1d0c-11eb-91a9-67b082972df0.png)
# For master we have configured the same file also.
![Screenshot 2020-11-02 09 52 48](https://user-images.githubusercontent.com/61896468/97840258-b6941000-1d09-11eb-8415-3a247764c2cc.png)
#  Now we configure core-site.xml in all nodes including master,client and slave.
![Screenshot 2020-11-02 09 53 38](https://user-images.githubusercontent.com/61896468/97840260-b72ca680-1d09-11eb-94e6-d7568e8020a2.png)
# In slave and client ,give master public ip to do configuration.
![Screenshot 2020-11-02 09 56 38](https://user-images.githubusercontent.com/61896468/97840264-b85dd380-1d09-11eb-983e-61c2ba04df24.png)
# In master node,give 0.0.0.0 to allow all nodes within the cluster to contact master.
![Screenshot 2020-11-02 09 57 29](https://user-images.githubusercontent.com/61896468/97840267-b98f0080-1d09-11eb-8500-7f0328e376b0.png)
# Now we format namenode directory.
![Screenshot 2020-11-02 09 59 56](https://user-images.githubusercontent.com/61896468/97840270-bac02d80-1d09-11eb-9fd5-ffd265ab49b0.png)
# -->> Here we stated namenode.
![Screenshot 2020-11-02 10 00 27](https://user-images.githubusercontent.com/61896468/97840275-bd228780-1d09-11eb-8fc1-78d191514e3a.png)
# -->> And now started datanode.
![Screenshot 2020-11-02 10 00 51](https://user-images.githubusercontent.com/61896468/97840284-c0b60e80-1d09-11eb-93af-d71394a8b26f.png)
# -->> From client , file is uploading.
![Screenshot 2020-11-02 10 03 47](https://user-images.githubusercontent.com/61896468/97840286-c14ea500-1d09-11eb-97da-531bec59fd99.png)
# -->> in client packets file, Here client first connect to master to know which slave is available to use as master has all slave nodes metadata.
![Screenshot 2020-11-02 10 04 49](https://user-images.githubusercontent.com/61896468/97840288-c1e73b80-1d09-11eb-8eaa-428773f93bc2.png)
# -->> Now client can directly connect to slave 1 to upload first block.
![2020-11-01 (1)](https://user-images.githubusercontent.com/61896468/97840321-cad80d00-1d09-11eb-9101-d3002211361d.png)
# -->> Again client connect to slave 1 to upload second block.
![2020-11-01 (2)](https://user-images.githubusercontent.com/61896468/97840324-cc093a00-1d09-11eb-93c8-c49f643459a9.png)
# -->> For final block,once again client contact slave 1.
![2020-11-01 (3)](https://user-images.githubusercontent.com/61896468/97840327-cdd2fd80-1d09-11eb-80ad-e91dfc78612c.png)
# -->> In slave 1 packets file, slave 1 is first contacted by client and file is uploaded in three blocks in slave 1 through client.
![2020-11-01 (4)](https://user-images.githubusercontent.com/61896468/97840331-cf042a80-1d09-11eb-8c93-5739208fc9af.png)
# -->> Then slave 1 connect slave 2 to create replica.
![2020-11-01 (16)](https://user-images.githubusercontent.com/61896468/97840336-d0355780-1d09-11eb-8cbc-a1873c7e7ad4.png)
#  -->> In slave 2 packets file,as shown slave 2 is contacted by slave 1 and replica is created here .
![2020-11-01 (17)](https://user-images.githubusercontent.com/61896468/97840341-d1ff1b00-1d09-11eb-89fa-4de7d4f67cb0.png)
#  -->> Then slave 2 send another replica to slave 3.
![image](https://user-images.githubusercontent.com/61896468/97843901-14c3f180-1d10-11eb-8197-76f56ebf6053.png)
# *  -->> 
![image](https://user-images.githubusercontent.com/61896468/97843871-083f9900-1d10-11eb-987b-f57d1c353a3e.png)

![image](https://user-images.githubusercontent.com/61896468/97843952-2ad1b200-1d10-11eb-86f2-4f89c33c2258.png)

