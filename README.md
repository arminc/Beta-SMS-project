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
```

Now add the changes to the file belove and logout to apply your changes
```
/etc/environment
```

### Maven settings
To your maven settings.xml file add the following:
```
<pluginGroups>
	<pluginGroup>com.jayway.maven.plugins.android.generation2</pluginGroup>
</pluginGroups>
```

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
```

The settings.xml file can be found
```
maven/conf/settings.xml
```
or 
```
~/.m2/settings.xml
```

## The source

To get the source do the following.

First get the Beta-SMS-project
```
git clone git://github.com/arminc/Beta-SMS-project.git
````

Now enter in to the Beta-SMS-project and get the two other projects
```
cd Beta-SMS-project
git clone git://github.com/arminc/Beta-SMS-it.git
git clone git://github.com/arminc/Beta-SMS.git
```

### Emulator

To be able to run and test the Beta-SMS project you need to create a Emulator with Android 2.1 and call it “TestEmu”

### Eclipse and the source

To import the sources to Eclipse just import the Beta-SMS-project as an "Existing Maven Project". 

## Building the source

### Beta-SMS
When in the Beta-SMS project you can do the following:
```
mvn clean test
mvn clean package
mvn android:emulator-start
mvn deploy
mvn redeploy
mvn undeploy
mvn android:emulator-stop
```

### Beta-SMS-it
When in the Beta-SMS-it project you can do the following:
```
mvn clean package
mvn android:emulator-start
mvn deploy
mvn redeploy
mvn undeploy
mvn android:emulator-stop
mvn install
mvn android:instrument
```

### Beta-SMS-project
When in the Beta-SMS-project project you can do the following:
```
mvn install
```

## Releasing
To do a release you need to do the following:
```
mvn clean install -Prelease \
-Dsign.keystore=/path/to/key.keystore \
-Dsign.alias=mykey \
-Dsign.storepass=testtest \
-Dsign.keypass=testtest
```

Don't forget to change the release number every time you start a new release. You only need to change the
```
Beta-SMS/AndroidManifest.xml
```

Change these:
```
android:versionCode="?" android:versionName="?"
```




