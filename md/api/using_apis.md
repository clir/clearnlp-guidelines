# Using APIs with Maven and Eclipse
* Install maven: ([guidelines](http://maven.apache.org/download.cgi)).
* Create a maven project using the following command (use your own `VERSION`, `GROUP_ID`, and `ARTIFACT_ID`).
		
		VERSION=3.0
		GROUP_ID=edu.emory.clir
		ARTIFACT_ID=clearnlp-demo
		mvn archetype:generate -DarchetypeGroupId=org.apache.maven.archetypes -DgroupId=$GROUP_ID -DartifactId=$ARTIFACT_ID -Dversion=$VERSION-SNAPSHOT
		
* Add the following dependency to your `pom.xml` (here, we use the snapshot version).

		<dependency>
		  <groupId>edu.emory.clir</groupId>
		  <artifactId>clearnlp</artifactId>
		  <version>3.0.0-SNAPSHOT</version>
		</dependency>
		
* Goto the `clearnlp-demo` directory and enter the following command.

		mvn eclipse:eclipse
		
* Create a Java project using the `clearnlp-demo` directory.