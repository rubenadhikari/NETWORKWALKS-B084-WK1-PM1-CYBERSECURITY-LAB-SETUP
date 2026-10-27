# Network Walks - Week 1 | PM1: Cybersecurity Lab Setup - Ruben Adhikari

## Overview

This project documents my Week 1, Project Module 1 lab setup for the Network Walks cybersecurity learning program. The lab uses Oracle VirtualBox to run Kali Linux on a Windows 11 host.

The objective was to configure a virtual lab environment, establish network connectivity, enable host-to-guest file sharing, and verify that the environment was ready for further cybersecurity exercises.

## Objectives

- Install and configure Oracle VirtualBox and Kali Linux.
- Configure the required IPv4 address and subnet.
- Verify the default gateway and network routing.
- Test internet connectivity and DNS resolution.
- Configure the VirtualBox NAT Network.
- Set up a shared folder between Windows and Kali Linux.
- Enable and test shared clipboard and drag-and-drop.
- Create a virtual machine snapshot.
- Document the configuration and verification results.

## Lab Environment

| Component | Configuration |
|---|---|
| Host operating system | Windows 11 |
| Virtualization software | Oracle VirtualBox |
| Guest operating system | Kali Linux |
| Network interface | `eth0` |
| Kali IPv4 address | `10.0.0.2/24` |
| NAT Network subnet | `10.0.0.0/24` |
| Default gateway | `10.0.0.1` |
| Shared folder | Windows Downloads folder |

## Network Configuration and Verification

### 1. IPv4 Configuration

The Kali Linux network interface was configured with the required address:

`10.0.0.2/24`

The configuration was verified using:

```bash
ip -br addr
```
<img width="1917" height="1195" alt="01-ip-configuration" src="https://github.com/user-attachments/assets/270374f7-a424-4cb3-9c6d-8035e9f03bf3" />

### 2. Routing Table

The routing table was checked using:

```bash
ip route
```
<img width="1917" height="1197" alt="02-routing-table" src="https://github.com/user-attachments/assets/2f059843-5c18-41ff-a9b2-d36615c5b163" />

The output showed a default route through `10.0.0.1` and a connected route for the `10.0.0.0/24` subnet.

### 3. DNS Resolution

DNS resolution and connectivity to a domain name were tested with:

```bash
ping -c 4 google.com
```
<img width="1907" height="1197" alt="03-internet-and-dns" src="https://github.com/user-attachments/assets/7128f676-748a-4880-a620-c56d91c3b021" />

The domain resolved successfully, and the test received four replies with 0% packet loss.

These results confirmed that IP connectivity and DNS resolution were working at the time of testing.

## Troubleshooting

During network configuration, I encountered an issue with the expected IP configuration. I followed the troubleshooting instruction provided in the lab material and ran:

```bash
sudo nmcli connection modify "Wired connection 1" ipv4.dad-timeout 0
```

This changes the NetworkManager connection's duplicate-address-detection timeout setting. After applying the documented fix, I verified the IP address, routing table, and network connectivity.

## VirtualBox Configuration

The following configuration items were completed:

- Configured the VM to use the NAT Network.
- Verified the `10.0.0.0/24` subnet.
  <img width="1917" height="1192" alt="04-nat-network" src="https://github.com/user-attachments/assets/5abcb777-9040-4ad1-bec2-8660da8959b5" />
- Configured a shared folder pointing to the Windows Downloads folder.
- Enabled Auto-mount and Make Permanent for the shared folder.
- Enabled Shared Clipboard and Drag'n'Drop in Bidirectional mode.
  <img width="970" height="651" alt="06-clipboard-dragdrop" src="https://github.com/user-attachments/assets/92b18d70-5394-4a58-9782-23972443e227" />
- Configured and Tested shared-folder access, clipboard sharing, and drag-and-drop.
  <img width="970" height="642" alt="07-shared-folder" src="https://github.com/user-attachments/assets/5654a8f0-6de1-4665-b209-ce5961000ac3" />
- Created a VM snapshot.
  <img width="1261" height="732" alt="08-vm-snapshot" src="https://github.com/user-attachments/assets/bd49965d-57f6-444f-ac4d-a95ac239dec9" />


## Evidence and Screenshots

Screenshots documenting the lab configuration and tests are included in the `WK1/` directory.

| Screenshot | Description |
|---|---|
| `01-ip-configuration.png` | Kali Linux IP address |
| `02-routing-table.png` | Default gateway and routing table |
| `03-internet-and-dns.png` | Connectivity and DNS tests |
| `04-nat-network.png` | NAT Network configuration |
| `05-vm-network-adapter.png` | VirtualBox network adapter |
| `06-clipboard-dragdrop.png` | Clipboard and drag-and-drop settings |
| `07-shared-folder.png` | Shared folder configuration |
| `08-vm-snapshot.png` | Virtual machine snapshot |

## Learning Outcomes

Through this exercise, I practiced:

- Basic Linux network inspection and troubleshooting.
- IPv4 addressing and subnet notation.
- Default gateways and routing tables.
- Testing connectivity and DNS resolution.
- Configuring NAT-based virtual networking.
- Sharing files between a Windows host and a Kali Linux guest.
- Using VM snapshots to preserve a working lab state.
- Documenting technical work with reproducible commands and screenshots.

## Conclusion

The Kali Linux virtual lab was configured and its network connectivity was verified. The shared folder, clipboard, and drag-and-drop features were also tested. The environment is ready for the next stage of cybersecurity learning and practical network-analysis exercises.

