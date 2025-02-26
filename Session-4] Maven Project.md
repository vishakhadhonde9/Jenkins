# Structure of Project -
# Project 1: maven-build - 
# On Jenkins -

      mkdir mavenapp 
      cd mavenapp
      mkdir -p src/main/com/fortune/myapp  src/test/com/fortune/myapp 
      sudo apt install tree

- Copy the code of pom.xml, App.java and AppTest.java from below github link and make changes as per your requirements 

      https://github.com/jenkins-docs/simple-java-maven-app/blob/master/pom.xml 


# pom.xml -
- vi src/pom.xml 

 

      <project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
      
        xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd"> 
      
        <modelVersion>4.0.0</modelVersion> 
      
        <groupId>com.fortune.myapp</groupId> 
      
        <artifactId>myapp</artifactId> 
      
        <packaging>jar</packaging> 
      
        <version>1.0-SNAPSHOT</version> 
      
        <name>myapp</name> 
      
        <url>https://maven.apache.org</url> 
      
        <dependencies> 
      
          <dependency> 
      
            <groupId>org.junit.jupiter</groupId> 
      
            <artifactId>junit-jupiter-api</artifactId> 
      
            <version>5.11.4</version> 
      
            <scope>test</scope> 
      
          </dependency> 
      
        </dependencies> 
      
        <properties> 
      
          <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding> 
      
        </properties> 
      
        <build> 
      
          <pluginManagement> 
      
            <plugins> 
      
              <plugin> 
      
                <groupId>org.apache.maven.plugins</groupId> 
      
                <artifactId>maven-compiler-plugin</artifactId> 
      
                <version>3.13.0</version> 
      
                <configuration> 
      
                  <release>17</release> 
      
                </configuration> 
      
              </plugin> 
      
            </plugins> 
      
          </pluginManagement> 
      
          <plugins> 
      
            <plugin> 
      
              <!-- Build an executable JAR --> 
      
              <groupId>org.apache.maven.plugins</groupId> 
      
              <artifactId>maven-jar-plugin</artifactId> 
      
              <version>3.4.2</version> 
      
              <configuration> 
      
                <archive> 
      
                  <manifest> 
      
                    <addClasspath>true</addClasspath> 
      
                    <classpathPrefix>lib/</classpathPrefix> 
      
                    <mainClass>com.fortune.myapp.App</mainClass> 
      
                  </manifest> 
      
                </archive> 
      
              </configuration> 
      
            </plugin> 
      
            <plugin> 
      
              <groupId>org.apache.maven.plugins</groupId> 
      
              <artifactId>maven-enforcer-plugin</artifactId> 
      
              <version>3.5.0</version> 
      
              <executions> 
      
                <execution> 
      
                  <id>enforce-maven</id> 
      
                  <goals> 
      
                    <goal>enforce</goal> 
      
                  </goals> 
      
                  <configuration> 
      
                    <rules> 
      
                      <requireMavenVersion> 
      
                        <version>[3.9.2,)</version> 
      
                      </requireMavenVersion> 
      
                      <requireJavaVersion> 
      
                        <version>[17,)</version> 
      
                      </requireJavaVersion> 
      
                    </rules> 
      
                  </configuration> 
      
                </execution> 
      
              </executions> 
      
            </plugin> 
      
          </plugins> 
      
       </build> 
      
      </project> 
      
       
      
# App.java -
- vi src/main/com/fortune/myapp/App.java 
      
        

        package com.fortune.myapp; 
        
        
        /** 
        
         * Hello world! 
        
         */ 
        
        public class App { 
        
         
        
            private static final String MESSAGE = "Hello World!"; 
        
         
        
            public App() {} 
        
         
        
            public static void main(String[] args) { 
        
                System.out.println(MESSAGE); 
        
            } 
        
         
        
            public String getMessage() { 
        
                return MESSAGE; 
        
            } 
        
        } 
        

  # AppTest.java 
- vi src/test/com/fortune/myapp/AppTest.java 
        
         
        
         
        
        package com.fortune.myapp; 
        
         
        
        import org.junit.jupiter.api.Test; 
        
         
        
        import static org.junit.jupiter.api.Assertions.assertEquals; 
        
         
        
        /** 
        
         * Unit test for simple App. 
        
         */ 
        
        public class AppTest 
        
        { 
        
            @Test 
        
            public void testAppConstructor() { 
        
                App app1 = new App(); 
        
                App app2 = new App(); 
        
                assertEquals(app1.getMessage(), app2.getMessage()); 
        
            } 
        
         
        
            @Test 
        
            public void testAppMessage() 
        
            { 
        
                App app = new App(); 
        
                assertEquals("Hello World!", app.getMessage()); 
        
            } 
        
        } 

 

- Open the App.java file and make changes in 1st line (mycompany ->  fortune and app -> myapp) 
- Open the AppTest.java file and make the same changes as we did in App.java in 1st line (mycompany ->  fortune and app -> myapp) 

# On Github -
- Create a new repository on Github 
- Set webhook to trigger Jenkins 

# On Jenkin -
- In mavenapp/ dir 

      git init 
      git config - -global user.name “usernamei” 
      git config - -global user.email “email-id” 
      git remote add origin git-repo-link 


# Jenkin Server (8080) -
- Do setup for Maven and JDK tool which is installed already while configuring Jenkins 1st time. 


- Dashboard --> Manage Jenkins --> Tools --> JDK installations amd  Add JDK --> Enter Name --> install
- Create new item.
- Add Description.
- Select Source Code Management as git and add git repo link.
- Select trigger as "GitHub hook trigger for GITScm polling"
- Select Build Step as "Invoke top-level Maven targets"and goal as "clean package"
- Save.

# On Jenkin -
- Now push the code files to github repo 


      git add . 
      git commit –m “maven commit” 
      git push origin master 


- Check the workspace you will get .jar file there. 

# Project 2: maven-test 
## On Jenkin Server(8080) -
- Create new item.
- Add Description.
- Select Source Code Management as git and add git repo link.
- Select trigger as "Build after other projects are build" ---> add watch as "project1_name".
- Select Build Step as "Invoke top-level Maven targets"and goal as "test"
- Save.


 

 

 
 

 
