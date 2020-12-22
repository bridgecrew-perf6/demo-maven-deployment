# Publish artifacts into a nexus artifactory
## Preparation
- Configure a distribution management into the project pom.xml:
  ```
    <distributionManagement>
      <snapshotRepository>
        <id>jmens-snapshots</id>
        <url>https://maven.jmens.de/repository/maven-snapshots/</url>
      </snapshotRepository>
      <repository>
        <id>jmens-releases</id>
        <url>https://maven.jmens.de/repository/maven-releases/</url>
      </repository>
    </distributionManagement>
  ```
- Configure credentials in your maven settings file.
 
  Credentials in the settings and configured server within your pom.xml 
  are kept together via the server id - `jmens-snapshots` and `jmens-releases` 
  in this example.
  ```
  <servers>
     <server>
        <id>jmens-snapshots</id>
        <username>username</username>
        <password>top_secret</password>
     </server>
     <server>
        <id>jmens-releases</id>
        <username>username</username>
        <password>top_secret</password>
     </server>
  </servers>
  ```
## Execution
- Set a new version if needed: 
  
  `mvn versions:set -DnewVersion=1.0.0-SNAPSHOT`
- Publish: 
  
  `mvn deploy`