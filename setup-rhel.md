# Set up Red Hat Enterprise Linux (RHEL) 

#### Applies to: RHEL 10.2

## Terminal Commands

### Display host date and time information
**timedatectl** displays the current local (system) time, UTC, hardware clock (RTC) , time zone, and NTP synchronization status on systemd-based Linux systems. If no subcommand is provided to timedatectl, status is assumed by default.

    $ timedatectl

### Confirm accurate time
Ensure timekeeping is accurate. Maintaining accurate time ensures that your system operates reliably and securely in both local and networked environments.

Accurate time is critical for log correlation, certificate validation, and authentication protocols such as Kerberos.

If your system time is inaccurate, first ensure the system has a charged CMOS battery and time is set correctly in its BIOS.

Next, confirm the system timezone is correct. If it is not, list all available options, and then select the timezone closest to your system’s location.

Finally, confirm time synchronization. RHEL uses chrony by default.

    $ timedatectl list-timezones
    $ sudo timedatectl set-timezone America/Los_Angeles
    $ chronyc tracking

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

### Confirm system journal recorded the custom reboot message
Use journalctl to view the custom reboot message after the system comes back up.

    $ journalctl -b -1 | grep -i reboot

### Confirm the firewall status
RHEL installs and enables a firewall by default. Confirm the firewall status is "running".

    $ sudo firewall-cmd --state

List all active rules to confirm the services allowed in the default zone.

    $ sudo firewall-cmd --list-all

Query the list of named services that can be added to the firewall.

    $ sudo firewall-cmd --get-services

### Configure the firewall
Open firewall ports as needed by either invoking the service name or a custom port and protocol. Complete the firewall configuration by reloading the firewall service so the changes can take immediate effect.

    $ sudo firewall-cmd --add-service=http --permanent
    $ sudo firewall-cmd --add-service=https --permanent
    $ sudo firewall-cmd --add-port=19132/udp --permanent
    $ sudo firewall-cmd --add-port=25565/udp --permanent
    $ sudo firewall-cmd --add-port=25565/tcp --permanent
    $ sudo firewall-cmd --reload

### Confirm SELinux status
RHEL sets SELinux to run in enforcing mode by default. Confirm the status is "Enforcing".

    $ getenforce

