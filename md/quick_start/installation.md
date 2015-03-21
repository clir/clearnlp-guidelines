# Installation

## Without Maven

* Create a directory called `clearnlp`.
* Download the following jar files and place them under the `clearnlp` directory:<br>[`clearnlp`](http://search.maven.org/remotecontent?filepath=edu/emory/clir/clearnlp/3.0.1/clearnlp-3.0.1.jar), [`args4j`](http://search.maven.org/remotecontent?filepath=args4j/args4j/2.0.29/args4j-2.0.29.jar), [`log4j`](http://search.maven.org/remotecontent?filepath=log4j/log4j/1.2.17/log4j-1.2.17.jar), [`hppc`](http://search.maven.org/remotecontent?filepath=com/carrotsearch/hppc/0.6.1/hppc-0.6.1.jar), [`xz`](http://search.maven.org/remotecontent?filepath=org/tukaani/xz/1.5/xz-1.5.jar).
* Add all the jar files to your Java classpath. If you are using the bash shell, it is something like the followings:
		
		CLEARNLP=some_path/clearnlp
		export CLASSPATH=$CLEARNLP/clearnlp-3.0.1.jar:\\
		                 $CLEARNLP/args4j-2.0.29.jar:\\
		                 $CLEARNLP/log4j-1.2.17.jar:\\
		                 $CLEARNLP/hppc-0.6.1.jar:\\
		                 $CLEARNLP/xz-1.5.jar:.
                 	
## With Maven

* ClearNLP can be retrieved from the [Maven Central](http://search.maven.org/#artifactdetails%7Cedu.emory.clir%7Cclearnlp%7C3.0.1%7Cjar). Add the following lines to your `pom.xml` with the group ID `edu.emory.clir`, the artifact ID `clearnlp`, and the current version number.

		<dependency>
		  	<groupId>edu.emory.clir</groupId>
		 	<artifactId>clearnlp</artifactId>
		  	<version>3.0.1</version>
		</dependency>

## Test

* Type the following command on a terminal.

		$ java edu.emory.clir.clearnlp.bin.Version
		
* If you see the information below, ClearNLP is successfully installed on your machine.

		ClearNLP Version 3.0.1
		Webpage: http://www.clearnlp.com
		Owner  : Jinho D. Choi
		Contact: support@clearnlp.com

* Download the [log4j configuration file](https://github.com/clir/clearnlp/blob/master/src/main/resources/configure/log4j.properties) and place it under the `clearnlp` directory.  This file is needed to print logs during training and decoding.
