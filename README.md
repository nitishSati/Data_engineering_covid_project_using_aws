# Data_engineering_covid_project_using_aws
In this project, we created a datawarehouse based on covid data using AWS.
The dataset used in project is from Amazon itself.Link to the dataset is https://aws.amazon.com/blogs/big-data/exploring-the-public-aws-covid-19-data-lake/
We used jupyter notebook for this project. 

First we uploaded all our data files to Amazon S3. 

![image](https://user-images.githubusercontent.com/59816163/223097710-9166cfed-4565-4707-8610-6d9a791f22b0.png)

Then we ran glue crawlers on our S3 data to have out data in Athena so that we can query it.

![image](https://user-images.githubusercontent.com/59816163/223098386-65f5fbb0-548b-406d-b9f8-9c42e7542880.png)

We have tables in Athena now

![image](https://user-images.githubusercontent.com/59816163/223099108-c4583730-ed6b-45f3-998d-f3517c4a5ae9.png)

We then build our dimension model as follows - 

![image](https://user-images.githubusercontent.com/59816163/223100030-baa515e5-2ec1-4564-ab76-48f64b0cdfba.png)

Then we build our dimension model on jupyter notebook using pandas and boto3 libraries, and stored it back to Amazon S3.

![image](https://user-images.githubusercontent.com/59816163/223100756-c6288f2e-9fc4-441e-8f46-fd569fcdce4b.png)

Now that we have our data is S3, we can create tables in redshift and put this data into those tables.
We can do this by multiple methods, simplest one is to create and load tables with data in redshift query editor. 2nd option is to crate a glue job that creates and loads tables in redshift. 3rd option is to connect to redhshift using python from our jupyter notebook and create and load tables from there. We used the 3rd option here. We connected to redshift using redshift_connector and then created tables into redshift. Then we used COPY command to load data from S3 to redshift tables.

![image](https://user-images.githubusercontent.com/59816163/223102742-429723b5-f59d-44f2-946a-cbf61ae65841.png)

Now can connect to Microsoft PowerBI or Tableau or any other visualization tool on this data warehouse and perform different type of analysis.
