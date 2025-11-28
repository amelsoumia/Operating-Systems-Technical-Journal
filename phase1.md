<a href="index.html"> 🏠︎Home </a>
<h1 align= "center"> Phase 1 | System Planning and Distribution Selection </h1>
<br> <br>
<img 
  width="400" 
  height="300" 
  align= "left"
  hspace= "30"
  alt="System Architecture Diagram drawio" 
  src="https://github.com/user-attachments/assets/ed0193f0-7e73-4d44-a93a-12036b5e398b" />
  <br><br> 
This System Architecture Diagram provides a basic view of how my two virtual machines will be set up and how they'll interact with each other. I'll go into more detail below about the key decisions I made while designing this, regarding my distribution choice, workstation setup, and network configuration.
<br clear="all"> <br>

## Why Ubuntu?
I chose Ubuntu as it's the most compatible and easy-to-use distribution for the completion of the required tasks in this coursework. While other distributions each offer their own favourable features, for example Fedora and Arch being highly innovative and up-to-date, and Mint being very user-friendly, Ubuntu provides the best overall balance. It has a large community with vast documentation to help with any issues, it provides all the packages and tools needed, it’s relevant in many professional industries, including IT for Software Development, and it’s compatible with VirtualBox. In addition, Ubuntu’s stability and security make it a very reliable option, especially for this project. 

## Choosing a Workstation Setup
I chose to use a virtual Ubuntu Desktop on VirtualBox to run the server rather than my actual host machine as it allows me to use a Linux OS, gives me full control over system and network configuration, and prevents my host machine from being affected by the tasks performed. I also won’t use a hybrid method for consistency. This way, all the packages I need will be available and easier to install. Using the same distribution for the workstation and server means full compatibility and less issues will likely arise when using certain tools.

## VirtualBox VM Specification and Network Configuration
<table>
  <tr>
    <th> Desktop VM </th>
    <th> Server VM </th>
  </tr>

  <tr> 
    <td> 
      <img 
        width="400" 
        height="300" 
        alt="VM Desktop Specs and Config" 
        src="https://github.com/user-attachments/assets/e9bbd2ef-ed8e-4bf6-b880-3919f47e17db" /> 
      <br> <br>
      <img 
        width="494" 
        height="25" 
        alt="VM Desktop IP config" 
        src="https://github.com/user-attachments/assets/e6d99f04-a27d-4f0a-a8c3-2bdca99c2847" />
    </td>
    <td>  
      <img 
        width="400" 
        height="300" 
        alt="VM Server Specs and Config " 
        src="https://github.com/user-attachments/assets/48ff3262-9937-4f08-af28-6a6ac89d8768" />
      <br> <br>
      <img 
        width="181" 
        height="16" 
        alt="VM Server IP config" 
        src="https://github.com/user-attachments/assets/f6345c14-d0c3-4390-ba13-93498265f289" />
    </td>
  </tr>
</table>
For both of the VMs above, I chose to configure them with NAT *and* Host-Only network connections. NAT will allow me to install packages without sacrificing the security of my VMs as they have a one-way connection to the internet. The Host-Only connection will allow the Desktop VM to connect to the Server VM via SSH later in the project. 

## CLI Specification Documentation
<table>
  <tr>
    <th> Desktop VM </th>
    <th> Server VM </th>
  </tr>

  <tr> 
    <td> 
     <img
       width="350" 
       height="300" 
       alt="VM Desktop Phase 1 CLI " 
       src="https://github.com/user-attachments/assets/71c7f271-e9a7-4ac0-8a7c-94ce6578bf0f" />
    </td>
    <td>  
     <img 
       width="350"
       height="300" 
       alt="VM Server Phase 1 CLI" 
       src="https://github.com/user-attachments/assets/459510b4-8e23-4e00-919f-13d441dd5a63" />
    </td>
  </tr>
</table>
<br> <br>

<p align= "right">
  <a href="phase2.html"> Next </a>
</p>
