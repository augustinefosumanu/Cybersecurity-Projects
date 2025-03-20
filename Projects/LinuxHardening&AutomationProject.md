# Linux Hardening and Automation Project

<h2>Overview</h2>
This extensive project focused on auditing and hardening a Linux server for The Baker Street Corporation (BSC) - a fictional organization - to protect confidential data from security breaches. Over multiple phases, I implemented system security enhancements, enforced access controls, and automated security tasks.
</br>
</br>
</br>
<b>Note</b>
</br>
The code in this repository includes external sources. Below is the reference to its origin: </br>
Sources: </br>
  - https://docs.google.com/document/d/1kFHWmJFY9dnGnEl-TpFPJwsUIJlDeuLyKvVo-tKvLSA/edit?tab=t.0 </br>
  - https://docs.google.com/document/d/1RmqqAC8ORFDnuLpojEUho-Rft4k_btqIrY4KenuXx1A/edit?tab=t.0 </br>
  - https://docs.google.com/document/d/1xw6dCkLgGvhmBgP69EzQ_1zYBc46x5zfXCBLvpUveIg/edit?tab=t.0 </br>
  - https://docs.google.com/document/d/1bKEnmbsVCQWxJ6zoz-dYorkm-BWc3MchmQEWdLPczP4/edit?tab=t.0 </br>
  - https://docs.google.com/document/d/1ZrseVTh6g5NbGiG6Wmov0ggQVeHenCsvCmejGLQ6EuU/edit?tab=t.0 </br>

<h2>Technical Skills</h2>
✅ System Inventory & Backup Management </br>
✅ User & Group Auditing </br>
✅ Password Policy Enforcement </br>
✅ Sudo Privilege Management </br>
✅ File & Directory Permission Hardening </br>
✅ SSH Security Configuration </br>
✅ Package & Service Management </br>
✅ Logging & Monitoring Implementation </br>
✅ Security Automation & Scheduling (cron) </br>
✅ Summary Report Documentation </br>

<h2> Downloading latest Docker Container </h2>
I successfully downloaded the required container by executing the following command: <b>sudo docker pull cyberxsecurity/container_project1_v4:latest
</b>. This action ensured that the latest version of the container was retrieved from the repository, allowing for seamless deployment and further development.
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/xYMHrV5.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/ZIbmLra.png" height="80%" width="90%" alt=""/>
<br />
<br />
  
<h2> Starting the Project Container </h2>
I initiated the container by executing the following command: <b>sudo docker run -d --hostname=Baker_Street_Linux_Server --network=host --name project1_v4 cyberxsecurity/container_project1_v4:latest
</b>. This action started the container in detached mode, assigned it a hostname, connected it to the host network, and ensured it was properly named for easy identification and management.
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/RvuOUgR.png" height="80%" width="90%" alt=""/>
<br />
<br />

<h2> Connecting to the Running Container </h2>
I accessed the running container by executing the following command: <b>sudo docker exec -it project1_v4 /bin/bash
</b>. This action allowed me to open an interactive Bash shell within the container, enabling direct interaction for configuration, troubleshooting, or executing commands as needed.
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/xTYZ01I.png" height="80%" width="90%" alt=""/>
<br />
<br />
  
<h2> Retrieving System Information from the Container </h2>
I gathered essential system details from the running container by executing the following commands: <b>hostname</b>, <b>cat /etc/os-release</b>, <b>free -h</b>, and <b>uptime</b>. These actions helped verify the container’s system specifications and status for further configuration and monitoring.
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/ID5JGD8.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/qZ5LVpQ.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/VKNIcHL.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/FBH9TmL.png" height="80%" width="90%" alt=""/>
<br />
<br />

<h2> Backing Up the Operating System </h2>
I archived the root filesystem while excluding specific directories that do not need to be backed up, such as /proc, /tmp, /mnt, /sys, /dev, and /run. The resulting compressed tarball, baker_street_backup.tar.gz, ensured that essential system files were preserved for recovery or migration purposes.
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/7jaFLEQ.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/VRAm603.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/oaTUVYM.png" height="80%" width="90%" alt=""/>
<br />
<br />

<h2> Removing Terminated Staff Accounts and Associated Data </h2>
I removed all staff members who had been terminated from the system. As part of this process, I ensured the deletion of their home directories and associated files to maintain data security and compliance.
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/u8VvKWy.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/POoyQg0.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/tYIYd8W.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/AF1Yzq2.png" height="80%" width="90%" alt=""/>
<br />
<br />


