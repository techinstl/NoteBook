## How to create Spark project from scratch in Intelij
### Prepare for project
- Open Intelij
- Auto import class settings
The IDEA is working a bit differently, the “unambiguous imports” are imported on the fly, and you need to enable this feature manually.
**File –>> Settings –>> Editor –>> General –>> Auto Import –>> Checked these options :
Add unambiguous imports on the fly
Optimize imports on the fly**
- Install scala plugin
- Create a normal maven project
   at default, the project will use java source codes, and need to change it to scala.
- Right click project, select **Add Framework Support**, choose scala, and then click OK.
- Change java folder into scala. then you should be able to add scala class
- Add Spark repositories. 
  See link https://mvnrepository.com/artifact/org.apache.spark. 
  In this example, choose below dependecies.
      <dependencies>
        <!-- https://mvnrepository.com/artifact/org.apache.spark/spark-core -->
        <dependency>
            <groupId>org.apache.spark</groupId>
            <artifactId>spark-core_2.11</artifactId>
            <version>2.3.3</version>
        </dependency>

        <!-- https://mvnrepository.com/artifact/org.apache.spark/spark-sql -->
        <dependency>
            <groupId>org.apache.spark</groupId>
            <artifactId>spark-sql_2.11</artifactId>
            <version>2.3.3</version>
        </dependency>

        <!-- https://mvnrepository.com/artifact/org.apache.spark/spark-streaming -->
        <dependency>
            <groupId>org.apache.spark</groupId>
            <artifactId>spark-streaming_2.11</artifactId>
            <version>2.3.3</version>
            <scope>provided</scope>
        </dependency>

        <!-- https://mvnrepository.com/artifact/org.apache.spark/spark-hive -->
        <dependency>
            <groupId>org.apache.spark</groupId>
            <artifactId>spark-hive_2.11</artifactId>
            <version>2.3.3</version>
            <scope>provided</scope>
        </dependency>

    </dependencies>
	
### Code Examples

    package com.fang.spark.examples
    
    import org.apache.spark.sql.SparkSession
    
    object SparkSessionUse {
    
      def main(args: Array[String]): Unit = {
        val spark = SparkSession.builder().appName("SparkSessionUse").master("local[*]").getOrCreate()
    
        spark.range(100).withColumnRenamed("id", "num").show()
      }
    }

### Exceptions and Solutions
**Problem:**

Exception in thread "main" java.lang.IllegalArgumentException: System memory 259522560 must be at least 471859200. Please increase heap size using the --driver-memory option or spark.driver.memory in Spark configuration.

**Solution:**

Add -Xmx512m in VM options.




