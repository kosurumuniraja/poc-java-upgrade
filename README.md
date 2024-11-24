# poc-java-upgrade

This Ansible playbook automates upgrading Java to version 21 on servers belonging to the java_servers group. Here's a brief breakdown:

#Target Servers:

Applies to servers in the java_servers inventory group.

Uses privilege escalation (become: yes) to perform tasks requiring root access.

#Variables:

Defines new_java_version as 21.

Sets the package names for Java 21 (java_package_debian for Debian-based systems and java_package_redhat for RedHat-based systems).

#Tasks:

Update Package Cache: Refreshes the package cache on Debian-based systems (apt module).

#Install Java:

Installs the specified Java package using apt for Debian-based systems.

Installs the specified Java package using yum for RedHat-based systems.

#Set Java Alternatives: Configures the system to use Java 21 by setting it as the default Java binary with the alternatives module (Debian only).

#Set Environment Variable:

Adds the JAVA_HOME environment variable to a script in /etc/profile.d to make it available system-wide.

#Source Environment Variables:

Sources the environment variable script in the current shell session to apply it immediately (shell module).

#Verify Installation:

Runs the java -version command to verify the installed Java version and registers the output.

#Display Java Version:

Prints the output of the java -version command using the debug module.

This playbook ensures that Java 21 is installed, set as the default version, and its environment variables are configured. It is designed to work on both Debian and RedHat-based Linux distributions.

#poc-java-revert_old_version

This Ansible playbook is designed to set Java 17 as the default version on Debian-based servers. Here's a brief explanation:

Target Servers:

Targets servers in the java_servers group.

Executes tasks with elevated privileges using become: yes.

#Variables:

Defines old_java_version as 17 and old_java_package_debian as the package name for Java 17 on Debian-based systems.

Tasks:

#Remove Newer Java Versions:

Ensures that newer Java versions (openjdk-18-jdk and openjdk-21-jdk) are uninstalled on Debian-based systems using the apt module.

#Install Java 17:

Installs the Java 17 package on Debian-based systems to ensure it is available.

#Set Java Alternatives:

Configures the system to use Java 17 as the default Java binary using the alternatives module.

#Set Environment Variable:

Sets the JAVA_HOME environment variable for Java 17 by adding it to /etc/profile.d/java.sh.

#Source Environment Variables:

Sources the environment variable script in the current shell session to apply changes immediately.

#Verify Installation:

Executes the java -version command to confirm the Java version in use and captures the output.

#Display Java Version:

Prints the output of the java -version command for verification using the debug module.

This playbook ensures that Java 17 is installed, newer versions are removed, and the system is configured to use Java 17 as the default version. It also sets and applies the JAVA_HOME environment variable.
