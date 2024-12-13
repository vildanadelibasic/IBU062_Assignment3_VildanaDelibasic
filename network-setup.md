# Network Setup

## Devices and IP Addresses

### 1. Router

- **Model**: Cisco 1941
- **IP Address Configuration**:
  - **Interface G0/0 (connected to Switch 1)**: 168.90.0.1/16
  - **Interface G0/1 (connected to Switch 2)**: 210.3.14.1/24
- **DHCP Server Configuration**: Enabled for both networks

### 2. Switches

- **Switch 1** (connected to network 168.90.0.0):
  - **Model**: Cisco Catalyst 2960
  - **IP Address**: None (Layer 2 Switch, no IP needed for basic operation)
- **Switch 2** (connected to network 210.3.14.0):
  - **Model**: Cisco Catalyst 2960
  - **IP Address**: None (Layer 2 Switch, no IP needed for basic operation)

### 3. PCs, Laptops, and Servers

#### Devices on **Switch 1** (Network 168.90.0.0):

- **PC 1**:
  - **Assigned IP Address**: 168.90.0.2 (IP assigned by DHCP)
- **PC 2**:
  - **Assigned IP Address**: 168.90.0.5 (IP assigned by DHCP)
- **PC 3**:
  - **Assigned IP Address**: 168.90.0.6 (IP assigned by DHCP)
- **Laptop**:
  - **Assigned IP Address**: 168.90.0.3 (IP assigned by DHCP)
- **Server**:
  - **Assigned IP Address**: 168.90.0.4 (IP assigned by DHCP)

#### Devices on **Switch 2** (Network 210.3.14.0):

- **PC 4**:
  - **Assigned IP Address**: 210.3.14.3 (IP assigned by DHCP)
- **PC 5**:
  - **Assigned IP Address**: 210.3.14.5 (IP assigned by DHCP)
- **Server 2**:
  - **Assigned IP Address**: 210.3.14.2 (IP assigned by DHCP)
- **Server 3**:
  - **Assigned IP Address**: 210.3.14.4 (IP assigned by DHCP)

#### Steps to Set Up DHCP:

1. **Access Router's Command Line Interface (CLI)**:

   - Enter **privileged exec mode**:
     ```bash
     enable
     ```
   - Enter **global configuration mode**:
     ```bash
     configure terminal
     ```

2. **Create DHCP Pool for the First Network (168.90.0.0/16)**:

   - Define the DHCP pool and network address:
     ```bash
     ip dhcp pool Pool1
     network 168.90.0.0 255.255.0.0
     ```
   - Set the **default-router** (gateway) IP for devices in this network:
     ```bash
     default-router 168.90.0.1
     ```
   - Set the **DNS server** address:
     ```bash
     dns-server 168.90.0.1
     ```

3. **Create DHCP Pool for the Second Network (210.3.14.0/24)**:

   - Define the DHCP pool and network address:
     ```bash
     ip dhcp pool Pool2
     network 210.3.14.0 255.255.255.0
     ```
   - Set the **default-router** (gateway) IP for devices in this network:
     ```bash
     default-router 210.3.14.1
     ```
   - Set the **DNS server** address:
     ```bash
     dns-server 210.3.14.1
     ```

4. **Exclude Static IP Addresses from DHCP Pool**:

   - Exclude a range of IP addresses that are reserved for **static IPs** (such as router, servers, etc.):
     ```bash
     ip dhcp excluded-address 168.90.0.1 168.90.0.10
     ip dhcp excluded-address 210.3.14.1 210.3.14.10
     ```
     These commands prevent the DHCP server from assigning IP addresses in these ranges to any device.

5. **Save Configuration**:
   - After configuring DHCP, save the changes to ensure they persist after a reboot:
     ```bash
     end
     write memory
     ```

#### Summary of the DHCP Configuration:

- **First Network (168.90.0.0/16)**:

  - DHCP Pool: **Pool1**
  - Network Address: **168.90.0.0 255.255.0.0**
  - Default Router: **168.90.0.1**
  - DNS Server: **168.90.0.1**
  - Excluded Addresses: **168.90.0.1 - 168.90.0.10** (Reserved for static IPs)

- **Second Network (210.3.14.0/24)**:
  - DHCP Pool: **Pool2**
  - Network Address: **210.3.14.0 255.255.255.0**
  - Default Router: **210.3.14.1**
  - DNS Server: **210.3.14.1**
  - Excluded Addresses: **210.3.14.1 - 210.3.14.10** (Reserved for static IPs)
