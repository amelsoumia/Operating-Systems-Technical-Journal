<a href="index.html"> 🏠︎Home </a>
<h1 align= "center"> Phase 2 | Security Planning and Testing Methodology </h1>
<br>

## Performance Testing Plan
I will be testing the Server VM’s performance remotely using the Desktop VM to connect via SSH through a Host-Only network.  Therefore, the tests will take place in the CLI using tools such as *nmon* to monitor CPU, RAM, I/O and network performance under different workloads targeting each subsystem. 

I will primarily use *nmon* to test my system, as it displays all the necessary performance metrics in one place, making documentation cleaner and more accurate. In addition, to get deeper information from different perspectives about each individual subsystem, tools like *mpstat*, *htop*, *iotop*, *iostat* and *vmstat* can be used. This also helps validate the results obtained from *nmon*.

## Security Configuration Checklist
<table>
  <tr>
   <th>Configuration</th> 
   <th>Implementation</th>
   <th>Reason</th>
  </tr>

  <tr>
    <td>Set up key-based authentication for SSH connection</td>
    <td>
         ssh-keygen -t ed25519 -C [email] <br> <br>
	       ssh-copy-id -p [SSH port] user@[Server IP]
    </td>
    <td>Much more resistant to brute-force attacks due to its cryptographic properties.</td>
  </tr>

  <tr>
    <td>Disable password authentication for SSH connection</td>
    <td>
      (in /etc/ssh/sshd_config) <br> <br>
         PasswordAuthentication yes ✗ <br>
         PasswordAuthentication no ✓
    </td>
    <td>Eliminates the possiblity of using password authentication and instead fully enforces key-based authentication.</td>
  </tr>

 <tr>
   <td>Disable root login</td>
   <td>
     (in /etc/ssh/sshd_config) <br> <br>
        PermitRootLogin yes ✗ <br>
        PermitRootLogin no ✓
  </td>
   <td>Attackers won't be able to connect to SSH as root in the case of a brute-force attack.</td>
 </tr>

 <tr>
   <td>Change default SSH port</td>
   <td>
     (in /etc/ssh/sshd_config) <br> <br>
        Port 22 ✗ <br>
        Port 2222 ✓
   </td>
   <td>Reduces likelihood of automated attacks.</td>
 </tr>

 <tr>
   <td>Identify and disable unnecessary services</td>
   <td>
     systemctl list-units --type=service --state=running <br> <br>
	   sudo systemctl disable/mask [unnecessary service]
   </td>
   <td>Reduces attack surface by removing services that aren't required for the server's intended purpose.</td>
 </tr>

 <tr>
   <td>Download, enable and configure UFW</td>
   <td>
     sudo apt install ufw <br> <br>
     sudo ufw default deny incoming <br> <br>
   	 sudo ufw default allow outgoing <br> <br>
  	 sudo ufw allow from [Desktop IP] to [Server IP] port [SSH port] proto tcp
   </td>
   <td>Firewall only allows the Desktop VM to connect to the Server VM via SSH, blocking any possible attackers from doing so.</td>
 </tr>

 <tr>
   <td>Enforce all AppArmour profiles</td>
   <td>sudo aa-enforce /etc/apparmor.d/*</td>
   <td>All protected applications can only do what they are authorised to, meaning if any are exploited, system security is less likely to be significantly impacted.</td>
 </tr>

 <tr>
   <td>Enable automatic updates</td>
   <td>
     sudo apt install unattended-upgrades <br> <br>
	   sudo systemctl enable --now unattended-upgrades
   </td>
   <td>Reduces risk of attack through known vulnerabilities in the system.</td>
 </tr>

 <tr>
   <td>Limit sudo privileges</td>
   <td>
     (in /etc/sudoers) <br> <br>
     username ALL=(ALL) [specified paths to files allowed to execute]
   </td>
   <td>Enforces principle of least privilege, reducing the risk of privilege escalation by attackers or accidental harm to the system by users.</td>
 </tr>
</table>

## Threats and Mitigation Strategies
There are many vulnerabilities by default, both within the system and through SSH connection, that can be exploited by attackers if the configuration above is not implemented. Examples include exposed configuration files, a predictable and accessible SSH port, reachable root privileges and easier unauthorised access through password-based authentication. 

Without strong security configuration, both users and attackers can intentionally or unintentionally harm the system. Users are likely to accidentally delete or modify configuration files due to improper file permissions or user privileges, leading to a high-impact risk, while attackers can exploit this, potentially leading to privilege escalation or worse. Additionally, a predicatble SSH port increases the risk of automated attack by outsiders. With password authentication and root login also enabled, attackers are then able to easily log in using brute-force to access the server with root permissions. However, this is less likely due to the many steps required but the risk is still medium because of its high impact. It's important to eliminate all these threats to minimise the likelihood of other threats occurring because they are all interconnected and work together to protect the system as a whole. 

Configuration files can be made immutable by the root user when changes are not intentionally being made. By also minimising file permissions so that they can only be read or modified by specific users, and reducing sudo permissions, the protection of important files is further strengthened against users and attackers. The default SSH port should be changed to reduce likelihood of automated attack on the known port, and a firewall should be configured to only allow specific host-only connections to the server in order to reduce external exposure. At this stage, disbaling password authentication and only allowing key-based login further prevents successful brute-force attacks by outsiders.

After taking all the necessary measures, the overall risk of threats is significantly reduced as the likelihood and impact of attacks become low.

<br>
<p align= "right">
  <a href="phase3.html"> Next </a>
</p>
