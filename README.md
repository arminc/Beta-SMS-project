# Beta-SMS

This is the Beta-SMS project. In this readme you can find all the necessary information you need to build the Beta-SMS project. The focus of this readme is Linux (Ubuntu) but you can also adjust the settings to get it to work on Windows.

## Build enviorment

To be able to build the Beta-SMS project you need the following:

* [git] (http://git-scm.com/)
* [maven 3](http://maven.apache.org/)
* [java 1.5+](http://www.oracle.com/technetwork/java/javase/downloads/index.html)
* [eclipse](http://www.eclipse.org/) \*optional
	* [Maven Integration for Eclipse] (http://marketplace.eclipse.org/content/maven-integration-eclipse)
	* [Maven Integration for Android Development Tools] (http://marketplace.eclipse.org/content/maven-integration-android-development-tools) 
	* [EGit] (http://marketplace.eclipse.org/content/egit-git-team-provider)
* [android sdk] (http://developer.android.com/sdk/index.html)

All tree Eclipse plugins can be installed from the Eclipse market.

## Preparing

Before we can continue we need to set all the setting.

### Path variables 
Change the following settings according your settings
```
JAVA_HOME=/usr/lib/jvm/java-6-sun
M2_HOME=/home/armin/apps/maven3
MAVEN_HOME=/home/armin/apps/maven3
M2=/home/armin/apps/maven3/bin
ANDROID_HOME=/home/armin/apps/android-sdk-linux_x86

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/armin/apps/maven3/bin:/home/armin/apps/android-sdk-linux_x86/tools:/home/armin/apps/android-sdk-linux_x86/platform-tools"

Now add the changes to the file belove and logout to apply your changes
```
/etc/environment

### Maven settings
To your maven settings.xml file add the following:
```
<pluginGroups>
	<pluginGroup>com.jayway.maven.plugins.android.generation2</pluginGroup>
</pluginGroups>

Change these to the correct values and add them as well
```
<profile>
	<id>android-release</id>
	<properties>
		<sign.keystore>/path/to/keystore</sign.keystore>
		<sign.alias>key alias</sign.alias>
		<sign.storepass>keystore password</sign.storepass>
		<sign.keypass>key password</sign.keypass>
	</properties>
</profile>


The settings.xml file can be found
```
maven/conf/settings.xml

or 
```
~/.m2/settings.xml


## The source

### Getting the source

### Eclipse and the source


## Building the source

### Testing the source

## Releasing







