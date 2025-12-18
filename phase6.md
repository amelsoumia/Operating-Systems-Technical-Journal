<a href="index.html"> 🏠︎Home </a>
<h1 align= "center"> Phase 6 | Performance Evaluation and Analysis </h1>
<br>

## Testing Approach
I first performed a baseline performance test using only *nmon* before any security configurations were implemented. Then I did the same again after the security configurations, but there were no significant changes with no applications running. 

<table>
  <tr>
    <th>Before</th>
    <th>After</th>
  </tr>

  <tr>
    <td>
      <img width="500" height="200" alt="First baseline perf test (no config applied)" src="https://github.com/user-attachments/assets/94898abb-34c2-4bdf-807b-dca7b26842f6" />
    </td>
    <td>
      <img width="500" height="200" alt="Nmon after configs" src="https://github.com/user-attachments/assets/1b3d8937-f3f9-45f7-ba42-85af0d1b8608" />
    </td>
  </tr>
</table>

While performing the application load testing for each workload type, I used both *nmon* and subsystem-specific tools as previosuly mentioned in my methodology. This was to ensure results are reliable and accurate as well as gaining deeper insight into how each subsystem behaves. 

<table>
  <tr> 
    <th></th>
    <th>CPU</th>
    <th>Disk</th>
    <th>I/O</th>
    <th>Network</th>
    <th>Server</th>
  </tr>

  <tr>
    <th>Individual Views</th>
    <td>
      <img width="400" height="200" alt="TOP CPU INTENSIVE" src="https://github.com/user-attachments/assets/54f92ad3-9b7e-4ee7-842e-15b59afc9ca3" />
    </td>
    <td>
      <img width="400" height="200" alt="RAM INTENSIVE FREE -H VMSTAT" src="https://github.com/user-attachments/assets/265bbb78-68d5-447d-a8f8-c3d7a366455c" />
    </td>
    <td>
      <img width="400" height="200" alt="IO INTENSIVE TEST EVIDENCE " src="https://github.com/user-attachments/assets/b1360d0d-cc79-4ba7-aec9-a3072f2f362a" /> <br>
      <img width="400" height="200" alt="IOSTAT IO INTENSIVE" src="https://github.com/user-attachments/assets/1777c9ae-e83e-441d-8c29-2138fe5d7ab1" />
    </td>
    <td>
      <img width="400" height="200" alt="ACTUAL NETWORK IP S LINK" src="https://github.com/user-attachments/assets/1ebd00f1-2800-4f19-b108-e2f4ad3f569f" />
    </td>
    <td>
      <img width="400" height="200" alt="IPERF3 SERVER STATS" src="https://github.com/user-attachments/assets/2088ea73-9342-43cf-a464-f533f351d200" />
    </td>
  </tr>

  <tr>
    <th>Collective View</th>
    <td>
      <img width="450" height="300" alt="NMON CPU INTENSIVE" src="https://github.com/user-attachments/assets/6348e947-d964-496b-ae5f-fd96fe816308" />
    </td>
    <td>
      <img width="450" height="300" alt="NMON RAM INTENSIVE" src="https://github.com/user-attachments/assets/ad0fd64f-5898-46aa-98de-3345168fb20d" />
    </td>
    <td>
      <img width="450" height="300" alt="NMON IO INTENSIVE" src="https://github.com/user-attachments/assets/e977cba4-84c3-4517-8cd6-1aeb50eb534a" />
    </td>
    <td>
      <img width="450" height="300" alt="ACTUAL NETWORK NMON" src="https://github.com/user-attachments/assets/02e2155c-9f01-4737-b0a6-545ff7c959fe" />
    </td> 
    <td>
      <img width="450" height="300" alt="SERVER NMON" src="https://github.com/user-attachments/assets/c2ec4ac0-b858-4c78-afda-bca97825498a" />
    </td>
  </tr>
</table>
Overall, the system performed slightly differently to what was predicted, however not in an unexpected way. CPU usage was high throughout the load testing, demonstrating active workload scheduling, while RAM usage was moderate. Network and disk activities were relatively low when not directly tested. Disk I/O seems to be the bottleneck, as its slow performance caused a significant portion of the processes to be held at waiting a state. It's unlikely that security configurations directly impacted these results as Disk I/O was otherwise low, however, they can increase I/O overhead due to logging, auditing and file scanning.

To optimise Disk I/O, it's possible to increase queue depth, allowing more processes to be queued and processed at the same time rather than them waiting. 

## Performance Data
<table>
  <tr>
    <th>Workload Type</th>
    <th>Average CPU Utilisation</th>
    <th>Average Memory Utilisation</th>
    <th>Average Disk I/O</th>
    <th>Average Network Throughput</th>
  </tr>

  <tr>
    <td>CPU-intensive (stress-ng)</td>
    <td>High</td>
    <td>High</td>
    <td>Low/None</td>
    <td>Low/None</td>
  </tr>

  <tr>
    <td>RAM-intensive (stress-ng)</td>
    <td>High</td>
    <td>High</td>
    <td>Low/None</td>
    <td>Low/None</td>
  </tr>

  <tr>
    <td>I/O-intensive (fio)</td>
    <td>High</td>
    <td>Moderate</td>
    <td>High</td>
    <td>Low/None</td>
  </tr>

<tr>
    <td>Network-intensive (iperf3)</td>
    <td>High</td>
    <td>Moderate</td>
    <td>Low/None</td>
    <td>High</td>
  </tr>
  
  <tr>
    <td>Minecraft Server</td>
    <td>Low</td>
    <td>High</td>
    <td>Low/None</td>
    <td>Low/None</td>
  </tr>
</table>

<br>
<p align= "right">
  <a href="phase7.html"> Next </a>
</p>
