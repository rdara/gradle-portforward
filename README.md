# gradle-portforward

## Port Forwarding aka Tunneling
Port forwarding is handy when one requires to access a service thats running on a remote machine, but its not port is not accessible.

Example
...
ssh root@{RemoteHostURL} -L {localPort}:localhost:{remortPort}
...

Refer [SSH Port Forward aka Tunneling](https://www.ssh.com/ssh/tunneling/example) for further details.

The port forwarding is useful for automating testing.

##Gradle spwan task
The [Gradle spawn plugin](https://github.com/marc0der/gradle-spawn-plugin) is used for starting and stopping UNIX command line processes from within your build. This plugin also can be used to establish tunneling.

##Gradle-portforward
This gradle project demonstrates opening up the tunnel, running tests while tunnel is open, closing the tunnel and orchestartion of task with the minimilistic code that can be experimented.

##Step-by-step instructions to use this project if you already have gradle
1. Clone the project on any new directory
...
git clone https://github.com/rdara/gradle-portforward.git
...
2. cd to gradle-protforward directory 
3. Run
...
./gradlew -Dremote.host={remoteHostURL} -Dremote.port=${remoteHostPort} test
...
Substittue remoteHostURL and remoteHostPort with remost host and port values.

##Step-by-step instructions to use this project if you dont have gradle

1. Install gradle
Check whether gradle is already installed on your system with
...
gradle -v
...
If its not installed follow [Gradle Installing Guide](https://docs.gradle.org/current/userguide/installation.html) and install gradle.
2. Create a project from scratch
Follow instructions here at [Creating gradle wrapper](https://guides.gradle.org/creating-new-gradle-builds/) project
3. Make build.gradle
Create a build.gradle in your project's home directory and copy the [contents](https://raw.githubusercontent.com/rdara/gradle-portforward/master/build.gradle) to that build.gradle
4. Run
...
./gradlew -Dremote.host={remoteHostURL} -Dremote.port=${remoteHostPort} test
...

## startSSHTunnel and stopSSHtunnel
You can issue the following commands to start or stop the tunnel as desired. Once tiunnel is established, that tunnel will be opened until stopped.
...
./gradlew -Dremote.host={remoteHostURL} -Dremote.port=${remoteHostPort} startSSHTunnel
...
...
./gradlew stopSSHTunnel
...




