# A simple, minimal Maven example: hello world

To create the files in this git repo we've already run `mvn archetype:generate` from http://maven.apache.org/guides/getting-started/maven-in-five-minutes.html

    mvn archetype:generate -DgroupId=com.mycompany.app -DartifactId=my-app -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false

Now, to print "Hello World!", type either...

    cd my-app
    mvn compile
    java -cp target/classes com.mycompany.app.App

or...

    cd my-app
    mvn package
    java -cp target/my-app-1.0-SNAPSHOT.jar com.mycompany.app.App

Running `mvn clean` will get us back to only the source Java and the `pom.xml`:

    $ mvn clean --quiet
    $ ack -a -f
    pom.xml
    src/main/java/com/mycompany/app/App.java
    src/test/java/com/mycompany/app/AppTest.java

Running `mvn compile` produces a class file:

    $ mvn compile --quiet
    $ ack -a -f
    pom.xml
    src/main/java/com/mycompany/app/App.java
    src/test/java/com/mycompany/app/AppTest.java
    target/classes/com/mycompany/app/App.class
    $ 
    $ java -cp target/classes com.mycompany.app.App
    Hello World!

Running `mvn package` does a compile and creates the target directory, including a jar:

    $ mvn clean --quiet
    $ mvn package > /dev/null
    $ ack -a -f
    pom.xml
    src/main/java/com/mycompany/app/App.java
    src/test/java/com/mycompany/app/AppTest.java
    target/classes/com/mycompany/app/App.class
    target/maven-archiver/pom.properties
    target/my-app-1.0-SNAPSHOT.jar
    target/surefire-reports/com.mycompany.app.AppTest.txt
    target/surefire-reports/TEST-com.mycompany.app.AppTest.xml
    target/test-classes/com/mycompany/app/AppTest.class
    $ 
    $ java -cp target/my-app-1.0-SNAPSHOT.jar com.mycompany.app.App
    Hello World!

Running `mvn clean compile exec:java` requires http://mojo.codehaus.org/exec-maven-plugin/

Running `java -jar target/my-app-1.0-SNAPSHOT.jar` requires http://maven.apache.org/plugins/maven-shade-plugin/
