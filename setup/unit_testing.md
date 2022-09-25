Unit Testing is a one of the testing done to make sure individual unit or component functionalities are working fine. It helps to find bugs early, reduce cost of charge, improves the quality of code. The mvn --test commad can be used to  test the file. It fails the build if one of the test cases fails.

JaCoCo is an actively developed line coverage tool that i used to meaure how many llines of code are tested


Running unit test cases using Jenkins.
JUnit tests using mvn test

NoW THE Test might run successfully however we do not know the number of lines that have been tested and thus jacoco comes in handy

We need to add the jacoco plugin to the pom.xml file
