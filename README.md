# PavanDevops
Devopslearning started in july
CI testing 
retesting CI
working commmit
1. Login via SSH
First of all login to your Ubuntu 16.04 VPS via SSH as user root

ssh root@IP_Address -p Port_number
2. Update OS Packages
and update all installed packages to the latest version

apt-get update && apt-get upgrade
3. Check Maven Version
The installation of Apache Maven is a very simple process. It is available in the official Ubuntu 16.04 reposiroty. You can check the exact version by executing the following command

apt-cache show maven | grep Version
Version: 3.3.9-3
4. Install Maven from the official repository
So currently installed is version 3.3.9. Note that the latest available version of Apache Maven is currently 3.5.2 and it is recommended version for all users.

To proceed with the installation, run the following command

apt-get -y install maven
This will install the latest Maven 3 version available in the repository among with all Maven dependencies, including Java.

After the installation is complete, you can verify whether Maven is successfully installed on your Ubuntu 16.04 server, use the following command

mvn --version
The result should be similar to

Apache Maven 3.3.9
Maven home: /usr/share/maven
Java version: 1.8.0_151, vendor: Oracle Corporation
Java home: /usr/lib/jvm/java-8-openjdk-amd64/jre
Default locale: en_US, platform encoding: ANSI_X3.4-1968
OS name: "linux", version: "2.6.32-042stab127.2", arch: "amd64", family: "unix"
5. Manual Installation of Maven
As we already mentioned, 3.3.9 is not the latest version of Maven. If you want to install the latest one, you can download it from Maven’s official website. First of all, we have to install Java on the server. It is not available in the official Ubuntu 16.04 repository, so we will add the PPA repository maintained by the Webupd8 team

apt-get install software-properties-common
apt-add-repository ppa:webupd8team/java
apt-get update
6. Install Java
Next, install Java 8 with the following command

apt-get install oracle-java8-installer
To verify the installation, run

java -version

java version "1.8.0_121"
Java(TM) SE Runtime Environment (build 1.8.0_121-b13)
Java HotSpot(TM) 64-Bit Server VM (build 25.121-b13, mixed mode)
7. Download Latest Maven Version
Download the latest stable release Maven

wget http://ftp.wayne.edu/apache/maven/maven-3/3.5.2/binaries/apache-maven-3.5.2-bin.zip
Once downloaded, unpack the zip archive

unzip apache-maven-3.5.2-bin.zip
8. Configure Maven
rename the create directory to something simpler

mv apache-maven-3.5.2 maven
Set the necessary environment variables by creating new file with the following content

nano /etc/profile.d/maven.sh

export JAVA_HOME=/usr/lib/jvm/java-8-oracle
export M2_HOME=/opt/maven
export MAVEN_HOME=/opt/maven
export PATH=${M2_HOME}/bin:${PATH}
Make sure that all paths are correct.

Run the following command to load the environment variables

source /etc/profile.d/maven.sh
