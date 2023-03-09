## Hive Commands
 - S3 bucket address : s3://aws-logs-116903467531-us-east-2/elasticmapreduce/j-BB2W0CNKWL4W/node/data/
 - SQL command
 
           CREATE EXTERNAL TABLE delayed_flights (
           Year INT,
           Month INT,
           DayofMonth INT,
           DayOfWeek INT,
           DepTime INT,
           CRSDepTime INT,
           ArrTime INT,
           CRSArrTime INT,
           UniqueCarrier STRING,
           FlightNum INT,
           TailNum STRING,
           ActualElapsedTime INT,
           CRSElapsedTime INT,
           AirTime INT,
           ArrDelay INT,
           DepDelay INT,
           Origin STRING,
           Dest STRING,
           Distance INT,
           TaxiIn INT,
           TaxiOut INT,
           Cancelled INT,
           CancellationCode STRING,
           Diverted INT,
           CarrierDelay INT,
           WeatherDelay INT,
           NASDelay INT,
           SecurityDelay INT,
           LateAircraftDelay INT
       )
       ROW FORMAT DELIMITED
       FIELDS TERMINATED BY ','
       STORED AS TEXTFILE
       LOCATION 's3://aws-logs-116903467531-us-east-2/elasticmapreduce/j-BB2W0CNKWL4W/node/data/';

### Hive Queries
- Year wise carrier delay from 2003-2010

       select sum(CarrierDelay),Year from delayed_flights where Year >=2003 AND Year<=2010 group by Year;
- Year wise NAS delay from 2003-2010

       select sum(NASDelay),Year from delayed_flights where Year >=2003 AND Year<=2010 group by Year;
- Year wise Weather delay from 2003-2010

       select sum(WeatherDelay),Year from delayed_flights where Year >=2003 AND Year<=2010 group by Year;
- Year wise late aircraft delay from 2003-2010

       select sum(LateAircraftDelay),Year from delayed_flights where Year >=2003 AND Year<=2010 group by Year;
- Year wise security delay from 2003-2010

       select sum(SecurityDelay),Year from delayed_flights where Year >=2003 AND Year<=2010 group by Year;
    