<h2> User Account Management for Staff on Leave </h2>
I locked the accounts of all staff members currently on temporary leave to restrict access during their absence. Additionally, I unlocked the accounts of any employed users to ensure they could access the system without interruption.
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/PjVEhKR.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/A9dCtbn.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/qdxMPSY.png" height="80%" width="90%" alt=""/>
<br />
<br />

<h2> Employee Group Reassignment and Marketing Department Closure </h2>
I moved all employees from the marketing department to a newly created group called "research," ensuring that the group was created if it did not already exist. Additionally, I removed the marketing group from the system, as the marketing department was officially closed this year.
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/MKpgRwD.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/d4tZGI3.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/D47b6R8.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/wRKb94w.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/dneUaEb.png" height="80%" width="90%" alt=""/>
<br />
<br />

<h2> Updating Password Requirements for User Accounts </h2>
I updated the password requirements for all users to enhance security. To implement these changes, I edited the <b>/etc/pam.d/common-password</b> file and added the necessary settings to the line: <b>password requisite pam_pwquality.so minlen=12 dcredit=2 ucredit=-1 lcredit=-1 ocredit=-2 retry=3</b>.
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/trx6Onp.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/J24ieQ8.png" height="80%" width="90%" alt=""/>
<br />
<br />


<h2> Restricting and Assigning Sudo Privileges </h2>
I reviewed and updated sudo privileges to ensure proper access control. The following changes were implemented:</br>

Retained full sudo privileges only for Sherlock. All other users with full sudo access were removed.</br>
Granted Watson and Mycroft sudo privileges exclusively to execute the script located at: <b>/var/log/logcleanup.sh</b>.</br>
Allowed all employees in the research group to execute the script at: <b>/tmp/scripts/research_script.sh</b>.</br>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/G0EJNaH.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/F12TCdc.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/fjLlwZk.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/pw1j1qA.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/DWxWGE2.png" height="80%" width="90%" alt=""/>
<br />
<br />

<h2> Restricting World Permissions in User Home Directories </h2>
I identified and removed any world permissions (read, write, or execute) from files located in all user home directories. This was done to enhance security and ensure that no files were globally accessible. The permissions were updated to restrict unauthorized access while maintaining necessary user functionality.
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/j5IL53g.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/bF9qfaX.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/FeGAw9C.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/H6b3IVJ.png" height="80%" width="90%" alt=""/>
<br />
<br />

<h2> Updating File Permissions for Department-Specific Scripts </h2>
I searched for and updated file permissions for department-specific scripts using a case-insensitive search. The following changes were applied:<br />

Engineering scripts (files containing "engineering" in the filename): Restricted access to members of the engineering group, allowing only them to view, edit, or execute these files.<br />
Research scripts: Granted permissions exclusively to the research group, ensuring only authorized members could access or modify them.<br />
Finance scripts: Adjusted permissions to allow only finance group members to view, edit, or execute these files.<br />
These changes were made to ensure proper access control and security for department-specific scripts.<br />
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/Kqeb2Wz.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/yp82LMI.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/4bc6dVJ.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/iRSINuL.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/6FxT2KG.png" height="80%" width="90%" alt=""/>
<br />
<br />

<h2> SSH Security Configuration Update </h2>
I updated the SSH configuration to enhance security by implementing the following restrictions:<br />

Disabled empty password logins to prevent authentication without a password.<br />
Blocked SSH access for the root user to reduce the risk of privilege escalation attacks.<br />
Restricted SSH to only use port 22, preventing connections on other ports.<br />
Enabled SSH Protocol 2 to ensure secure communication.<br />
After applying these updates, I restarted the SSH service using the command: <b>service ssh restart
</b>. These changes help improve system security and reduce unauthorized access risks.
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/vvcaG1A.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/7kXCWpy.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/uX11TkL.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/BFsKvlt.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/w4mcTLd.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/90eXiCu.png" height="80%" width="90%" alt=""/>
<br />
<br />

