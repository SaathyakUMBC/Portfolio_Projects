Project Name: Using Big Data Techniques for Analysis & Prediction of Flight Delay & Cancellation

Table of contents: 
	Introduction
	Software Requirements
	Reccomended Hardware
	Installation
	Configuration
	Execution
	FAQ

Introduction: 
	This project aims to use massive amount of data of the order  7Gb in magnitude and over 60 million rows of flight_data.
	For generation of insights and a prediction model using Machine learning algorithms.
	This "readme.txt" file aims to help the users with the required installations, configuring the environment and setup required to run the code.


Software Requirements:
	Python version 3.10
	Jupyter notebook version 5+
	MongoDB Version 6+
	PySpark version 3.3.1
	Windows version 10/11


Reccomended Hardware Specifications:
	32Gb or higher RAM - 3000Mhz or Higher frequency reccomended.
	128GB SSD or higher.


Installation:
	Python installation:
		1. From www.python.org, select the version of python 3.10, select windows 64 bits.
		2. Run the installer, tick both check boxes (installation, adding path).
		3. click "install now".
		4. Once installation is complete, close the installer.
		5. To verify the installation process, open CMD and run the command "python". This will display the current version of python.
		6. Next, to check if pip is installed, run "pip –V".
		7. Installation and setup of Python is complete. 
	
	Jupyter Installation:
		1. in CMD, run the command, "pip install notebook" for installing Jupyter.
		2. To run the notebook use "jupyter notebook".
	
	MongoDB Installation:
		1. Open "https://www.mongodb.com/try/download/community" on the browser.
		2. Select version 6, OS: WindowsOS, Package: msi and download the files.
		3. Accept end user agreement and click next.
		4. Click "complete" for setup.
		5. Next, click “Run service as Network Service user” and add path to data directory.
		6. Then click "install" button
		7. After installation finishes, click finish.
		8. Open the location of the MongoDBbin folder in the local storage.
		9. Copy the bin path, and open the system environment variables and add the new path to list of environment variables.
		10. Open CMD and run "mongod". This will run MongoDB server.

		
	PySpark Installation:
		1. Open "https://spark.apache.org/downloads.html" with the browser.
		2. Choose a Spark release: 3.3.1 (Oct 25 2022)
		   Choose a package type: Pre-built for Apache Hadoop 3.3 and later
		   Download Spark: spark-3.3.1-bin-hadoop3.tgz
		3. extract the binary using 7zip and copy the underlying folder spark-3.0.0-bin-hadoop2.7 to c:\apps
		4. Now set the following environment variables.
		   SPARK_HOME  = C:\apps\spark-3.0.0-bin-hadoop2.7
		   HADOOP_HOME = C:\apps\spark-3.0.0-bin-hadoop2.7
           PATH=%PATH%;C:\apps\spark-3.0.0-bin-hadoop2.7\bin
		5. Download winutils.exe file from winutils, copy it to %SPARK_HOME%\bin folder.
		6. Open the command prompt and type pyspark command to run the PySpark shell. 
		
Configuration:
		Setting-1 :
		Add the following configuration to the PySpark sesssion:
		spark.driver.memory 15gb 
		org.mongodb.spark:mongo-spark-connector:10.0.5
		(This ensures that the PySpark session always has 15gb of memeory to work with and prevents the occurance of memory allocation errors)

Execution:

	Fetching data : 
		The data is downloaded from the source -> https://www.kaggle.com/datasets/yuanyuwendymu/airline-delay-and-cancellation-data-2009-2018 
		The total size of the data is : 7GB.
		The total number of CSV files are: 10 Files.
	
	Loading the data to MongoDB:
		Connect the local database to MongoDB Compass. (for UI) 
		Create flight_db database and flight_data collections.
		Use the "ADD DATA" option to select and import the CSV files from the local storage.
		The Data is now visible in MongoDB.
		
	Reading the data:
		The data is read in PySpark from MongoDB using the "mongo-spark" connector.
		Name of the project notebook file is "Polisetty_Akam_Kasuganti.ipynb" run using Jupyter notebook 
		
	Running the primary code:
	Run the notebook using the Jupyter tool - this project has been designed and configured to be run using Jupyter in Python enviroment. 
		Phase-1 : This step does the cleaning of data. 
		Phase-2 : This step does the EDA, Aggregations, Functions, Sorting.	
		Phase-3 : Generating the machine learning code:
				  This step modifies the data for suitable types and formats to be  used as input for the ML models.
				  The cleaned data fields are taken as input for 2 machine learning models.
				  The predicted values are generated using the input data.
		Phase-4 : Generating the visualisations:
				 This step uses various functions and tools to generate the insights.
				 The generated insights are displayed as visualisations using various libraries.
		
		
FAQ: 
	1. What if the PySpark script crashes during run-time ?
	This can be a cause due to the magnitude of the data loaded, PySpark uses the RAM of the machine for execution. 
	Loading the data from MongoDB and processing huge amounts of data using the RAM, causes a memory error "ERROR: OUT OF MEMORY".
	Consider using only a part of the database from MongoDB or using a machine with increased RAM capacity and frequency.

	2. What if you are encountering a memeory allocation error using PySpark ?
	This issue is fixed using the configuratiion presented  above, that ensures that PySpark always has access to a minumum amount of memory.
	
Additional Resources:
https://sparkbyexamples.com/
https://www.tutorialspoint.com/how-to-install-python-in-windows

Project Collborators:
Saathyak Rao Kasuganti, Graduate Student MPS Data Science UMBC.
Manideep Akam, Graduate Student MPS Data Science UMBC.
Chanakya Polisetty, Graduate Student MPS Data Science UMBC.





