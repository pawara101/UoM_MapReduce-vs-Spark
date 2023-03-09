## Spark Commands
- load data
`val df = spark.read.format("csv").option("header", "true").load("s3://aws-logs-261294063287-us-east-2/DelayedFlights-updated.csv")`

`df.createOrReplaceTempView("DelayedFlights")`

- Year wise carrier delay from 2003-2010
`spark.time(spark.sql("SELECT Year, SUM(CarrierDelay) as total_delay FROM DelayedFlights WHERE Year >= 2003 AND Year <= 2010 AND CarrierDelay IS NOT NULL GROUP BY Year ORDER BY Year").show())`

- Year wise NAS delay from 2003-2010
`spark.time(spark.sql("SELECT Year, SUM(NASDelay) as total_delay FROM DelayedFlights WHERE Year >= 2003 AND Year <= 2010 AND CarrierDelay IS NOT NULL GROUP BY Year ORDER BY Year").show())`

- Year wise Weather delay from 2003-2010
`spark.time(spark.sql("SELECT Year, SUM(WeatherDelay) as total_delay FROM DelayedFlights WHERE Year >= 2003 AND Year <= 2010 AND CarrierDelay IS NOT NULL GROUP BY Year ORDER BY Year").show())`

- Year wise late aircraft delay from 2003-2010
`spark.time(spark.sql("SELECT Year, SUM(LateAircraftDelay) as total_delay FROM DelayedFlights WHERE Year >= 2003 AND Year <= 2010 AND CarrierDelay IS NOT NULL GROUP BY Year ORDER BY Year").show())`

- Year wise security delay from 2003-2010
`spark.time(spark.sql("SELECT Year, SUM(SecurityDelay) as total_delay FROM DelayedFlights WHERE Year >= 2003 AND Year <= 2010 AND CarrierDelay IS NOT NULL GROUP BY Year ORDER BY Year").show())`
