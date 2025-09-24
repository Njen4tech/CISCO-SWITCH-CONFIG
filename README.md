# Welcome to CISCO setup!

This is your README. Readme files are where you can communicate what your project is and how to use it.

Write your name on line 6, save it, and then head back to GitHub Desktop.

## 🛠️ Utility and Tools

- **USB Type** (Mini Type B)
- **Power Cable**
- **Ethernet Cable**
- **Cisco 3560-X 48-Port Switch**

---

## 🌐 Environment Specifications

> ⚠️ **WARNING**  
> This is a demonstration of a configuration of a Cisco switch.  
> Different model switches may vary in configuration method and syntax on the Cisco command line.

---

## 🔧 CCL Walk-through

### 1. Turn on the device

**Instructions:**
- Plug the power cable into the rear I/O port of the Cisco switch.
- Plug the other end into a power outlet.
- Confirm that the switch powers on by observing the LED indicators.

<p align="center">
<img src="https://github.com/user-attachments/assets/eea95b75-3043-4b70-834e-966a9909307c" width="70%" alt="Cisco Console Port" />
</p>

---

### 2. Connect to the Console Port

**Instructions:**
- Use a USB Mini Type B cable to connect your laptop to the console port of the switch.
- Ensure the USB end is plugged into your computer and the Mini Type B into the switch.

<p align="center">
<img src="https://github.com/user-attachments/assets/14a9db29-9d79-4522-ae19-e3483a65ad0a" width="50%" alt="USB Mini Type B" />
</p>

---

### 3. Use PuTTY to Configure the Switch

**Instructions:**
- Open **PuTTY** (or **TeraTerm**) on your computer.
- Select the **Serial** connection type.
- Enter the COM port that corresponds to your USB-to-Serial adapter.
- Click **Open** to access the switch terminal.

<p align="center">
<img src="https://github.com/user-attachments/assets/be75c2a0-ab57-46e0-9ce6-254a151dcceb" width="70%" alt="Using PuTTY to Configure" />
</p>

---

### 4. Change Default Hostname in Terminal

**Instructions:**
- In the terminal, type `enable` and press Enter.
- Then enter `configure terminal`.
- Use `hostname <your_hostname>` to rename the switch.

<p align="center">
<img src="https://github.com/user-attachments/assets/e38066b6-9dc5-485b-a29b-45f6c52dc1ab" width="70%" alt="Change Host" />
</p>

---

### 5. Enter Cisco Switch

**Instructions:**
- At the terminal prompt, press Enter to access the switch CLI.
- Enter privileged EXEC mode by typing `enable`.

<p align="center">
<img src="https://github.com/user-attachments/assets/6c3227ff-e60c-4c19-8f04-5a2d5ffdb1e7"  width="70%" alt="Installing pfSense" />
</p>

---

### 6. Configure and Assign a VLAN Interface (SVI)

**Instructions:**
- In global config mode, type:
  ```
  interface vlan 10 
  ip address 10.10.10.1 255.255.255.0
  no shutdown
  ```

---

### 7. View VLAN List

**Instructions:**
- Type the following command to display the VLANs:  
  ```
  show vlan brief
  ```

<p align="center">
<img src="https://github.com/user-attachments/assets/fcd637d7-4f7c-4e76-8325-e0c49e40dff5" width="70%" alt="VLAN Brief Screenshot" />
</p>

---

### 8. Save the Configuration

**Instructions:**
- Save the running configuration to NVRAM using:
  ```
  write memory
  ```

<p align="center">
<img src="https://github.com/user-attachments/assets/296ca1c1-1f75-4a49-a899-1d2288124299" width="70%" alt="Saving Configuration" />
</p>

---

### 9. Final Setup Overview

**Instructions:**
- Repeat the following steps for each VLAN (10 through 30):

```
MySwitch(config)# vlan 10 
MySwitch(config-vlan)# name VLAN
MySwitch(config-vlan)# exit
---
MySwitch(config)# interface vlan 10
MySwitch(config-if)# ip address 10.10.10.1 255.255.255.0
MySwitch(config-if)# no shutdown
MySwitch(config-if)# exit
```

<p align="center">
<img src="https://github.com/user-attachments/assets/01a4ecd4-9de1-438e-89e9-8e82c8a9c54c" width="70%" alt="Final Cisco Switch Setup Overview" />
</p>

---

### 10. Select Ports to Enable

**Instructions:**
- Use the following command to configure access ports:

```
MySwitch(config)# interface range GigabitEthernet0/1-12, GigabitEthernet0/13-24
MySwitch(config-if-range)# switchport mode access
MySwitch(config-if-range)# switchport access vlan 10
MySwitch(config-if-range)# no shutdown
MySwitch(config-if-range)# exit
```

---

### 11. Enable IP Address for the Selected VLAN

<p align="center">
<img src="https://github.com/user-attachments/assets/647d3bb4-c5c2-4800-92e5-914f6ef33194"  width="70%" alt="Enable VLAN IP Address" />
</p>

---

### 12. Connect the Laptop with an Ethernet Cable to the Cisco Switch

<p align="center">
<img src="https://github.com/user-attachments/assets/aeefc812-8e11-457e-87d3-dd55e8fd362d" width="70%" alt="Connect Laptop via Ethernet Cable" />
</p>

---

### 13. Verify Physical Port Connection

**Instructions:**
- On the Cisco switch CLI, type the following command:
  ```
  show interfaces status
  ```
- Look for the port you connected (e.g., `Gi0/7`).  
- The **Status** column should display `connected`.  
- If it shows `notconnect`, check the cable or try another port.

<p align="center">
<img src="https://github.com/user-attachments/assets/ce67a050-3ce5-417b-8c6b-9f6cab816a85"  width="70%" alt="Check Port Connection with show interfaces status" />
</p>

---

### 14. Ethernet Connected (No Internet Access)

<p align="center">
<img src="https://github.com/user-attachments/assets/47542a33-b0b1-4caa-b863-bee1865bf6a6" width="70%" alt="Ethernet Connected but No Internet" />
</p>

---

### 15. Open Internet Adapter Settings

<p align="center">
<img src="https://github.com/user-attachments/assets/89674b19-dbd3-43d2-81f7-016ded705da2" width="70%" alt="Open Adapter Settings" /> 
</p>

---

### 16. Setting Internet Protocol IPv4

<p align="center">
<img src="https://github.com/user-attachments/assets/6e5c13c9-caee-44e9-a434-38336a4af410" width="70%" alt="Set IPv4 Properties" />
</p>

---

### 17. Open Command Prompt and Ping

<p align="center">
<img src="https://github.com/user-attachments/assets/74682236-8f1a-4c1f-a50e-345293b70420" width="70%" alt="Ping Test" />
</p>
