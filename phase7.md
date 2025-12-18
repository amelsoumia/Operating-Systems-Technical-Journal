<a href="index.html"> 🏠︎Home </a>
<h1 align= "center"> Phase 7 | Security Audit and System Evaluation </h1>
<br>

## Lynis Security Auditing
A total of 4 Lynis security audits were performed on my system, leading me to further strengthen my system's security each time by taking into account warnings, suggestions and other information from the report. This includes an initial audit before any security configurations were made. 

To achieve a Hardening Index of at least 73, it's required to:
- Thoroughly update SSH configuration permissions and settings
- Mask or disable unnecessary services and legacy protocols (DCCP, SCTP, RDS, TIPC)
- Secure file permssions and attributes if necessary
- Install extra services that help protect the system
  
These were all implemented in addition to the initial security configurations covered in the previous phases.

<img width="593" height="43" alt="First lynis test (no configs applied)" src="https://github.com/user-attachments/assets/bd223429-da59-4089-9a52-93dca50da020" /> <br>
<img width="601" height="50" alt="Lynis after first config " src="https://github.com/user-attachments/assets/8e14c66d-dd8b-4154-a505-5f4e68cd4f0b" /> <br>
<img width="600" height="44" alt="Lynis after second config" src="https://github.com/user-attachments/assets/7d26e9c6-4578-4e79-aebd-62acbc69ea71" /> <br>
<img width="347" height="18" alt="Final Lynis score" src="https://github.com/user-attachments/assets/d6d3d2fc-f3dc-4298-a263-bb35f2f48d14" />

These remediations likley have minimal impact on the system, with little to no performance overhead. This meant that I didn't encounter any measurable trade-offs between security and performance, however, initial configurations like enabling a firewall could signifcantly impact connections required for network testing.

## Network Security Assessment
<img width="323" height="99" alt="Nmap 1" src="https://github.com/user-attachments/assets/b4da327d-84d6-4350-ac44-3e4923dcefd4" /> <br>
<img width="254" height="79" alt="Nmap 2" src="https://github.com/user-attachments/assets/be528500-08c2-4671-9030-1f10a1245bf4" /> <br>
<img width="269" height="81" alt="Nmap 3" src="https://github.com/user-attachments/assets/6fcc5d73-e75d-4b77-8126-321fccfe713f" />

## Service Inventory
<img width="440" height="234" alt="Running Services" src="https://github.com/user-attachments/assets/77893854-3d5d-4d34-a7c6-5d94e81a1ad3" /> <br>
I have already masked unnecessary services, leaving the services above enabled as they are either core services or run security-related tasks.

## Security Configuration Check
<img width="263" height="126" alt="Baseline check" src="https://github.com/user-attachments/assets/3b57b0c3-8f94-4050-8e4b-e91f67e5cabe" /> <br>
Above, I ran my security baseline script which checks if all the core security configurations are enabled and ouputs the result of each check in the command line.