<h2> System Package Update and Upgrade </h2>
I updated the package manager to ensure it had the latest package information by running: <b>apt update</b>. Following that, I upgraded all installed packages to their latest versions by executing: <b>apt upgrade -y</b>. These updates help maintain system stability, security, and performance by ensuring all packages are up to date.
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/TPiRcAt.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/I2ejdxG.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/LkTK0dB.png" height="80%" width="90%" alt=""/>
<br />
<br />

<h2> Generating Installed Package List and Security Audit </h2>
I created a file named package_list.txt containing a list of all installed packages using the command: <b>apt list --installed > package_list.txt</b>. I then checked for the presence of telnet and rsh-client, as these packages can introduce security risks:
Telnet: Transmits data, including passwords, in plaintext, making it vulnerable to interception and man-in-the-middle attacks.<br />
RSH-Client: Lacks encryption, allowing credentials and data to be easily captured by attackers.<br />
I removed the packages as these actions help maintain system security by eliminating insecure protocols and reducing potential attack vectors.
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/h0frL8Z.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/qeSXELU.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/3yYKl11.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/BU4hgt3.png" height="80%" width="90%" alt=""/>
<br />
<br />

<h2> Installation of Security Packages and Hardening Features </h2>
I installed the following security packages to enhance system protection: <b>ufw</b>, <b>lynis</b>, and <b>tripwire</b> due to the protections they provide to the system. UFW
provides an easy-to-use firewall for managing incoming and outgoing traffic, Lynis identifies vulnerabilities and misconfigurations, and Tripwire, a file integrity monitoring tool, detects unauthorized changes and alerts administrators.
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/Np7YjYZ.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/hItdqLo.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/s5iAmbn.png" height="80%" width="90%" alt=""/>
<br />
<br />

<h2> Service Audit and Removal of Unnecessary Services </h2>
I listed all running services and saved the output to service_list.txt. I then checked if MySQL or Samba services were running, as these can pose security risks if not properly configured:
MySQL: If not secured, it can be an entry point for unauthorized database access.<br />
Samba: Can expose file-sharing services to unauthorized users if misconfigured.<br />
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/xaSvXiU.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/LYmDEKB.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/HMjnIWE.png" height="80%" width="90%" alt=""/>
<br />
<br />

<h2> Configuring Persistent Logging and Log Rotation </h2>
I modified the journald.conf file located at /etc/systemd/journald.conf using nano to enhance log management. The following settings were updated and uncommented:
<b>Storage=persistent</b> → Ensures logs are saved locally even after reboots. <br />
<b>SystemMaxUse=300M</b> → Limits log storage to 300MB to prevent excessive disk usage. <br /> 
Additionally, I edited the log rotation settings in <b>/etc/logrotate.conf</b> to prevent logs from consuming too much space. The changes included:
Changing log rotation from weekly to daily.<br />
Setting logs to rotate out after 7 days.<br />
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/Ya6u8qR.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/FqRc3n1.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/d4G7xZ0.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/2Ketnzl.png" height="80%" width="90%" alt=""/>
<br />
<br />

<h2> Updating and Executing Hardening Script </h2>
I copied the provided script 1 template into a file named hardening_script1.sh and replaced all placeholders with the correct values. After ensuring there were no placeholders remaining, I updated the script permissions and executed it for validation.
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/3eejVht.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/H0yNUrQ.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/ppNWBkL.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/TFdEcJV.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/DaPNwih.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/wMCrHM0.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/UrbUFfo.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/dRvrNbs.png" height="80%" width="90%" alt=""/>
<br />
<br />

<h2> Updating and Executing Hardening Script 2 </h2>
I copied the provided script 2 template into a file named hardening_script2.sh and replaced all placeholders with the appropriate values, ensuring no placeholders remained.
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/qWuwWZM.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/ghNQof2.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/gbRrSDn.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/U4GMRLD.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/qVLTHcm.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/4ZeS2cu.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/iTSLWp2.png" height="80%" width="90%" alt=""/>
<br />
<br />

<h2> Scheduling Hardening Scripts Using Cron </h2>
I scheduled the execution of hardening_script1.sh and hardening_script2.sh using cron to automate their execution at specified intervals. These configurations ensure hardening_script1.sh runs at the beginning of each month, while hardening_script2.sh runs every Monday, helping maintain security compliance and system hardening.
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/uu61P6z.png" height="80%" width="90%" alt=""/>
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/IhzmER5.png" height="80%" width="90%" alt=""/>
<br />
<br />
