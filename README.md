# Dissimilar Client

This is fork of [dissimilar](https://github.com/bl-dpt/dissimilar).
It changed some points for my private purpose.

* Move Maven configuration to Gradle.
* Rename packages to com.github.pitzcarraldo for publish to my sonatype maven central.
* Remove GUI, because I don't need it.

All right reserved [BL Digital Preservation Team](https://github.com/bl-dpt).


## Repository

### Maven
```xml
    <repositories>
    ...
        <repository>
            <id>sonatype.oss.snapshots</id>
            <name>Sonatype OSS Snapshot Repository</name>
            <url>http://oss.sonatype.org/content/repositories/snapshots</url>
            <releases>
              <enabled>false</enabled>
            </releases>
            <snapshots>
              <enabled>true</enabled>
            </snapshots>
        </repository> 
    ...
    </repositories>
    
    <dependency>
        <groupId>com.pitzcarraldo</groupId>
        <artifactId>dissimilar</artifactId>
        <version>0.5-SNAPSHOT</version>
    </dependency> 
```

### Gradle
```
buildscript {
	repositories {
	...
		maven {
			url 'https://oss.sonatype.org/content/repositories/snapshots/'
		}
	}
	...
}
...
dependencies {
	...
	compile 'com.github.pitzcarraldo:dissimilar:0.5-SNAPSHOT'
	...
}
```

# Dissimilar 0.5-SNAPSHOT

A Java program for calculating PSNR and SSIM.  By default a jar for the GUI is built.

IT IS NOT YET READY OR INTENDED FOR PRODUCTION USE.  See blog post: http://www.openplanetsfoundation.org/blogs/2013-07-17-dissimilar-experimental-image-quality-assurance-tool

## Requirements:
* JDK7 with JavaFX 
* Apache-commons imaging 1.0-SNAPSHOT needs to be packaged and installed to your Maven repository (snapshot 
repository now added to pom)
* lots of RAM!
* To load JP2 files, OpenJPEG binaries need to be installed or stored in the resources folder (opj_decompress or j2k_to_image).  

## Caveats:
* Whilst the code has seen some very light testing, it should not yet be trusted in a production environment
* To get JP2 loading working some editing of code is required 

## Usage:
* The GUI expects a CSV file without headers, with two image files per line: e.g. "fileone, filetwo,"