# NEXTGEN_ARGENTINA_PRO

## Table of Contents

- [Fabric Switches and Management IP](#fabric-switches-and-management-ip)
  - [Fabric Switches with inband Management IP](#fabric-switches-with-inband-management-ip)
- [Fabric Topology](#fabric-topology)
- [Fabric IP Allocation](#fabric-ip-allocation)
  - [Fabric Point-To-Point Links](#fabric-point-to-point-links)
  - [Point-To-Point Links Node Allocation](#point-to-point-links-node-allocation)
  - [Loopback Interfaces (BGP EVPN Peering)](#loopback-interfaces-bgp-evpn-peering)
  - [Loopback0 Interfaces Node Allocation](#loopback0-interfaces-node-allocation)
  - [VTEP Loopback VXLAN Tunnel Source Interfaces (VTEPs Only)](#vtep-loopback-vxlan-tunnel-source-interfaces-vteps-only)
  - [VTEP Loopback Node allocation](#vtep-loopback-node-allocation)

## Fabric Switches and Management IP

| POD | Type | Node | Management IP | Platform | Provisioned in CloudVision | Serial Number |
| --- | ---- | ---- | ------------- | -------- | -------------------------- | ------------- |
| NEXTGEN_ARGENTINA_PRO_DC1 | l3leaf | ARI-BL-301-MTZ | 192.168.0.100/24 | 7050X3 | Provisioned | - |
| NEXTGEN_ARGENTINA_PRO_DC1 | l3leaf | ARI-BL-302-MTZ | 192.168.0.101/24 | 7050X3 | Provisioned | - |
| NEXTGEN_ARGENTINA_PRO_DC2 | l3leaf | ARI-BL-401-SKY | 192.168.0.200/24 | 7050X3 | Provisioned | - |
| NEXTGEN_ARGENTINA_PRO_DC2 | l3leaf | ARI-BL-402-SKY | 192.168.0.201/24 | 7050X3 | Provisioned | - |
| NEXTGEN_ARGENTINA_PRO_DC1 | l3leaf | ARI-CL-301-MTZ | 192.168.0.12/24 | 7050X3 | Provisioned | - |
| NEXTGEN_ARGENTINA_PRO_DC1 | l3leaf | ARI-CL-302-MTZ | 192.168.0.13/24 | 7050X3 | Provisioned | - |
| NEXTGEN_ARGENTINA_PRO_DC1 | l3leaf | ARI-CL-303-MTZ | 192.168.0.14/24 | 7050X3 | Provisioned | - |
| NEXTGEN_ARGENTINA_PRO_DC1 | l3leaf | ARI-CL-304-MTZ | 192.168.0.15/24 | 7050X3 | Provisioned | - |
| NEXTGEN_ARGENTINA_PRO_DC2 | l3leaf | ARI-CL-401-SKY | 192.168.0.122/24 | 7050X3 | Provisioned | - |
| NEXTGEN_ARGENTINA_PRO_DC2 | l3leaf | ARI-CL-402-SKY | 192.168.0.123/24 | 7050X3 | Provisioned | - |
| NEXTGEN_ARGENTINA_PRO_DC2 | l3leaf | ARI-CL-403-SKY | 192.168.0.124/24 | 7050X3 | Provisioned | - |
| NEXTGEN_ARGENTINA_PRO_DC2 | l3leaf | ARI-CL-404-SKY | 192.168.0.125/24 | 7050X3 | Provisioned | - |
| NEXTGEN_ARGENTINA_PRO_DC1 | spine | ARI-SP-301-MTZ | 192.168.0.10/24 | 7260CX3 | Provisioned | - |
| NEXTGEN_ARGENTINA_PRO_DC1 | spine | ARI-SP-302-MTZ | 192.168.0.11/24 | 7260CX3 | Provisioned | - |
| NEXTGEN_ARGENTINA_PRO_DC2 | spine | ARI-SP-401-SKY | 192.168.0.20/24 | 7260CX3 | Provisioned | - |
| NEXTGEN_ARGENTINA_PRO_DC2 | spine | ARI-SP-402-SKY | 192.168.0.21/24 | 7260CX3 | Provisioned | - |

> Provision status is based on Ansible inventory declaration and do not represent real status from CloudVision.

### Fabric Switches with inband Management IP

| POD | Type | Node | Management IP | Inband Interface |
| --- | ---- | ---- | ------------- | ---------------- |

## Fabric Topology

| Type | Node | Node Interface | Peer Type | Peer Node | Peer Interface |
| ---- | ---- | -------------- | --------- | ----------| -------------- |
| l3leaf | ARI-BL-301-MTZ | Ethernet2 | spine | ARI-SP-301-MTZ | Ethernet7 |
| l3leaf | ARI-BL-301-MTZ | Ethernet3 | spine | ARI-SP-302-MTZ | Ethernet7 |
| l3leaf | ARI-BL-301-MTZ | Ethernet33 | l3leaf | ARI-BL-401-SKY | Ethernet33 |
| l3leaf | ARI-BL-301-MTZ | Ethernet34 | l3leaf | ARI-BL-402-SKY | Ethernet34 |
| l3leaf | ARI-BL-302-MTZ | Ethernet2 | spine | ARI-SP-301-MTZ | Ethernet8 |
| l3leaf | ARI-BL-302-MTZ | Ethernet3 | spine | ARI-SP-302-MTZ | Ethernet8 |
| l3leaf | ARI-BL-302-MTZ | Ethernet33 | l3leaf | ARI-BL-402-SKY | Ethernet33 |
| l3leaf | ARI-BL-302-MTZ | Ethernet34 | l3leaf | ARI-BL-401-SKY | Ethernet34 |
| l3leaf | ARI-BL-401-SKY | Ethernet2 | spine | ARI-SP-401-SKY | Ethernet7 |
| l3leaf | ARI-BL-401-SKY | Ethernet3 | spine | ARI-SP-402-SKY | Ethernet7 |
| l3leaf | ARI-BL-402-SKY | Ethernet2 | spine | ARI-SP-401-SKY | Ethernet8 |
| l3leaf | ARI-BL-402-SKY | Ethernet3 | spine | ARI-SP-402-SKY | Ethernet8 |
| l3leaf | ARI-CL-301-MTZ | Ethernet2 | spine | ARI-SP-301-MTZ | Ethernet2 |
| l3leaf | ARI-CL-301-MTZ | Ethernet3 | spine | ARI-SP-302-MTZ | Ethernet2 |
| l3leaf | ARI-CL-302-MTZ | Ethernet2 | spine | ARI-SP-301-MTZ | Ethernet3 |
| l3leaf | ARI-CL-302-MTZ | Ethernet3 | spine | ARI-SP-302-MTZ | Ethernet3 |
| l3leaf | ARI-CL-303-MTZ | Ethernet2 | spine | ARI-SP-301-MTZ | Ethernet4 |
| l3leaf | ARI-CL-303-MTZ | Ethernet3 | spine | ARI-SP-302-MTZ | Ethernet4 |
| l3leaf | ARI-CL-304-MTZ | Ethernet2 | spine | ARI-SP-301-MTZ | Ethernet5 |
| l3leaf | ARI-CL-304-MTZ | Ethernet3 | spine | ARI-SP-302-MTZ | Ethernet5 |
| l3leaf | ARI-CL-401-SKY | Ethernet2 | spine | ARI-SP-401-SKY | Ethernet2 |
| l3leaf | ARI-CL-401-SKY | Ethernet3 | spine | ARI-SP-402-SKY | Ethernet2 |
| l3leaf | ARI-CL-402-SKY | Ethernet2 | spine | ARI-SP-401-SKY | Ethernet3 |
| l3leaf | ARI-CL-402-SKY | Ethernet3 | spine | ARI-SP-402-SKY | Ethernet3 |
| l3leaf | ARI-CL-403-SKY | Ethernet2 | spine | ARI-SP-401-SKY | Ethernet4 |
| l3leaf | ARI-CL-403-SKY | Ethernet3 | spine | ARI-SP-402-SKY | Ethernet4 |
| l3leaf | ARI-CL-404-SKY | Ethernet2 | spine | ARI-SP-401-SKY | Ethernet5 |
| l3leaf | ARI-CL-404-SKY | Ethernet3 | spine | ARI-SP-402-SKY | Ethernet5 |

## Fabric IP Allocation

### Fabric Point-To-Point Links

| Uplink IPv4 Pool | Available Addresses | Assigned addresses | Assigned Address % |
| ---------------- | ------------------- | ------------------ | ------------------ |
| 10.110.8.0/23 | 512 | 24 | 4.69 % |
| 10.111.8.0/23 | 512 | 24 | 4.69 % |

### Point-To-Point Links Node Allocation

| Node | Node Interface | Node IP Address | Peer Node | Peer Interface | Peer IP Address |
| ---- | -------------- | --------------- | --------- | -------------- | --------------- |
| ARI-BL-301-MTZ | Ethernet2 | 10.110.8.241/31 | ARI-SP-301-MTZ | Ethernet7 | 10.110.8.240/31 |
| ARI-BL-301-MTZ | Ethernet3 | 10.110.8.243/31 | ARI-SP-302-MTZ | Ethernet7 | 10.110.8.242/31 |
| ARI-BL-301-MTZ | Ethernet33 | 10.110.1.0/31 | ARI-BL-401-SKY | Ethernet33 | 10.110.1.1/31 |
| ARI-BL-301-MTZ | Ethernet34 | 10.110.1.2/31 | ARI-BL-402-SKY | Ethernet34 | 10.110.1.3/31 |
| ARI-BL-302-MTZ | Ethernet2 | 10.110.8.253/31 | ARI-SP-301-MTZ | Ethernet8 | 10.110.8.252/31 |
| ARI-BL-302-MTZ | Ethernet3 | 10.110.8.255/31 | ARI-SP-302-MTZ | Ethernet8 | 10.110.8.254/31 |
| ARI-BL-302-MTZ | Ethernet33 | 10.110.1.4/31 | ARI-BL-402-SKY | Ethernet33 | 10.110.1.5/31 |
| ARI-BL-302-MTZ | Ethernet34 | 10.110.1.6/31 | ARI-BL-401-SKY | Ethernet34 | 10.110.1.7/31 |
| ARI-BL-401-SKY | Ethernet2 | 10.111.8.241/31 | ARI-SP-401-SKY | Ethernet7 | 10.111.8.240/31 |
| ARI-BL-401-SKY | Ethernet3 | 10.111.8.243/31 | ARI-SP-402-SKY | Ethernet7 | 10.111.8.242/31 |
| ARI-BL-402-SKY | Ethernet2 | 10.111.8.253/31 | ARI-SP-401-SKY | Ethernet8 | 10.111.8.252/31 |
| ARI-BL-402-SKY | Ethernet3 | 10.111.8.255/31 | ARI-SP-402-SKY | Ethernet8 | 10.111.8.254/31 |
| ARI-CL-301-MTZ | Ethernet2 | 10.110.8.1/31 | ARI-SP-301-MTZ | Ethernet2 | 10.110.8.0/31 |
| ARI-CL-301-MTZ | Ethernet3 | 10.110.8.3/31 | ARI-SP-302-MTZ | Ethernet2 | 10.110.8.2/31 |
| ARI-CL-302-MTZ | Ethernet2 | 10.110.8.13/31 | ARI-SP-301-MTZ | Ethernet3 | 10.110.8.12/31 |
| ARI-CL-302-MTZ | Ethernet3 | 10.110.8.15/31 | ARI-SP-302-MTZ | Ethernet3 | 10.110.8.14/31 |
| ARI-CL-303-MTZ | Ethernet2 | 10.110.8.25/31 | ARI-SP-301-MTZ | Ethernet4 | 10.110.8.24/31 |
| ARI-CL-303-MTZ | Ethernet3 | 10.110.8.27/31 | ARI-SP-302-MTZ | Ethernet4 | 10.110.8.26/31 |
| ARI-CL-304-MTZ | Ethernet2 | 10.110.8.37/31 | ARI-SP-301-MTZ | Ethernet5 | 10.110.8.36/31 |
| ARI-CL-304-MTZ | Ethernet3 | 10.110.8.39/31 | ARI-SP-302-MTZ | Ethernet5 | 10.110.8.38/31 |
| ARI-CL-401-SKY | Ethernet2 | 10.111.8.1/31 | ARI-SP-401-SKY | Ethernet2 | 10.111.8.0/31 |
| ARI-CL-401-SKY | Ethernet3 | 10.111.8.3/31 | ARI-SP-402-SKY | Ethernet2 | 10.111.8.2/31 |
| ARI-CL-402-SKY | Ethernet2 | 10.111.8.13/31 | ARI-SP-401-SKY | Ethernet3 | 10.111.8.12/31 |
| ARI-CL-402-SKY | Ethernet3 | 10.111.8.15/31 | ARI-SP-402-SKY | Ethernet3 | 10.111.8.14/31 |
| ARI-CL-403-SKY | Ethernet2 | 10.111.8.25/31 | ARI-SP-401-SKY | Ethernet4 | 10.111.8.24/31 |
| ARI-CL-403-SKY | Ethernet3 | 10.111.8.27/31 | ARI-SP-402-SKY | Ethernet4 | 10.111.8.26/31 |
| ARI-CL-404-SKY | Ethernet2 | 10.111.8.37/31 | ARI-SP-401-SKY | Ethernet5 | 10.111.8.36/31 |
| ARI-CL-404-SKY | Ethernet3 | 10.111.8.39/31 | ARI-SP-402-SKY | Ethernet5 | 10.111.8.38/31 |

### Loopback Interfaces (BGP EVPN Peering)

| Loopback Pool | Available Addresses | Assigned addresses | Assigned Address % |
| ------------- | ------------------- | ------------------ | ------------------ |
| 10.110.5.0/24 | 256 | 8 | 3.13 % |
| 10.111.5.0/24 | 256 | 8 | 3.13 % |

### Loopback0 Interfaces Node Allocation

| POD | Node | Loopback0 |
| --- | ---- | --------- |
| NEXTGEN_ARGENTINA_PRO_DC1 | ARI-BL-301-MTZ | 10.110.5.25/32 |
| NEXTGEN_ARGENTINA_PRO_DC1 | ARI-BL-302-MTZ | 10.110.5.26/32 |
| NEXTGEN_ARGENTINA_PRO_DC2 | ARI-BL-401-SKY | 10.111.5.25/32 |
| NEXTGEN_ARGENTINA_PRO_DC2 | ARI-BL-402-SKY | 10.111.5.26/32 |
| NEXTGEN_ARGENTINA_PRO_DC1 | ARI-CL-301-MTZ | 10.110.5.5/32 |
| NEXTGEN_ARGENTINA_PRO_DC1 | ARI-CL-302-MTZ | 10.110.5.6/32 |
| NEXTGEN_ARGENTINA_PRO_DC1 | ARI-CL-303-MTZ | 10.110.5.7/32 |
| NEXTGEN_ARGENTINA_PRO_DC1 | ARI-CL-304-MTZ | 10.110.5.8/32 |
| NEXTGEN_ARGENTINA_PRO_DC2 | ARI-CL-401-SKY | 10.111.5.5/32 |
| NEXTGEN_ARGENTINA_PRO_DC2 | ARI-CL-402-SKY | 10.111.5.6/32 |
| NEXTGEN_ARGENTINA_PRO_DC2 | ARI-CL-403-SKY | 10.111.5.7/32 |
| NEXTGEN_ARGENTINA_PRO_DC2 | ARI-CL-404-SKY | 10.111.5.8/32 |
| NEXTGEN_ARGENTINA_PRO_DC1 | ARI-SP-301-MTZ | 10.110.5.1/32 |
| NEXTGEN_ARGENTINA_PRO_DC1 | ARI-SP-302-MTZ | 10.110.5.2/32 |
| NEXTGEN_ARGENTINA_PRO_DC2 | ARI-SP-401-SKY | 10.111.5.1/32 |
| NEXTGEN_ARGENTINA_PRO_DC2 | ARI-SP-402-SKY | 10.111.5.2/32 |

### VTEP Loopback VXLAN Tunnel Source Interfaces (VTEPs Only)

| VTEP Loopback Pool | Available Addresses | Assigned addresses | Assigned Address % |
| ------------------ | ------------------- | ------------------ | ------------------ |
| 10.110.6.0/24 | 256 | 6 | 2.35 % |
| 10.111.6.0/24 | 256 | 6 | 2.35 % |

### VTEP Loopback Node allocation

| POD | Node | Loopback1 |
| --- | ---- | --------- |
| NEXTGEN_ARGENTINA_PRO_DC1 | ARI-BL-301-MTZ | 10.110.6.25/32 |
| NEXTGEN_ARGENTINA_PRO_DC1 | ARI-BL-302-MTZ | 10.110.6.26/32 |
| NEXTGEN_ARGENTINA_PRO_DC2 | ARI-BL-401-SKY | 10.111.6.25/32 |
| NEXTGEN_ARGENTINA_PRO_DC2 | ARI-BL-402-SKY | 10.111.6.26/32 |
| NEXTGEN_ARGENTINA_PRO_DC1 | ARI-CL-301-MTZ | 10.110.6.5/32 |
| NEXTGEN_ARGENTINA_PRO_DC1 | ARI-CL-302-MTZ | 10.110.6.6/32 |
| NEXTGEN_ARGENTINA_PRO_DC1 | ARI-CL-303-MTZ | 10.110.6.7/32 |
| NEXTGEN_ARGENTINA_PRO_DC1 | ARI-CL-304-MTZ | 10.110.6.8/32 |
| NEXTGEN_ARGENTINA_PRO_DC2 | ARI-CL-401-SKY | 10.111.6.5/32 |
| NEXTGEN_ARGENTINA_PRO_DC2 | ARI-CL-402-SKY | 10.111.6.6/32 |
| NEXTGEN_ARGENTINA_PRO_DC2 | ARI-CL-403-SKY | 10.111.6.7/32 |
| NEXTGEN_ARGENTINA_PRO_DC2 | ARI-CL-404-SKY | 10.111.6.8/32 |
