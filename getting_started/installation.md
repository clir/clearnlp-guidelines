# ClearNLP Installation
##How to install
#### Without Maven
1. Create a directory called 'clearnlp'
2. Download the [ClearNLP library](http://clearnlp.wikispaces.com/file/detail/clearnlp-lib-2.0.2.tgz) and uncompress it. Place all jar files under the clearnlp directory
3. Add all jar files in the clearnlp directory to your Java classpath. If you are using the bash shell, it is something like the followings:
		
		export CLEARNLP=some_path/clearnlp
		export CLASSPATH=$CLEARNLP/args4j-2.0.23.jar:\\
                 $CLEARNLP/guava-14.0.1.jar:\\
                 $CLEARNLP/hppc-0.5.2.jar:\\
                 $CLEARNLP/jregex1.2_01.jar:\\
                 $CLEARNLP/log4j-1.2.17.jar:\\
                 $CLEARNLP/clearnlp-2.0.2.jar:.
4. Create the log4j configuration file named `log4j.properties` with the following lines under the ClearNLP directory
		
		# Set root logger level to DEBUG and its only appender to A1.
		log4j.rootLogger=DEBUG, A1

		# A1 is set to be a ConsoleAppender.
		log4j.appender.A1=org.apache.log4j.ConsoleAppender

		# A1 uses PatternLayout.
		log4j.appender.A1.layout=org.apache.log4j.PatternLayout
		log4j.appender.A1.layout.conversionPattern=%m

5. Type the following command on a terminal

		$ java com.clearnlp.run.Version
		
6. If you see the information below, ClearNLP is successfully installed on your machine

		ClearNLP version x.x.x
		Webpage: clearnlp.com
		Owner  : Jinho D. Choi
		Contact: support@clearnlp.com
		
#### With Maven
* ClearNLP can be retrieved from the [Maven Central](http://search.maven.org/#artifactdetails%7Ccom.clearnlp%7Cclearnlp%7C2.0.2%7Cjar). Add the following lines to your 'pom.xml' with the group ID 'com.clearnlp', the artifact ID 'clearnlp', and the current version number.

		<dependencies>
		...
			<dependency>
	    		<groupId>com.clearnlp</groupId>
    			<artifactId>clearnlp</artifactId>
    			<version>2.0.2</version>
  			</dependency>
		...
		</dependencies>
		
* Create the log4j configuration file named `log4j.properties` with the following lines under the ClearNLP directory
		
		# Set root logger level to DEBUG and its only appender to A1.
		log4j.rootLogger=DEBUG, A1

		# A1 is set to be a ConsoleAppender.
		log4j.appender.A1=org.apache.log4j.ConsoleAppender

		# A1 uses PatternLayout.
		log4j.appender.A1.layout=org.apache.log4j.PatternLayout
		log4j.appender.A1.layout.conversionPattern=%m
