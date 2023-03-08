### Integrating JFrog Artifactory with MAVEN 

### Configure Maven Client on MAC

1. Copy the following to your ~/.m2/settings.xml file for MacOS, or $USERPROFILE$\.m2\settings.xml for Windows

2. create setting.xml
<?xml version="1.0" encoding="UTF-8"?>
<settings xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.2.0 http://maven.apache.org/xsd/settings-1.2.0.xsd" xmlns="http://maven.apache.org/SETTINGS/1.2.0"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
  <servers>
    <server>
      <username>smelukote@gmail.com</username>
      <password>cmVmdGtuOjAxOjE3MDk4NTI3Mjk6dVFTeG1yQUVrMTZpM3c2MnluY1I4bXVLY1ZZ</password>
      <id>central</id>
    </server>
    <server>
      <username>smelukote@gmail.com</username>
      <password>cmVmdGtuOjAxOjE3MDk4NTI3Mjk6dVFTeG1yQUVrMTZpM3c2MnluY1I4bXVLY1ZZ</password>
      <id>snapshots</id>
    </server>
  </servers>
  <profiles>
    <profile>
      <repositories>
        <repository>
          <snapshots>
            <enabled>false</enabled>
          </snapshots>
          <id>central</id>
          <name>libs-release</name>
          <url>https://mysmd.jfrog.io/artifactory/libs-release</url>
        </repository>
        <repository>
          <snapshots />
          <id>snapshots</id>
          <name>libs-snapshot</name>
          <url>https://mysmd.jfrog.io/artifactory/libs-snapshot</url>
        </repository>
      </repositories>
      <pluginRepositories>
        <pluginRepository>
          <snapshots>
            <enabled>false</enabled>
          </snapshots>
          <id>central</id>
          <name>libs-release</name>
          <url>https://mysmd.jfrog.io/artifactory/libs-release</url>
        </pluginRepository>
        <pluginRepository>
          <snapshots />
          <id>snapshots</id>
          <name>libs-snapshot</name>
          <url>https://mysmd.jfrog.io/artifactory/libs-snapshot</url>
        </pluginRepository>
      </pluginRepositories>
      <id>artifactory</id>
    </profile>
  </profiles>
  <activeProfiles>
    <activeProfile>artifactory</activeProfile>
  </activeProfiles>
</settings>
## Run the followng command to create a sample maven projcet
## install dependencies

3. mvn archetype:generate -DgroupId=com.mycompany.app -DartifactId=my-app -DarchetypeArtifactId=maven-archetype-quickstart -DarchetypeVersion=1.4 -DinteractiveMode=false
cd my-app
## Install maven
mvn install
#### Copy the following code snippet to the <project> block of your pom.xml file, with your target local repository URL:
<distributionManagement>
    <snapshotRepository>
        <id>snapshots</id>
        <name>a0wxgfunblktk-artifactory-primary-0-snapshots</name>
        <url>https://mysmd.jfrog.io/artifactory/libs-snapshot</url>
    </snapshotRepository>
</distributionManagement>

### Run the following command to deploy your Maven package to Artifactory:
mvn deploy
