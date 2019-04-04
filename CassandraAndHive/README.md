## Cassandra and Hive Section

Here we have used Cassandra for storing data in key,value pair format and have used Hive to query aggregates out of it.
## Cassandra
### Running
#### To create a NAMESPACE and TABLE in Cassandra
```bash
reate keyspace games with
replication={'class':'SimpleStrategy','replication_factor':1};
USE VideoGame
CREATE ColumnFamily vidgames
(Name varchar PRIMARY KEY,
Platform varchar,
Year_of_Release varint,
Genre varchar,
Publisher varchar,
NA_Sales float,
EU_Sales float,
JP_Sales float,
Other_Sales float,
Global_Sales float,
Critic_Score varint,
Critic_Count varint,
User_Score float,
User_Count varint,
Developer varchar,
Rating varchar)
```
#### Copying data from HDFS into Cassandra
```bash
copy vidgames (name,platform,year_of_release,genre,publisher,na_sales,eu_sales,jp_sales,other_sales,global_sales,critic_score,critic_count,user_score,user_count,developer,rating) from 'dataset.csv' with HEADER=TRUE;
```
#### Checking if Data copied
```bash
select * from vidgames;
```
#### Creating INDEX in the table
```bash
create index pt on vidgames(platform);
```

#### Queries
```bash
select * from vidgames where platform='PS2';

select name from vidgames where user_count<25;
```
## HIVE
#### To create a table in hive
```bash
create table vidgames(name string,platform string,year_of_release int,genre string,publisher string,na_sales double,eu_sales double,jp_sales double,other_sales double,global_sales double,critic_score double,critic_count double,user_score double,user_count double,developer string,rating string);
```
#### To load data from CSV file
```bash
LOAD DATA LOCAL INPATH 'dataset.csv' OVERWRITE INTO TABLE vidgames;
```
#### Queries
```bash
select * from vidgames;

select count(distinct name) from vidgames;
```

## Output
### Cassandra
***
![dp1](https://raw.githubusercontent.com/YashMeh/BigDataProject/master/CassandraAndHive/New%20Doc%202019-04-04%2021.29.15_8.jpg)
***
***
![dp1](https://raw.githubusercontent.com/YashMeh/BigDataProject/master/CassandraAndHive/New%20Doc%202019-04-04%2021.29.15_10.jpg)
***
***
![dp1](https://raw.githubusercontent.com/YashMeh/BigDataProject/master/CassandraAndHive/New%20Doc%202019-04-04%2021.29.15_11.jpg)
***
***
![dp1](https://raw.githubusercontent.com/YashMeh/BigDataProject/master/CassandraAndHive/New%20Doc%202019-04-04%2021.29.15_9.jpg)
***

### HIVE
***
![dp1](https://raw.githubusercontent.com/YashMeh/BigDataProject/master/CassandraAndHive/WhatsApp%20Image%202019-04-05%20at%2012.02.01%20AM%20(1).jpeg)
***
***
![dp1](https://raw.githubusercontent.com/YashMeh/BigDataProject/master/CassandraAndHive/WhatsApp%20Image%202019-04-05%20at%2012.02.01%20AM%20(2).jpeg)
***
***
![dp1](https://raw.githubusercontent.com/YashMeh/BigDataProject/master/CassandraAndHive/WhatsApp%20Image%202019-04-05%20at%2012.02.01%20AM.jpeg)
***







