# Set up Red Hat Enterprise Linux (RHEL) 

## Terminal Commands

### Display host date and time information
**timedatectl** displays the current local (system) time, UTC, hardware clock (RTC) , time zone, and NTP synchronization status on systemd-based Linux systems. If no subcommand is provided to timedatectl, status is assumed by default. Ensure timekeeping is accurate. Maintaining accurate time ensures that your system operates reliably and securely in both local and networked environments.

    $ timedatectl

### Display hostname information
**hostnamectl** displays the system’s hostname information along with related metadata such as chassis type, deployment environment, and machine ID. If no subcommand is provided to hostnamectl, status is assumed by default.

    $ hostnamectl

### Display installed RHEL version
The cat command is used to display a file containing a single line of text that provides the release name and version of the installed RHEL operating system.

    $ cat /etc/redhat-release

If /etc/redhat-release is unavailable or outdated, you can use other commands to check the RHEL version:

    $ cat /etc/os-release  # Provides detailed OS information, including the version and ID.
    
    $ uname -r  # Shows the kernel version, which can indirectly indicate the OS version.
    
    $ hostnamectl  # Displays the OS version along with other system details.

### Map hostname to IP address for local resolution
Mapping the hostname to an IP address for local resolution acts as a local DNS cache, allowing hostname lookups without querying external DNS servers. This is particularly useful for testing, development, and local network management.

    $ echo "192.168.1.5 server05.local server05" | sudo tee -a /etc/hosts

### Register the system and subscribe for updates
In order to keep your RHEL system up to date, you will need to register it with Red Hat. This will grant your system access to Red Hat's official repos and security updates. When prompted, enter your Red Hat credentials.

    $ sudo subscription-manager register

### Confirm Red Hat registration status
If your Red Hat credentials are valid and current, and the system was successfully registered, the output should read “Overall Status: Registered”. This message confirms the system has valid entitlements and can now download updates.

    $ sudo subscription-manager status

### Confirm Red Hat repository status
Confirm the repositories "AppStream" and "BaseOS" registered before attemptintg to download updates.

    $ sudo dnf repolist

### Download and install updates
Download and install all available updates.

    $ sudo dnf -y update

### Restart system after major software updates
After updating critical software, such as the system kernel, restart your system to apply the changes. Consider including a custom reason in the system logs by using the option **--message=""**.

    $ sudo systemctl --message="Kernel update applied" reboot
