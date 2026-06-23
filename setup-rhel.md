# Set up Red Hat Enterprise Linux (RHEL) 

## Terminal Commands

### Timedatectl
**timedatectl** displays the current local (system) time, UTC, hardware clock (RTC) , time zone, and NTP synchronization status on systemd-based Linux systems. If no subcommand is provided to timedatectl, status is assumed by default.

    $ timedatectl

### Hostnamectl
**hostnamectl** displays the system’s hostname information along with related metadata such as chassis type, deployment environment, and machine ID. If no subcommand is provided to hostnamectl, status is assumed by default.

    $ hostnamectl

### Display installed RHEL version
The cat command is used to display a file containing a single line of text that provides the release name and version of the installed RHEL operating system.

    $ cat /etc/redhat-release

If /etc/redhat-release is unavailable or outdated, you can use other commands to check the RHEL version:

    $ cat /etc/os-release  # Provides detailed OS information, including the version and ID.
    
    $ uname -r  # Shows the kernel version, which can indirectly indicate the OS version.
    
    $ hostnamectl  # Displays the OS version along with other system details.

