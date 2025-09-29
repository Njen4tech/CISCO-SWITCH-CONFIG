# Welcome to CISCO Switch setup!

This is your README. Readme files are where you can communicate what your project is and how to use it.

Write your name on line 6, save it, and then head back to GitHub Desktop.

---

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

## 🔧 CCL Walk-through (Reordered & Scanned)

### 1. Turn on the Device

**Instructions:**
- Plug the power cable into the rear I/O port of the Cisco switch.
- Plug the other end into a power outlet.
- Confirm that the switch powers on by observing the LED indicators.

<p align="center">
<img src="https://github.com/user-attachments/assets/eea95b75-3043-4b70-834e-966a9909307c" width="70%" alt="Cisco Console Port / Rear I-O" />
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
<img src="https://github.com/user-attachments/assets/be75c2a0-ab57-46e0-9ce6-254a151dcceb" width="70%" alt="PuTTY Serial Connection" />
</p>


---

### 4. Change Default Hostname in Terminal

**Instructions:**
- In the terminal, type `enable` and press Enter.
- Then enter `configure terminal`.
- Use `hostname <your_hostname>` to rename the switch.

```bash
enable
configure terminal
hostname MySwitch
```

<p align="center">
<img src="https://github.com/user-attachments/assets/e38066b6-9dc5-485b-a29b-45f6c52dc1ab" width="70%" alt="Change Host" />
</p>


---

### 5. Enter Cisco Switch CLI

**Instructions:**
- At the terminal prompt, press Enter to access the switch CLI.
- Enter privileged EXEC mode by typing `enable`.

```bash
enable
```

<p align="center">
<img src="https://github.com/user-attachments/assets/6c3227ff-e60c-4c19-8f04-5a2d5ffdb1e7"  width="70%" alt="Switch CLI" />
</p>


---

### 6. Configure and Assign a VLAN Interface (SVI)

**Instructions:**
- In global config mode, type:
```bash
interface vlan 10
ip address 10.10.10.1 255.255.255.0
no shutdown
```


---

### 7. Final Setup Overview (create VLANs and SVIs)

**Instructions:**
- Repeat the following steps for each VLAN you need (example shows VLAN 10 and VLAN 20):
```bash
vlan 10
name VLAN10
exit

interface vlan 10
ip address 10.10.10.1 255.255.255.0
no shutdown
exit

vlan 20
name VLAN20
exit

interface vlan 20
ip address 10.10.20.1 255.255.255.0
no shutdown
exit
```

<p align="center">
<img src="https://github.com/user-attachments/assets/01a4ecd4-9de1-438e-89e9-8e82c8a9c54c" width="70%" alt="Overview: VLANs and SVIs" />
</p>


---

### 8. View VLAN List

**Instructions:**
- Type the following command to display the VLANs:
```bash
show vlan brief
```

<p align="center">
<img src="https://github.com/user-attachments/assets/fcd637d7-4f7c-4e76-8325-e0c49e40dff5" width="70%" alt="VLAN Brief Screenshot" />
</p>


---

### 9. Save the Configuration

**Instructions:**
- Save the running configuration to NVRAM using:
```bash
write memory
```

<p align="center">
<img src="https://github.com/user-attachments/assets/296ca1c1-1f75-4a49-a899-1d2288124299" width="70%" alt="Saving Configuration" />
</p>


---

### 10. Select Ports to Enable

**Instructions:**
- Use the following command to configure access ports:
```bash
interface range GigabitEthernet0/1-12, GigabitEthernet0/13-24
switchport mode access
switchport access vlan 10
no shutdown
exit
```
<p align="center">
<img src="https://github.com/user-attachments/assets/63ac162e-c484-45e0-95d9-eea202db0a9a" width="70%" alt="Final Cisco Switch Setup Overview" />
</p>

---

### 11. Enable IP Address for the Selected VLAN

**Instructions:**
- Reconfirm the VLAN interface IP setup:
```bash
interface vlan 10
ip address 10.10.10.1 255.255.255.0
no shutdown
```

<p align="center">
<img src="https://github.com/user-attachments/assets/a102d889-bee4-4ec5-957d-5091e8618150"  width="70%" alt="VLAN IP Configuration" />
</p>


---

### 12. Connect the Laptop with an Ethernet Cable to the Cisco Switch

**Instructions:**
- Use an Ethernet cable to connect your laptop to one of the active switch ports.

<p align="center">
<img src="https://github.com/user-attachments/assets/aeefc812-8e11-457e-87d3-dd55e8fd362d" width="70%" alt="Connect Laptop via Ethernet Cable" />
</p>


---

### 13. Verify Physical Port Connection

**Instructions:**
- On the Cisco switch CLI, type the following command:
```bash
show interfaces status
```
- Look for the port you connected (e.g., `Gi0/7`).
- The **Status** column should display `connected`.
- If it shows `notconnect`, check the cable or try another port.

<p align="center">
<img src="https://github.com/user-attachments/assets/05fdd924-d743-4c18-9167-d7ef8280d3cb" width="70%" alt=" show interfaces status output (port connection)" />
</p>


---

### 14. Ethernet Connected (No Internet Access)

**Instructions:**
- The laptop NIC should show **Connected** but **No Internet** (since no upstream router is set).

<p align="center">
<img src="https://github.com/user-attachments/assets/47542a33-b0b1-4caa-b863-bee1865bf6a6" width="70%" alt="Ethernet Connected but No Internet" />
</p>


---

### 15. Open Internet Adapter Settings

**Instructions:**
- Go to **Network & Internet Settings → Change adapter options**.
- Right-click **Ethernet → Properties**.

<p align="center">
<img src="https://github.com/user-attachments/assets/89674b19-dbd3-43d2-81f7-016ded705da2" width="70%" alt="Network Adapter Settings" /> 
</p>


---

### 16. Set IPv4 Address Manually

**Instructions:**
- Configure the adapter with an IP in the same subnet as the switch VLAN.  
  Example:
  - IP address: `10.10.10.1`
  - Subnet mask: `255.255.255.0`
  - Default gateway: `10.10.10.5`

<p align="center">
<img src="https://github.com/user-attachments/assets/3e4b7b5b-aba7-4ebf-b2f3-08edf0ef3585"  width="70%" alt="IPv4 Settings" />
</p>


---

### 17. Test Connectivity with Ping

**Instructions:**
- Open Command Prompt and type:
```bash
ping 10.10.10.5
```
- You should receive replies if everything is configured correctly.

<p align="center">
<img src="https://github.com/user-attachments/assets/74682236-8f1a-4c1f-a50e-345293b70420" width="70%" alt="Ping Test" />
</p>

