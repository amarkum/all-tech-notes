
# Maven, Git, and GitLab Commands Guide

This guide covers essential commands for managing projects with Maven, Git, and GitLab CI/CD.

---

## Maven Commands

1. **Change Project Version**  
   Sets a new project version in Maven.
   ```bash
   mvn versions:set -DnewVersion=01234-SNAPSHOT
   ```

2. **Clean Install (Skipping Tests)**  
   Cleans and installs the project without running tests, skipping unnecessary build checks.
   ```bash
   mvn clean install -DskipTests -Dmaven.javadoc.skip=true -Dfindbugs.skip=true -Dmaven.clover.skip=true -DskipITs
   ```

3. **Deploy Docker Image**  
   Packages and deploys a Docker image, including stopping and starting Docker services, and following logs.
   ```bash
   mvn clean package -Dfindbugs.skip=true docker:stop docker:build docker:start docker:logs -Ddocker.follow -Ddocker.logDate=DEFAULT -Dmaven.test.skip=true
   ```

4. **Assembly Plugin Configuration**  
   The `maven-assembly-plugin` is configured here for packaging applications with dependencies.

   ```xml
   <plugin>
       <artifactId>maven-assembly-plugin</artifactId>
       <configuration>
           <archive>
               <manifest>
                   <!-- <mainClass></mainClass> -->
               </manifest>
           </archive>
           <descriptorRefs>
               <descriptorRef>jar-with-dependencies</descriptorRef>
           </descriptorRefs>
       </configuration>
       <executions>
           <execution>
               <id>make-assembly</id>
               <phase>package</phase>
               <goals>
                   <goal>single</goal>
               </goals>
           </execution>
       </executions>
   </plugin>
   ```

5. **Compiler Plugin Configuration**  
   Sets the Java source and target version in Maven.
   ```xml
   <plugin>
       <groupId>org.apache.maven.plugins</groupId>
       <artifactId>maven-compiler-plugin</artifactId>
       <configuration>
           <source>8</source>
           <target>8</target>
       </configuration>
   </plugin>
   ```

---

## Git Commands

1. **Show All Git Configuration**
   ```bash
   git config --list --show-origin
   ```

2. **Un-stage a Commit**
   ```bash
   git restore --staged <file>
   ```

3. **Configuration Files**  
   - Local config file: `.git/config`
   - Global config file: `~/.gitconfig`

4. **Change Git User Information**
   - **User Name**  
     ```bash
     git config --global user.name "Amar Kumar"
     ```
   - **User Email**  
     ```bash
     git config --global user.email amar@gmail.com
     ```

5. **Change Default Editor**
   ```bash
   git config --global core.editor atom
   ```

6. **Remote Connection Setup**
   ```bash
   git init
   git add README.md
   git commit -m "first commit"
   git remote add origin https://github.com/amarkum/repss.git
   git push -u origin master
   ```

7. **Sample .gitignore for SBT Projects**  
   Recommended `.gitignore` for Scala-based SBT projects, IntelliJ, and Eclipse files.

   ```
   # sbt
   bin/
   project/
   target/
   build/

   # eclipse
   build
   .classpath
   .project
   .settings
   .worksheet

   # intellij idea
   *.log
   *.iml
   *.ipr
   *.iws
   .idea

   # macOS
   .DS_Store

   # other
   .history
   .scala_dependencies
   .cache
   .cache-main

   # general
   *.class
   ```

---

## GitLab CI/CD Configuration

GitLab CI/CD pipelines are organized into stages and jobs.

- **Defining Stages**
  ```yaml
  stages:
    - run
    - build
    - test
  ```

- **Example Jobs with Stages**  
  Each job is associated with a specific stage.

  ```yaml
  job-one:
    image: docker:latest
    stage: run

  job-two:
    image: docker:latest
    stage: run
  ```

---

This guide provides a structured approach to using Maven, Git, and GitLab CI/CD for managing software development workflows efficiently.
