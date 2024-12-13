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
- **Laptop**:
  - **Assigned IP Address**: 168.90.0.3 (IP assigned by DHCP)
- **Server**:
  - **Assigned IP Address**: 168.90.0.4 (IP assigned by DHCP)

#### Devices on **Switch 2** (Network 210.3.14.0):

- **PC 3**:
  - **Assigned IP Address**: 210.3.14.3 (IP assigned by DHCP)
- **Server 2**:

  - **Assigned IP Address**: 210.3.14.2 (IP assigned by DHCP)

- **Server 3**:
  - **Assigned IP Address**: 210.3.14.4 (IP assigned by DHCP)
