# Lutece site Pom

## Usage

This POM is used as parent POM to generate  a Lutece site. 

A Luece site contains at least the following information:

*    The declaration of THIS parent POM lutece-site-pom in its latest version
*    The site metadata (version, name, groupId, artifactId…)
*    Maven repository statements for Lutece project :  contains stable versions of Lutece components and of several third-party libraries
*    The declaration as dependencies of the plugins that make up the site

## Recommendations

For the creation of a stable version of a site, it will be necessary to ensure that all the dependencies, including the transitive dependencies, 
are also fixed to a stable version in order to guarantee that the site brings back the same versions of components at each redeployment. 
For this, the explicit versions must be used in square brackets in the dependencies. 

The parent lutece-site-pom POM defines a certain number of default Maven profiles.

For more informations about generating a lute site, see [https://lutece.paris.fr/support/jsp/site/Portal.jsp?page=wiki]


Example of use of this parent POM in a lutece site POM :

```

<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/maven-v4_0_0.xsd">

    <parent>
        <artifactId>lutece-site-pom</artifactId>
        <groupId>fr.paris.lutece.tools</groupId>
        <version>7.0.5</version>
    </parent>

    <modelVersion>4.0.0</modelVersion>
    <groupId>fr.paris.lutece</groupId>
    <artifactId>my-lutece-site</artifactId>
    <packaging>lutece-site</packaging>
    <name>Site My Site</name>
    <version>1.0.0-SNAPSHOT</version>

    <repositories>
        <repository>
            <snapshots>
                <enabled>false</enabled>
            </snapshots>
            <id>lutece</id>
            <name>luteceRepository</name>
            <url>http://dev.lutece.paris.fr/maven_repository</url>
        </repository>
    <!-- Snapshot repository is referenced in the global pom -->
    </repositories>

    <dependencies>

        <!-- Lutece Core -->
        <dependency>
            <groupId>fr.paris.lutece</groupId>
            <artifactId>lutece-core</artifactId>
            <version>7.0.5</version>
            <type>lutece-core</type>
        </dependency>

        <!-- Specific plugins -->
        <dependency>
            <groupId>fr.paris.lutece.plugins</groupId>
            <artifactId>plugin-myplugin</artifactId>
            <version>1.2.1</version>
            <type>lutece-plugin</type>
        </dependency>
        (...)
     </dependencies>
</project>

       
```
   
