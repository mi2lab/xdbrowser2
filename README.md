XDBrowser 2.0
=============

Please read the wiki section for source control guidelines and code maintenance!!

This document is intended to provide an overview of the svn directory strutcure of the Kinect Analysis project
and to give instructions on how to setup and run Kinect Analysis. 


The following directories and files are located in the root directory:

 - Client:
		- index.html is main application page and web-socket.js file implements client
		- settings.html and settings.js implement the Kinect Analysis Settings page
		- the css subdirectory contains stylesheets: style.css contains the css styles for the main application page.
		- various subdirectories for libraries (bootstrap extensions etc.) or configurations that are not loaded through a CDN

 
 - KinectAnalysis: 
		- Kinect Analysis server component

 
 - audioRecordings: Directory for storing audio recordings (WAV files). This directory needs to exist for the server
					to store WAV files and for the client to replay them in the browser.
 
 - logFiles: Directory for storing log files. To successfully parse and visualize a log file, it has to be located in this directory.
 
 - dump.sql: File containing MySQL database schema without any table data. Run dump.sql after MySql installation
			 to setup the Kinect Analysis database. The file contains everything that is required. 
			 The Kinect Analysis server assumes by default the following database configuration:	
			 
			 server=localhost;
			 user=root;
			 database=kinectrecordings;
			 port=3306;
			 password=kinect;
			 
			If any of this changes, it has to be modified in the App.config settings of Kinect Analysis.
			
			MySQL configuration:
 
			It is important to set the buffer pool size of InnoDB to at least 1 GB 
			on a machine with 4 GB RAM. The buffer pool size is the only parameter that must be adjusted. The default
			MySQL settings can be used otherwise.
			 		 
			--> Set "innodb_buffer_pool_size = 1G" in C:\ProgramData\MySQL\MySQL Server 5.6\my.ini or similar.
			 
				
 - documentation: Contains the thesis and different documents. 
 
 - PostProcessor: Contains the program that was used to create skeleton tracking statistics based on the Kinect Browser data stored in 
				  a MySQL database.
 
 - other: 
		- Audio Converter: Small C# program to convert WAV files to MP3 using lame.exe. 
		
		- video recording: Contains ffmpeg and scripts to create a video sequence from a bunch of ordered JPEG images. 
 
 
 
 
 HOW TO SETUP KINECT ANALYSIS:
 =============================
 
 
 1. Install Visual Studio and Kinect SDK
 
 2. Install MySQL Community Server
 
 3. Change MySQL settings as explained above (--> increase innodb_buffer_pool_size to at least 1GB)
 
 4. Check out the svn directory with the abovementioned directory structure on the machine where you want to run Kinect Analysis
 
 5. Run dump.sql (e.g. in MySQL Workbench) to create Kinect Analysis database with corresponding tables
 
 6. Compile and start Kinect Analysis server
 
 7. Start Kinect Analysis client by opening index.html in Chrome
 
 
 

 David Ott, December 2013
 <ott.david [at] outlook.com>
