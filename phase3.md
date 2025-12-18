<a href="index.html"> 🏠︎Home </a>
<h1 align= "center"> Phase 3 | Application Selection for Performance Testing </h1>
<br> 

## Application Selection Matrix
<table>
  <tr>
    <th>Application</th>
    <th>Workload Type</th>
    <th>Implementation</th>
    <th>Explanation</th>
  </tr>

  <tr>
    <td>stress-ng</td>
    <td>CPU-intensive</td>
    <td>stress-ng --cpu 1 --timeout [time to run in seconds]</td>
    <td>Allows direct application of the workload through a simple command that can specifically target the CPU while also providing full control over the parameters.</td>
  </tr>

  <tr>
    <td>stress-ng</td>
    <td>RAM-intensive</td>
    <td>stress-ng --vm 1 --vm-bytes 75% --timeout [time to run in seconds]</td>
    <td>Allows direct application of the workload through a simple command that can specifically target the RAM while also providing full control over the parameters.</td>
  </tr>

  <tr>
    <td>fio</td>
    <td>I/O-intensive</td>
    <td>fio --name=test --rw=randrw --bs=4k --direct=1 --numjobs=1 --time_based --runtime=[time to run in seconds] --size=1G --directory=/tmp</td>
    <td>
      Also allows direct application of the workload, specifically I/O-intensive, and also provides full control over parameters to match testing styles across applications.
    </td>
  </tr>

  <tr>
    <td>iperf3</td>
    <td>Network-intensive</td>
    <td>
        On the Server VM (via SSH): <br><br>
        iperf3 -s <br> <br> <br>
        On the Desktop VM (seperate terminal): <br> <br>
        iperf3 -c [Server IP] -t [time to run in seconds]
    </td>
    <td>
      Allows the creation of a controlled network stream from the Desktop VM to the Server VM to measure maximum network throughput and the Server's ability to perform network-specific tasks.
    </td>
  </tr>

  <tr>
    <td>Minecraft Server</td>
    <td>Unspecified (Mixed)</td>
    <td>java -Xms1G -Xmx2G -jar server.jar nogui</td>
    <td>
      Simulates a realsitic server workload on the entire system, demonstrating how the it uses multiple subsystems simultaneously. However, this does not include network activity since there are no external connections.
    </td>
  </tr>
</table>
The applications above, up until the Server, allow consistent and specific targeting of the subsystems through configurable parameters, resultng in more accurate, individual performance metrics. By isolating each subsystem during the testing, it's possible to also observe how they may work together under stress, providing an insight into the synthesis of the operating system and hardware.

## SSH-based Installation Guide
**1. Connect to Server VM via SSH** <br> <br>
   *ssh -p [port] user@[Server IP]* <br> <br>
   
**2. Update and upgrade system packages** <br> <br>
   *sudo apt update && sudo apt upgrade* <br> <br>

**3. Install applications** <br> <br>
   *sudo apt install stress-ng* <br> <br>
   *sudo apt install fio* <br> <br>
   *sudo apt install iperf3* <br> <br>
   *sudo apt install openjdk-25-jre-headless* <br>
   *mkdir /path/to/minecraft-server* <br>
   *wget -O /path/to/minecraft-server/mcserver.jar [URL of Minecraft Server JAR]* 
  
## Expected Resource Profiles
<table>
  <tr>
    <th>Workload Type</th>
    <th>Expected CPU Usage</th>
    <th>Expected RAM Usage</th>
    <th>Expected Disk Usage</th>
    <th>Expected Network Usage</th>
  </tr>

  <tr>
    <td>CPU-intensive (stress-ng)</td>
    <td>High</td>
    <td>Low</td>
    <td>None</td>
    <td>None</td>
  </tr>

  <tr>
    <td>RAM-intensive (stress-ng)</td>
    <td>Low</td>
    <td>High</td>
    <td>Low</td>
    <td>None</td>
  </tr>

  <tr>
    <td>I/O-intensive (fio)</td>
    <td>Low</td>
    <td>Low</td>
    <td>High</td>
    <td>None</td>
  </tr>

<tr>
    <td>Network-intensive (iperf3)</td>
    <td>Low</td>
    <td>Low</td>
    <td>None</td>
    <td>High</td>
  </tr>
  
  <tr>
    <td>Minecraft Server</td>
    <td>High</td>
    <td>High</td>
    <td>Medium</td>
    <td>Low/None</td>
  </tr>
</table>
These expectations are based on the fact that the applications selected, apart from the Minecraft Server, intentionally target a specific subsystem alone, but take into account how other resources may be used simultaneously. 

## Monitoring Strategy
For each application, I will use a resource-specific monitoring tool (e.g. *htop*) alongside *nmon* to observe both the detailed activity of the primary subsystem and that of any other subsystems. 

<br>
<p align= "right">
  <a href="phase4.html"> Next </a>
</p>
