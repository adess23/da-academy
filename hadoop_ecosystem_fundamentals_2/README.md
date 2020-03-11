# Hadoop Ecosystem: Fundamentals - Spark

<p align="center"> 
<img src="../assets/spark.png"> 
</p>

### Motivation ###
Apache Spark is an open-source distributed general-purpose cluster-computing framework. Spark was developed in 2012 in response to limitations in the MapReduce cluster computing paradigm, which forces a particular linear dataflow structure on distributed programs. Spark had in excess of 1000 contributors in 2015, making it one of the most active projects in the Apache Software Foundation and one of the most active open source big data projects.
Right now, Apache Spark is used in the majority of our Data projects so it's crucial for our Data Architects to be proficient with it.

### What you will learn ###

You will learn the main concepts, architecture and basics. Besides, you will be able to run your fist Spark program.

### Courses: ###

**Mandatory:**

1. [Spark on udacity](https://www.udacity.com/course/learn-spark-at-udacity--ud2002) (10h)

**Extra:**

2. [Spark Basics](https://www.udemy.com/spark-basics/) (8h)

3. [Spark Starter Kit](https://www.udemy.com/sparkstarterkit/) (3.5h)

**Reading:**

4. [Apache Spark Tutorial](https://www.datacamp.com/community/tutorials/apache-spark-python)

### Practice: ###

#### Before you begin ####
(It is assumed that Git is already installed and working).

#### Exercices ####

**Server Log Analysis with Spark**

Files: [weblog.csv](../exercices/weblog.csv)

This lab will demonstrate how you can perform web server log analysis with Apache Spark.
Log data comes from many sources, such as web server and server commands.

The log files that we use for this assignment are in the Apache Common Log Format (CLF). 
Each part of this log entry is described below.

*IP*: This is the IP address (or host name, if available) of the client (remote host) which made the request to the server. 

*Time*: The time that the server finished processing the request. The format is: *day/month/year:hour:minute:second*

*URL*: This is the first line of the request string from the client. It consists of three components: the **request method** (e.g., GET, POST, etc.), **the endpoint** (a Uniform Resource Identifier), and the **client protocol version**.

*Status*: This is the status code that the server sends back to the client. 

*Notes:
IP: may contain information that is not necessarily an IP value, remember, it is a log with many sources.
Time: Keep in mind that you must clean the value to be considered date type, remember, it is a log with many sources.*

**How to complete this lab.**

1. Exploratory Data Analysis

2. Analysis Walk-Through on the Log File
    1. **HTTP Status Analysis**: Create a PySpark script that allows to know which status values appear in the data and how many times. 
    2. **Frequent Hosts**: Create a PySpark script that looks hosts that have accessed the server frequently (e.g., more than ten times). 
    3. **Frequent Commands**: Create a PySpark script that allows to find commands executed
    4. **Top Paths**: Create a PySpark script that allows you to find  the top paths (URIs) in the log with code 200. 
    Sample:
     ('/details.php', 100),
     ('/contestproblem.php', 98),
     ('/css/normalize.css', 85),
     (' /js/vendor/modernizr-2.8.3.min.js', 75)

3. Analyzing Web Server Log File
    1. **Top Ten Error Paths**: Create a PySpark script that allows you to know the top ten paths which did not have return code 200. Create a sorted list containing the paths and the number of times that they were accessed with a non-200 return code and show the top ten.
    2. **Number of Unique Hosts**: Create a PySpark script that allows you to know unique hosts are there in the entire log.
    3. **Number of Unique Daily Hosts**: Create a PySpark script that allows you to know the number of unique hosts in the entire log on a day-by-day. 
    4. **Exploring Status Codes**: 
        1. Create a PySpark script that allows you: 
            1. Counting 304 Response Codes
            2. Listing the Top Five 304 Response Code paths
            3. Listing the Top tene 302 Response Code Hosts
            4. Listing 206 / 404 Errors per Day
        2. Create a PySpark script that allows you:
            1. Hourly 206 Errors
            2. Hourly 304 Errors

Note: for 3.iii, create a DataFrame with following columns:

| Column        | Explanation           |
| ------------- |:-------------:        |
| host          | the host ip           |
| month         | month                 |
| day           | the day of the month  |

**Challenge!**:

- What do people think about Sandra Bullock's *"Bird Box"*? Make a sentiment analysis using Twitter information. [Help](https://medium.com/@anicolaspp/spark-streaming-and-twitter-sentiment-analysis-c860938d484).

### Commit: ###

Commit your practice code.

<img src="../assets/stop.png" title="Stop Logo" width="150" height="150">

### Auto assessment: ###

*1. What is a DAG?*

*2. What is an RDD?*

*3. Which are the benefits of Spark over MapReduce?*

*4. Do you need to install Spark on all nodes of YARN cluster?*

*5. What is the different of using `yarn-cluster` mode vs using `local` ?*

*6. What is the different of using `yarn-cluster` mode vs `yarn-client` mode ?*

*7. How do we create an RDD in Apache Spark ?*

*8. What is the difference between RDDs, Dataframes and Datasets ?*

*9. What types of operations do we use in the RDDs ?*

*10. What is a partition?*

*11. What is the Spark Driver? Which is the difference with the Spark Executor?*

*12. What are broadcast variables? And accumulators?*

*13. What is a DStream?*

*14. What is the significance of Sliding Window Operations?*

*15. Why would you use caching in Apache Spark?*

*16. What do you understand by eager evaluation? And lazy? Which is used by Apache Spark?*

*17. Which part of the following code will be executed on the master? Which will run on each worker node?*
```
val formatter: DateTimeFormatter = DateTimeFormatter.ofPattern("yyyy/MM")

def getEventCountOnWeekdaysPerMonth(data: RDD[(LocalDateTime, Long)]): Array[(String, Long)] = {

 val result = data
   .filter(e => e._1.getDayOfWeek.getValue < DayOfWeek.SATURDAY.getValue)
   .map(mapDateTime2Date)
   .reduceByKey(_ + _)
   .collect()

 result
   .map(e => (e._1.format(formatter), e._2))
}

private def mapDateTime2Date(v: (LocalDateTime, Long)): (LocalDate, Long) = {
 (v._1.toLocalDate.withDayOfMonth(1), v._2)
}
```

---

## Additional resources

- Hadoop - The Definitive Guide - O’Reilly

- Spark - The Definitive Guide - O’Reill

---

<img src="../assets/get_badge.png"> 

### *Sync to obtain your badge!*
 
Remember to sync with an Academy tutor to obtain your badge before continuing to the next module. This will also let you be sure you have acquired every needed concept. Complete the [Ending Module form](https://forms.gle/ukvWjKtoFYx4Kn8q7) and a tutor will ping you to schedule the evaluation date. If not being noticed after 7 days, feel free to remind any of the tutors about it.