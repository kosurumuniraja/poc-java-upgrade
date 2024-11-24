# poc-java-upgrade

This Ansible playbook automates upgrading Java to version 21 on servers belonging to the java_servers group. Here's a brief breakdown:

Target Servers:

Applies to servers in the java_servers inventory group.
Uses privilege escalation (become: yes) to perform tasks requiring root access.
Variables:

Defines new_java_version as 21.
Sets the package names for Java 21 (java_package_debian for Debian-based systems and java_package_redhat for RedHat-based systems).
Tasks:

Update Package Cache: Refreshes the package cache on Debian-based systems (apt module).
Install Java:
Installs the specified Java package using apt for Debian-based systems.
Installs the specified Java package using yum for RedHat-based systems.
Set Java Alternatives: Configures the system to use Java 21 by setting it as the default Java binary with the alternatives module (Debian only).
Set Environment Variable:
Adds the JAVA_HOME environment variable to a script in /etc/profile.d to make it available system-wide.
Source Environment Variables:
Sources the environment variable script in the current shell session to apply it immediately (shell module).
Verify Installation:
Runs the java -version command to verify the installed Java version and registers the output.
Display Java Version:
Prints the output of the java -version command using the debug module.
This playbook ensures that Java 21 is installed, set as the default version, and its environment variables are configured. It is designed to work on both Debian and RedHat-based Linux distributions.

poc-java-revert_old_version
