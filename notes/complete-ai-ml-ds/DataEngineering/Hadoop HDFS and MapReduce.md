Hadoop
- Databases like MySQL can become "too full"
- Hadoop could handle "big data"

Essentially a "data lake"
- Two key drivers
	- HDFS (Hadoop distributed file system)
		- Store multiple files on multiple computers
		- Data stored across different computers
	- MapReduce
		- Allows us to perform jobs over
			- All files and
			- All computers
		- Less used now
			- Replaced by Apache Spark

Additional tools around Hadoop
- Hive
	- Allows one to run SQL against a Hadoop data collection

Used primarily by data engineers
- Not for reads / writes from many users
- But typically used by data engineers

Targets **huge** amounts of data
