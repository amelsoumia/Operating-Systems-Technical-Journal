<a href="index.html"> 🏠︎Home </a>
<h1 align= "center"> Phase 4 | Initial System Configuration & Security Implementation </h1>
<br>

## SSH Connection Evidence 
<img 
  width="350" 
  height="300" 
  align ="left"
  alt="Successfull ssh login" src="https://github.com/user-attachments/assets/c647652b-05ca-4a80-9efb-8169183b06db" />
  <br><br>
  This screenshot shows my successful connection to the Server VM from the Desktop VM via SSH, after having made changes to the sshd_config file, shown below.
<br clear="all"> <br>

## Configuration Files Documentation
<table>
  <tr>
    <th></th>
    <th>Before Configuration</th>
    <th>After Configuration</th>
  </tr>

  <tr>
    <th>SSH Config File</th>
    <td>
      <img width="150" height="15" alt="Root login before" src="https://github.com/user-attachments/assets/ad6604c6-6ec8-4774-b7b1-9bb65a731ac5" /> <br>
      <img width="150" height="15" alt="Pubkey auth before" src="https://github.com/user-attachments/assets/7b11d134-2698-495f-a660-59a6293b2180" /> <br>
      <img width="150" height="15" alt="Pass auth before" src="https://github.com/user-attachments/assets/f77155ca-0f59-40eb-88f7-d3802d24dc78" /> <br>
      <img width="50" height="15" alt="Port before" src="https://github.com/user-attachments/assets/0c4b0266-e92b-469b-a99b-5a2007078b19" />
    </td>
    <td>
      <img width="150" height="15" alt="Root login after" src="https://github.com/user-attachments/assets/ce885631-b3a6-4056-aa87-3002880d0b65" /> <br>
      <img width="150" height="15" alt="Pubkey auth after" src="https://github.com/user-attachments/assets/5ec85b1a-7344-472d-b848-3a108fe399ea" /> <br>
      <img width="150" height="15" alt="Pass auth after" src="https://github.com/user-attachments/assets/7fec047a-3150-4ea5-a684-b262738fedf5" /> <br>
      <img width="50" height="15" alt="Port after" src="https://github.com/user-attachments/assets/c0613a69-7152-4e83-9949-51469231369f" /> 
    </td>
    
  </tr>

  <tr>
    <th>Sudoers File</th>
    <td>
      <img width="300" height="100" alt="User privlg before" src="https://github.com/user-attachments/assets/c176481a-60b9-4807-b662-e155368885ac" />
    </td>
    <td>
      <img width="300" height="100" alt="User privlg after" src="https://github.com/user-attachments/assets/b3602135-2160-401c-b4fa-fbb4d889aab8" />
    </td>
  </tr>
</table>
<br>

## Firewall Documentation
<img width="317" height="100" alt="UFW status" src="https://github.com/user-attachments/assets/59d56aef-730d-4693-85b7-90c7f500cbfa" /> 
<br>
<img width="349" height="34" alt="UFW added rules" src="https://github.com/user-attachments/assets/33b6f44f-c5b1-4f04-9318-a384925e28fc" />

<br>
<p align= "right">
  <a href="phase5.html"> Next </a>
</p>
