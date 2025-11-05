# ARI-BL-302-MTZ

## Table of Contents

- [Management](#management)
  - [Banner](#banner)
- [      WARNING: only authorized access is allowed.        #](#warning-only-authorized-access-is-allowed)
- [      AVISO: solo se permite acceso a autorizados.       #](#aviso-solo-se-permite-acceso-a-autorizados)
- [      Actions are monitored and recorded.                #](#actions-are-monitored-and-recorded)
- [      Sus acciones son monitoreadas y registradas.       #](#sus-acciones-son-monitoreadas-y-registradas)
    - [Management Interfaces](#management-interfaces)
    - [Clock Settings](#clock-settings)
    - [Management SSH](#management-ssh)
    - [Management Console](#management-console)
    - [Management API HTTP](#management-api-http)
  - [Authentication](#authentication)
    - [Local Users](#local-users)
    - [Enable Password](#enable-password)
    - [TACACS Servers](#tacacs-servers)
    - [IP TACACS Source Interfaces](#ip-tacacs-source-interfaces)
    - [AAA Server Groups](#aaa-server-groups)
    - [AAA Authentication](#aaa-authentication)
    - [AAA Authorization](#aaa-authorization)
  - [Management Security](#management-security)
    - [Management Security Summary](#management-security-summary)
    - [Management Security Device Configuration](#management-security-device-configuration)
  - [Monitoring](#monitoring)
    - [TerminAttr Daemon](#terminattr-daemon)
    - [Logging](#logging)
    - [SNMP](#snmp)
    - [SFlow](#sflow)
    - [Link Tracking](#link-tracking)
  - [LACP](#lacp)
    - [LACP Summary](#lacp-summary)
    - [LACP Device Configuration](#lacp-device-configuration)
  - [Spanning Tree](#spanning-tree)
    - [Spanning Tree Summary](#spanning-tree-summary)
    - [Spanning Tree Device Configuration](#spanning-tree-device-configuration)
  - [Internal VLAN Allocation Policy](#internal-vlan-allocation-policy)
    - [Internal VLAN Allocation Policy Summary](#internal-vlan-allocation-policy-summary)
    - [Internal VLAN Allocation Policy Device Configuration](#internal-vlan-allocation-policy-device-configuration)
  - [VLANs](#vlans)
    - [VLANs Summary](#vlans-summary)
    - [VLANs Device Configuration](#vlans-device-configuration)
  - [MAC Address Table](#mac-address-table)
    - [MAC Address Table Summary](#mac-address-table-summary)
    - [MAC Address Table Device Configuration](#mac-address-table-device-configuration)
  - [Interfaces](#interfaces)
    - [Switchport Default](#switchport-default)
    - [Interface Defaults](#interface-defaults)
    - [Ethernet Interfaces](#ethernet-interfaces)
    - [Loopback Interfaces](#loopback-interfaces)
    - [VLAN Interfaces](#vlan-interfaces)
    - [VXLAN Interface](#vxlan-interface)
  - [Routing](#routing)
    - [Service Routing Protocols Model](#service-routing-protocols-model)
    - [Virtual Router MAC Address](#virtual-router-mac-address)
    - [IP Routing](#ip-routing)
    - [IPv6 Routing](#ipv6-routing)
    - [Static Routes](#static-routes)
    - [ARP](#arp)
    - [Router BGP](#router-bgp)
  - [BFD](#bfd)
    - [Router BFD](#router-bfd)
  - [Multicast](#multicast)
    - [IP IGMP Snooping](#ip-igmp-snooping)
  - [Filters](#filters)
    - [Prefix-lists](#prefix-lists)
    - [Route-maps](#route-maps)
  - [ACL](#acl)
    - [Standard Access-lists](#standard-access-lists)
  - [VRF Instances](#vrf-instances)
    - [VRF Instances Summary](#vrf-instances-summary)
    - [VRF Instances Device Configuration](#vrf-instances-device-configuration)
  - [Virtual Source NAT](#virtual-source-nat)
    - [Virtual Source NAT Summary](#virtual-source-nat-summary)
    - [Virtual Source NAT Configuration](#virtual-source-nat-configuration)
  - [Errdisable](#errdisable)
    - [Errdisable Summary](#errdisable-summary)

## Management

### Banner

#### Login Banner

```text
#
                                   @
                                  @@
                                  @@@
                                  @@@@
                              @   @@@@@                      BANCO SANTANDER
                             @@@   @@@@@@            Grupo SANTANDER CENTRAL HISPANO
                             @@@@    @@@@@
                             @@@@@    @@@@@
                              @@@@@@   @@@@
                      @@@@@@    @@@@@@  @@@@@@@
                   @@@@@@@@@@    @@@@@@ @@@@@@@@@@@
                @@@@@@@@@@@@@@@    @@@@@@@@@@@@@@@@@@@
               @@@@@@@@@@@@@@@@@@   @@@@@@@@@@@@@@@@@@@
              @@@@@@@@@@@@@@@@@@@@ @@@@@@@@@@@@@@@@@@@@@
                @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
                  @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
                      @@@@@@@@@@@@@@@@@@@@@@@@@@

############################################################
#       WARNING: only authorized access is allowed.        #
#       AVISO: solo se permite acceso a autorizados.       #
#       Actions are monitored and recorded.                #
#       Sus acciones son monitoreadas y registradas.       #
############################################################
EOF
```

### Management Interfaces

#### Management Interfaces Summary

##### IPv4

| Management Interface | Description | Type | VRF | IP Address | Gateway |
| -------------------- | ----------- | ---- | --- | ---------- | ------- |
| Management0 | OOB_MANAGEMENT | oob | MGMT | 192.168.0.101/24 | 192.168.0.1 |

##### IPv6

| Management Interface | Description | Type | VRF | IPv6 Address | IPv6 Gateway |
| -------------------- | ----------- | ---- | --- | ------------ | ------------ |
| Management0 | OOB_MANAGEMENT | oob | MGMT | - | - |

#### Management Interfaces Device Configuration

```eos
!
interface Management0
   description OOB_MANAGEMENT
   no shutdown
   vrf MGMT
   ip address 192.168.0.101/24
```

### Clock Settings

#### Clock Timezone Settings

Clock Timezone is set to **America/Buenos_Aires**.

#### Clock Device Configuration

```eos
!
clock timezone America/Buenos_Aires
```

### Management SSH

#### VRFs

| VRF | Enabled | IPv4 ACL | IPv6 ACL |
| --- | ------- | -------- | -------- |
| MGMT | True | MGMT-ACL | - |
| VRF-NEXTGEN_DESARROLLO | False | - | - |
| VRF-NEXTGEN_DMZ_FRONT | False | - | - |
| VRF-NEXTGEN_DMZ_INT | False | - | - |
| VRF-NEXTGEN_MGMT | False | - | - |
| VRF-NEXTGEN_MGMT_DMZ | False | - | - |
| VRF-NEXTGEN_PRODUCCION | False | - | - |
| default | False | - | - |

#### Other SSH Settings

| Idle Timeout | Connection Limit | Max from a single Host | Ciphers | Key-exchange methods | MAC algorithms | Hostkey server algorithms |
| ------------ | ---------------- | ---------------------- | ------- | -------------------- | -------------- | ------------------------- |
| 15 | - | - | default | default | default | default |

#### Management SSH Device Configuration

```eos
!
management ssh
   ip access-group MGMT-ACL vrf MGMT in
   idle-timeout 15
   no shutdown
   !
   vrf default
      shutdown
   !
   vrf MGMT
      no shutdown
   !
   vrf VRF-NEXTGEN_DESARROLLO
      shutdown
   !
   vrf VRF-NEXTGEN_DMZ_FRONT
      shutdown
   !
   vrf VRF-NEXTGEN_DMZ_INT
      shutdown
   !
   vrf VRF-NEXTGEN_MGMT
      shutdown
   !
   vrf VRF-NEXTGEN_MGMT_DMZ
      shutdown
   !
   vrf VRF-NEXTGEN_PRODUCCION
      shutdown
```

### Management Console

#### Management Console Timeout

Management Console Timeout is set to **15** minutes.

#### Management Console Device Configuration

```eos
!
management console
   idle-timeout 15
```

### Management API HTTP

#### Management API HTTP Summary

| HTTP | HTTPS | UNIX-Socket | Default Services |
| ---- | ----- | ----------- | ---------------- |
| False | True | - | - |

#### Management API VRF Access

| VRF Name | IPv4 ACL | IPv6 ACL |
| -------- | -------- | -------- |
| MGMT | CVP-ACL | - |

#### Management API HTTP Device Configuration

```eos
!
management api http-commands
   protocol https
   no shutdown
   !
   vrf MGMT
      no shutdown
      ip access-group CVP-ACL
```

## Authentication

### Local Users

#### Local Users Summary

| User | Privilege | Role | Disabled | Shell |
| ---- | --------- | ---- | -------- | ----- |
| admin | 15 | network-admin | False | - |
| ansible | 15 | network-admin | False | - |
| arista | 15 | network-admin | False | - |
| cvpadmin | 15 | network-admin | False | - |
| marcelo | 15 | network-admin | False | - |

#### Local Users Device Configuration

```eos
!
username admin privilege 15 role network-admin secret sha512 <removed>
username ansible privilege 15 role network-admin secret sha512 <removed>
username arista privilege 15 role network-admin secret sha512 <removed>
username cvpadmin privilege 15 role network-admin secret sha512 <removed>
username marcelo privilege 15 role network-admin secret sha512 <removed>
```

### Enable Password

Enable password has been disabled

### TACACS Servers

#### TACACS Servers

| VRF | TACACS Servers | Single-Connection | Timeout |
| --- | -------------- | ----------------- | ------- |
| MGMT | 180.250.33.126 | False | - |
| MGMT | 180.250.33.127 | False | - |

#### TACACS Servers Device Configuration

```eos
!
tacacs-server host 180.250.33.126 vrf MGMT key 7 <removed>
tacacs-server host 180.250.33.127 vrf MGMT key 7 <removed>
```

### IP TACACS Source Interfaces

#### IP TACACS Source Interfaces

| VRF | Source Interface Name |
| --- | --------------- |
| MGMT | Management0 |

#### IP TACACS Source Interfaces Device Configuration

```eos
!
ip tacacs vrf MGMT source-interface Management0
```

### AAA Server Groups

#### AAA Server Groups Summary

| Server Group Name | Type  | VRF | IP address |
| ------------------| ----- | --- | ---------- |
| TacServer | tacacs+ | MGMT | 180.250.33.126 |
| TacServer | tacacs+ | MGMT | 180.250.33.127 |

#### AAA Server Groups Device Configuration

```eos
!
aaa group server tacacs+ TacServer
   server 180.250.33.126 vrf MGMT
   server 180.250.33.127 vrf MGMT
```

### AAA Authentication

#### AAA Authentication Summary

| Type | Sub-type | User Stores |
| ---- | -------- | ---------- |
| Login | default | local group tacacs+ |
| Login | console | local |

AAA Authentication on-failure log has been enabled

AAA Authentication on-success log has been enabled

#### AAA Authentication Device Configuration

```eos
aaa authentication login default local group tacacs+
aaa authentication login console local
aaa authentication policy on-failure log
aaa authentication policy on-success log
!
```

### AAA Authorization

#### AAA Authorization Summary

| Type | User Stores |
| ---- | ----------- |
| Exec | local group tacacs+ |

Authorization for configuration commands is disabled.

#### AAA Authorization Privilege Levels Summary

| Privilege Level | User Stores |
| --------------- | ----------- |
| 15 | local group tacacs+ |

#### AAA Authorization Device Configuration

```eos
aaa authorization exec default local group tacacs+
aaa authorization commands 15 default local group tacacs+
!
```

## Management Security

### Management Security Summary

| Settings | Value |
| -------- | ----- |
| Common password encryption key | True |

### Management Security Device Configuration

```eos
!
management security
   password encryption-key common
```

## Monitoring

### TerminAttr Daemon

#### TerminAttr Daemon Summary

| CV Compression | CloudVision Servers | VRF | Authentication | Smash Excludes | Ingest Exclude | Bypass AAA |
| -------------- | ------------------- | --- | -------------- | -------------- | -------------- | ---------- |
| gzip | 192.168.0.5:9910 | MGMT | token,/tmp/token | ale,flexCounter,hardware,kni,pulse,strata | /Sysdb/cell/1/agent,/Sysdb/cell/2/agent | True |

#### TerminAttr Daemon Device Configuration

```eos
!
daemon TerminAttr
   exec /usr/bin/TerminAttr -cvaddr=192.168.0.5:9910 -cvauth=token,/tmp/token -cvvrf=MGMT -disableaaa -smashexcludes=ale,flexCounter,hardware,kni,pulse,strata -ingestexclude=/Sysdb/cell/1/agent,/Sysdb/cell/2/agent -taillogs
   no shutdown
```

### Logging

#### Logging Servers and Features Summary

| Type | Level |
| -----| ----- |
| Console | notifications |
| Monitor | debugging |
| Buffer | notifications |
| Trap | debugging |

| Format Type | Setting |
| ----------- | ------- |
| Timestamp | high-resolution |
| Hostname | hostname |
| Sequence-numbers | false |
| RFC5424 | False |

| VRF | Source Interface |
| --- | ---------------- |
| - | Management0 |
| MGMT | Management0 |

| VRF | Hosts | Ports | Protocol | SSL-profile |
| --- | ----- | ----- | -------- | ----------- |
| MGMT | 10.200.251.15 | Default | UDP | - |
| MGMT | 10.206.16.75 | Default | UDP | - |

#### Logging Servers and Features Device Configuration

```eos
!
logging buffered 8000 notifications
logging trap debugging
logging console notifications
logging monitor debugging
logging vrf MGMT host 10.200.251.15
logging vrf MGMT host 10.206.16.75
logging format timestamp high-resolution
logging source-interface Management0
logging vrf MGMT source-interface Management0
```

### SNMP

#### SNMP Configuration Summary

| Contact | Location | SNMP Traps | State |
| ------- | -------- | ---------- | ----- |
| - | - | All | Enabled |
| - | - |  | Enabled |
| - | - | bridge arista-mac-age, bridge arista-mac-learn, bridge arista-mac-move, entity arista-ent-sensor-alarm | Disabled |

#### SNMP Local Interfaces

| Local Interface | VRF |
| --------------- | --- |
| Management0 | MGMT |

#### SNMP VRF Status

| VRF | Status |
| --- | ------ |
| MGMT | Enabled |

#### SNMP Hosts Configuration

| Host | VRF | Community | Username | Authentication level | SNMP Version |
| ---- |---- | --------- | -------- | -------------------- | ------------ |
| 10.40.3.124 | MGMT | - | itmetro | priv | 3 |
| 10.40.3.125 | MGMT | - | itmetro | priv | 3 |
| 10.40.3.126 | MGMT | - | itmetro | priv | 3 |
| 10.40.3.127 | MGMT | - | itmetro | priv | 3 |

#### SNMP Groups Configuration

| Group | SNMP Version | Authentication | Read | Write | Notify |
| ----- | ------------ | -------------- | ---- | ----- | ------ |
| ROGROUP | v3 | priv | - | - | - |

#### SNMP Users Configuration

| User | Group | Version | Authentication | Privacy | Remote Address | Remote Port | Engine ID |
| ---- | ----- | ------- | -------------- | ------- | -------------- | ----------- | --------- |
| itmetro | ROGROUP | v3 | sha | aes | - | - | - |

#### SNMP Device Configuration

```eos
!
snmp-server vrf MGMT local-interface Management0
snmp-server group ROGROUP v3 priv
snmp-server user itmetro ROGROUP v3 auth sha <removed> priv aes <removed>
snmp-server host 10.40.3.124 vrf MGMT version 3 priv itmetro
snmp-server host 10.40.3.125 vrf MGMT version 3 priv itmetro
snmp-server host 10.40.3.126 vrf MGMT version 3 priv itmetro
snmp-server host 10.40.3.127 vrf MGMT version 3 priv itmetro
snmp-server enable traps
no snmp-server enable traps bridge arista-mac-age
no snmp-server enable traps bridge arista-mac-learn
no snmp-server enable traps bridge arista-mac-move
no snmp-server enable traps entity arista-ent-sensor-alarm
snmp-server vrf MGMT
```

### SFlow

#### SFlow Summary

| VRF | SFlow Source | SFlow Destination | Port |
| --- | ------------ | ----------------- | ---- |
| default | - | 127.0.0.1 | 6343 |
| default | Loopback0 | - | - |

sFlow Sample Rate: 131072

sFlow is enabled.

sFlow is disabled on all interfaces by default.

#### SFlow Interfaces

| Interface | Ingress Enabled | Egress Enabled |
| --------- | --------------- | -------------- |
| Ethernet2 | True | - |
| Ethernet3 | True | - |
| Ethernet33 | True | - |
| Ethernet34 | True | - |

#### SFlow Device Configuration

```eos
!
sflow sample 131072
sflow destination 127.0.0.1
sflow source-interface Loopback0
sflow interface disable default
sflow run
```

### Link Tracking

#### Link Tracking Groups Summary

| Group Name | Minimum Links | Recovery Delay |
| ---------- | ------------- | -------------- |
| LT_GROUP1 | - | 300 |

#### Link Tracking Groups Device Configuration

```eos
!
link tracking group LT_GROUP1
   recovery delay 300
```

## LACP

### LACP Summary

| Port-id range | Rate-limit default | System-priority |
| ------------- | ------------------ | --------------- |
| 257 - 384 | - | - |

### LACP Device Configuration

```eos
!
lacp port-id range 257 384
```

## Spanning Tree

### Spanning Tree Summary

STP mode: **none**

### Spanning Tree Device Configuration

```eos
!
spanning-tree mode none
```

## Internal VLAN Allocation Policy

### Internal VLAN Allocation Policy Summary

| Policy Allocation | Range Beginning | Range Ending |
| ------------------| --------------- | ------------ |
| ascending | 3800 | 4000 |

### Internal VLAN Allocation Policy Device Configuration

```eos
!
vlan internal order ascending range 3800 4000
```

## VLANs

### VLANs Summary

| VLAN ID | Name | Trunk Groups |
| ------- | ---- | ------------ |
| 11 | NEXTGEN_MGMT_Vl_11 | - |
| 150 | NEXTGEN_PRODUCCION_Vl_150 | - |
| 177 | NEXTGEN_PRODUCCION_Vl_177 | - |
| 252 | NEXTGEN_MGMT_Vl_252 | - |
| 267 | NEXTGEN_MGMT_DMZ_Vl_267 | - |
| 301 | NEXTGEN_DESARROLLO_Vl_301 | - |
| 329 | NEXTGEN_DESARROLLO_Vl_329 | - |
| 450 | NEXTGEN_DMZ_INT_Vl_450 | - |
| 470 | NEXTGEN_DMZ_FRONT_Vl_470 | - |
| 473 | NEXTGEN_DMZ_INT_Vl_473 | - |

### VLANs Device Configuration

```eos
!
vlan 11
   name NEXTGEN_MGMT_Vl_11
!
vlan 150
   name NEXTGEN_PRODUCCION_Vl_150
!
vlan 177
   name NEXTGEN_PRODUCCION_Vl_177
!
vlan 252
   name NEXTGEN_MGMT_Vl_252
!
vlan 267
   name NEXTGEN_MGMT_DMZ_Vl_267
!
vlan 301
   name NEXTGEN_DESARROLLO_Vl_301
!
vlan 329
   name NEXTGEN_DESARROLLO_Vl_329
!
vlan 450
   name NEXTGEN_DMZ_INT_Vl_450
!
vlan 470
   name NEXTGEN_DMZ_FRONT_Vl_470
!
vlan 473
   name NEXTGEN_DMZ_INT_Vl_473
```

## MAC Address Table

### MAC Address Table Summary

- MAC address table entry maximum age: 1800 seconds

### MAC Address Table Device Configuration

```eos
!
mac address-table aging-time 1800
```

## Interfaces

### Switchport Default

#### Switchport Defaults Summary

- Default Switchport Mode: routed

#### Switchport Default Device Configuration

```eos
!
switchport default mode routed
```

### Interface Defaults

#### Interface Defaults Summary

- Default Ethernet Interface Shutdown: True

- Default Routed Interface MTU: 9100

#### Interface Defaults Device Configuration

```eos
!
interface defaults
   mtu 9100
   ethernet
      shutdown
```

### Ethernet Interfaces

#### Ethernet Interfaces Summary

##### L2

| Interface | Description | Mode | VLANs | Native VLAN | Trunk Group | Channel-Group |
| --------- | ----------- | ---- | ----- | ----------- | ----------- | ------------- |

*Inherited from Port-Channel Interface

##### Encapsulation Dot1q Interfaces

| Interface | Description | Vlan ID | Dot1q VLAN Tag | Dot1q Inner VLAN Tag |
| --------- | ----------- | ------- | -------------- | -------------------- |
| Port-Channel291.69 | ARI-MG-DL-01-02-MTZ - MLAG51 - Vlan69 | - | 69 | - |
| Port-Channel291.70 | ARI-MG-DL-01-02-MTZ - MLAG51 - Vlan70 | - | 70 | - |
| Port-Channel291.888 | ARI-MG-DL-01-02-MTZ - MLAG51 - Vlan888 - TEST NRFU | - | 888 | - |

##### Link Tracking Groups

| Interface | Group Name | Direction |
| --------- | ---------- | --------- |
| Ethernet2 | LT_GROUP1 | upstream |
| Ethernet3 | LT_GROUP1 | upstream |

##### IPv4

| Interface | Description | Channel Group | IP Address | VRF |  MTU | Shutdown | ACL In | ACL Out |
| --------- | ----------- | ------------- | ---------- | ----| ---- | -------- | ------ | ------- |
| Ethernet2 | P2P_ARI-SP-301-MTZ_Ethernet8 | - | 10.110.8.253/31 | default | 9214 | False | - | - |
| Ethernet3 | P2P_ARI-SP-302-MTZ_Ethernet8 | - | 10.110.8.255/31 | default | 9214 | False | - | - |
| Ethernet33 | P2P_ARI-BL-402-SKY_Ethernet33 | - | 10.110.1.4/31 | default | 9214 | False | - | - |
| Ethernet34 | P2P_ARI-BL-401-SKY_Ethernet34 | - | 10.110.1.6/31 | default | 9214 | False | - | - |
| Port-Channel291.69 | ARI-MG-DL-01-02-MTZ - MLAG51 - Vlan69 | - | 10.0.70.2/29 | VRF-NEXTGEN_MGMT | - | False | - | - |
| Port-Channel291.70 | ARI-MG-DL-01-02-MTZ - MLAG51 - Vlan70 | - | 10.0.70.10/29 | VRF-NEXTGEN_MGMT_DMZ | - | False | - | - |
| Port-Channel291.888 | ARI-MG-DL-01-02-MTZ - MLAG51 - Vlan888 - TEST NRFU | - | 100.64.88.1/24 | VRF-NEXTGEN_PRODUCCION | - | False | - | - |

##### VRRP Details

| Interface | VRRP-ID | Priority | Advertisement Interval | Preempt | Tracked Object Name(s) | Tracked Object Action(s) | IPv4 Virtual IPs | IPv4 VRRP Version | IPv6 Virtual IPs | Peer Authentication Mode |
| --------- | ------- | -------- | ---------------------- | --------| ---------------------- | ------------------------ | ---------------- | ----------------- | ---------------- | ------------------------ |
| Port-Channel291.69 | 69 | 200 | - | Enabled | - | - | 10.0.70.1 | 3 | - | - |
| Port-Channel291.70 | 70 | 200 | - | Enabled | - | - | 10.0.70.9 | 3 | - | - |

#### Ethernet Interfaces Device Configuration

```eos
!
interface Ethernet2
   description P2P_ARI-SP-301-MTZ_Ethernet8
   no shutdown
   mtu 9214
   speed forced 100g
   no switchport
   ip address 10.110.8.253/31
   sflow enable
   link tracking group LT_GROUP1 upstream
!
interface Ethernet3
   description P2P_ARI-SP-302-MTZ_Ethernet8
   no shutdown
   mtu 9214
   speed forced 100g
   no switchport
   ip address 10.110.8.255/31
   sflow enable
   link tracking group LT_GROUP1 upstream
!
interface Ethernet33
   description P2P_ARI-BL-402-SKY_Ethernet33
   no shutdown
   mtu 9214
   speed 10g
   no switchport
   ip address 10.110.1.4/31
   service-profile santander_trust_dscp
   sflow enable
!
interface Ethernet34
   description P2P_ARI-BL-401-SKY_Ethernet34
   no shutdown
   mtu 9214
   speed 10g
   no switchport
   ip address 10.110.1.6/31
   service-profile santander_trust_dscp
   sflow enable
!
interface Port-Channel291.69
   description ARI-MG-DL-01-02-MTZ - MLAG51 - Vlan69
   no shutdown
   encapsulation dot1q vlan 69
   vrf VRF-NEXTGEN_MGMT
   ip address 10.0.70.2/29
   vrrp 69 priority-level 200
   vrrp 69 ipv4 10.0.70.1
   vrrp 69 ipv4 version 3
!
interface Port-Channel291.70
   description ARI-MG-DL-01-02-MTZ - MLAG51 - Vlan70
   no shutdown
   encapsulation dot1q vlan 70
   vrf VRF-NEXTGEN_MGMT_DMZ
   ip address 10.0.70.10/29
   vrrp 70 priority-level 200
   vrrp 70 ipv4 10.0.70.9
   vrrp 70 ipv4 version 3
!
interface Port-Channel291.888
   description ARI-MG-DL-01-02-MTZ - MLAG51 - Vlan888 - TEST NRFU
   no shutdown
   encapsulation dot1q vlan 888
   vrf VRF-NEXTGEN_PRODUCCION
   ip address 100.64.88.1/24
```

### Loopback Interfaces

#### Loopback Interfaces Summary

##### IPv4

| Interface | Description | VRF | IP Address |
| --------- | ----------- | --- | ---------- |
| Loopback0 | ROUTER_ID | default | 10.110.5.26/32 |
| Loopback1 | VXLAN_TUNNEL_SOURCE | default | 10.110.6.26/32 |
| Loopback1001 | DIAG_VRF_VRF-NEXTGEN_PRODUCCION | VRF-NEXTGEN_PRODUCCION | 10.110.7.26/32 |
| Loopback1002 | DIAG_VRF_VRF-NEXTGEN_DESARROLLO | VRF-NEXTGEN_DESARROLLO | 10.110.7.26/32 |
| Loopback1003 | DIAG_VRF_VRF-NEXTGEN_DMZ_INT | VRF-NEXTGEN_DMZ_INT | 10.110.7.26/32 |
| Loopback1004 | DIAG_VRF_VRF-NEXTGEN_DMZ_FRONT | VRF-NEXTGEN_DMZ_FRONT | 10.110.7.26/32 |
| Loopback1005 | DIAG_VRF_VRF-NEXTGEN_MGMT | VRF-NEXTGEN_MGMT | 10.110.7.26/32 |
| Loopback1006 | DIAG_VRF_VRF-NEXTGEN_MGMT_DMZ | VRF-NEXTGEN_MGMT_DMZ | 10.110.7.26/32 |

##### IPv6

| Interface | Description | VRF | IPv6 Address |
| --------- | ----------- | --- | ------------ |
| Loopback0 | ROUTER_ID | default | - |
| Loopback1 | VXLAN_TUNNEL_SOURCE | default | - |
| Loopback1001 | DIAG_VRF_VRF-NEXTGEN_PRODUCCION | VRF-NEXTGEN_PRODUCCION | - |
| Loopback1002 | DIAG_VRF_VRF-NEXTGEN_DESARROLLO | VRF-NEXTGEN_DESARROLLO | - |
| Loopback1003 | DIAG_VRF_VRF-NEXTGEN_DMZ_INT | VRF-NEXTGEN_DMZ_INT | - |
| Loopback1004 | DIAG_VRF_VRF-NEXTGEN_DMZ_FRONT | VRF-NEXTGEN_DMZ_FRONT | - |
| Loopback1005 | DIAG_VRF_VRF-NEXTGEN_MGMT | VRF-NEXTGEN_MGMT | - |
| Loopback1006 | DIAG_VRF_VRF-NEXTGEN_MGMT_DMZ | VRF-NEXTGEN_MGMT_DMZ | - |

#### Loopback Interfaces Device Configuration

```eos
!
interface Loopback0
   description ROUTER_ID
   no shutdown
   ip address 10.110.5.26/32
!
interface Loopback1
   description VXLAN_TUNNEL_SOURCE
   no shutdown
   ip address 10.110.6.26/32
!
interface Loopback1001
   description DIAG_VRF_VRF-NEXTGEN_PRODUCCION
   no shutdown
   vrf VRF-NEXTGEN_PRODUCCION
   ip address 10.110.7.26/32
!
interface Loopback1002
   description DIAG_VRF_VRF-NEXTGEN_DESARROLLO
   no shutdown
   vrf VRF-NEXTGEN_DESARROLLO
   ip address 10.110.7.26/32
!
interface Loopback1003
   description DIAG_VRF_VRF-NEXTGEN_DMZ_INT
   no shutdown
   vrf VRF-NEXTGEN_DMZ_INT
   ip address 10.110.7.26/32
!
interface Loopback1004
   description DIAG_VRF_VRF-NEXTGEN_DMZ_FRONT
   no shutdown
   vrf VRF-NEXTGEN_DMZ_FRONT
   ip address 10.110.7.26/32
!
interface Loopback1005
   description DIAG_VRF_VRF-NEXTGEN_MGMT
   no shutdown
   vrf VRF-NEXTGEN_MGMT
   ip address 10.110.7.26/32
!
interface Loopback1006
   description DIAG_VRF_VRF-NEXTGEN_MGMT_DMZ
   no shutdown
   vrf VRF-NEXTGEN_MGMT_DMZ
   ip address 10.110.7.26/32
```

### VLAN Interfaces

#### VLAN Interfaces Summary

| Interface | Description | VRF |  MTU | Shutdown |
| --------- | ----------- | --- | ---- | -------- |
| Vlan150 | NEXTGEN_PRODUCCION_Vl_150 | VRF-NEXTGEN_PRODUCCION | - | True |
| Vlan252 | NEXTGEN_MGMT_Vl_252 | VRF-NEXTGEN_MGMT | - | False |
| Vlan267 | NEXTGEN_MGMT_DMZ_Vl_267 | VRF-NEXTGEN_MGMT_DMZ | - | False |
| Vlan301 | NEXTGEN_DESARROLLO_Vl_301 | VRF-NEXTGEN_DESARROLLO | - | True |
| Vlan450 | NEXTGEN_DMZ_INT_Vl_450 | VRF-NEXTGEN_DMZ_INT | - | True |
| Vlan470 | NEXTGEN_DMZ_FRONT_Vl_470 | VRF-NEXTGEN_DMZ_FRONT | - | True |

##### IPv4

| Interface | VRF | IP Address | IP Address Virtual | IP Router Virtual Address | ACL In | ACL Out |
| --------- | --- | ---------- | ------------------ | ------------------------- | ------ | ------- |
| Vlan150 |  VRF-NEXTGEN_PRODUCCION  |  -  |  10.40.0.1/20  |  -  |  -  |  -  |
| Vlan252 |  VRF-NEXTGEN_MGMT  |  -  |  10.114.0.1/23  |  -  |  -  |  -  |
| Vlan267 |  VRF-NEXTGEN_MGMT_DMZ  |  -  |  10.114.6.1/23  |  -  |  -  |  -  |
| Vlan301 |  VRF-NEXTGEN_DESARROLLO  |  -  |  10.70.0.1/20  |  -  |  -  |  -  |
| Vlan450 |  VRF-NEXTGEN_DMZ_INT  |  -  |  10.30.16.1/20  |  -  |  -  |  -  |
| Vlan470 |  VRF-NEXTGEN_DMZ_FRONT  |  -  |  10.30.0.1/20  |  -  |  -  |  -  |

#### VLAN Interfaces Device Configuration

```eos
!
interface Vlan150
   description NEXTGEN_PRODUCCION_Vl_150
   shutdown
   vrf VRF-NEXTGEN_PRODUCCION
   ip address virtual 10.40.0.1/20
!
interface Vlan252
   description NEXTGEN_MGMT_Vl_252
   no shutdown
   vrf VRF-NEXTGEN_MGMT
   ip address virtual 10.114.0.1/23
!
interface Vlan267
   description NEXTGEN_MGMT_DMZ_Vl_267
   no shutdown
   vrf VRF-NEXTGEN_MGMT_DMZ
   ip address virtual 10.114.6.1/23
!
interface Vlan301
   description NEXTGEN_DESARROLLO_Vl_301
   shutdown
   vrf VRF-NEXTGEN_DESARROLLO
   ip address virtual 10.70.0.1/20
!
interface Vlan450
   description NEXTGEN_DMZ_INT_Vl_450
   shutdown
   vrf VRF-NEXTGEN_DMZ_INT
   ip address virtual 10.30.16.1/20
!
interface Vlan470
   description NEXTGEN_DMZ_FRONT_Vl_470
   shutdown
   vrf VRF-NEXTGEN_DMZ_FRONT
   ip address virtual 10.30.0.1/20
```

### VXLAN Interface

#### VXLAN Interface Summary

| Setting | Value |
| ------- | ----- |
| Source Interface | Loopback1 |
| UDP port | 4789 |

##### VLAN to VNI, Flood List and Multicast Group Mappings

| VLAN | VNI | Flood List | Multicast Group |
| ---- | --- | ---------- | --------------- |
| 11 | 10011 | - | - |
| 150 | 10150 | - | - |
| 177 | 10177 | - | - |
| 252 | 10252 | - | - |
| 267 | 10267 | - | - |
| 301 | 10301 | - | - |
| 329 | 10329 | - | - |
| 450 | 10450 | - | - |
| 470 | 10470 | - | - |
| 473 | 10473 | - | - |

##### VRF to VNI and Multicast Group Mappings

| VRF | VNI | Overlay Multicast Group to Encap Mappings |
| --- | --- | ----------------------------------------- |
| VRF-NEXTGEN_DESARROLLO | 1002 | - |
| VRF-NEXTGEN_DMZ_FRONT | 1004 | - |
| VRF-NEXTGEN_DMZ_INT | 1003 | - |
| VRF-NEXTGEN_MGMT | 1005 | - |
| VRF-NEXTGEN_MGMT_DMZ | 1006 | - |
| VRF-NEXTGEN_PRODUCCION | 1001 | - |

#### VXLAN Interface Device Configuration

```eos
!
interface Vxlan1
   description ARI-BL-302-MTZ_VTEP
   vxlan source-interface Loopback1
   vxlan udp-port 4789
   vxlan vlan 11 vni 10011
   vxlan vlan 150 vni 10150
   vxlan vlan 177 vni 10177
   vxlan vlan 252 vni 10252
   vxlan vlan 267 vni 10267
   vxlan vlan 301 vni 10301
   vxlan vlan 329 vni 10329
   vxlan vlan 450 vni 10450
   vxlan vlan 470 vni 10470
   vxlan vlan 473 vni 10473
   vxlan vrf VRF-NEXTGEN_DESARROLLO vni 1002
   vxlan vrf VRF-NEXTGEN_DMZ_FRONT vni 1004
   vxlan vrf VRF-NEXTGEN_DMZ_INT vni 1003
   vxlan vrf VRF-NEXTGEN_MGMT vni 1005
   vxlan vrf VRF-NEXTGEN_MGMT_DMZ vni 1006
   vxlan vrf VRF-NEXTGEN_PRODUCCION vni 1001
```

## Routing

### Service Routing Protocols Model

Multi agent routing protocol model enabled

```eos
!
service routing protocols model multi-agent
```

### Virtual Router MAC Address

#### Virtual Router MAC Address Summary

Virtual Router MAC Address: 00:1c:73:ca:fe:66

#### Virtual Router MAC Address Device Configuration

```eos
!
ip virtual-router mac-address 00:1c:73:ca:fe:66
```

### IP Routing

#### IP Routing Summary

| VRF | Routing Enabled |
| --- | --------------- |
| default | True |
| MGMT | False |
| VRF-NEXTGEN_DESARROLLO | True |
| VRF-NEXTGEN_DMZ_FRONT | True |
| VRF-NEXTGEN_DMZ_INT | True |
| VRF-NEXTGEN_MGMT | True |
| VRF-NEXTGEN_MGMT_DMZ | True |
| VRF-NEXTGEN_PRODUCCION | True |

#### IP Routing Device Configuration

```eos
!
ip routing
no ip icmp redirect
no ip routing vrf MGMT
ip routing vrf VRF-NEXTGEN_DESARROLLO
ip routing vrf VRF-NEXTGEN_DMZ_FRONT
ip routing vrf VRF-NEXTGEN_DMZ_INT
ip routing vrf VRF-NEXTGEN_MGMT
ip routing vrf VRF-NEXTGEN_MGMT_DMZ
ip routing vrf VRF-NEXTGEN_PRODUCCION
```

### IPv6 Routing

#### IPv6 Routing Summary

| VRF | Routing Enabled |
| --- | --------------- |
| default | False |
| MGMT | false |
| VRF-NEXTGEN_DESARROLLO | false |
| VRF-NEXTGEN_DMZ_FRONT | false |
| VRF-NEXTGEN_DMZ_INT | false |
| VRF-NEXTGEN_MGMT | false |
| VRF-NEXTGEN_MGMT_DMZ | false |
| VRF-NEXTGEN_PRODUCCION | false |

### Static Routes

#### Static Routes Summary

| VRF | Destination Prefix | Next Hop IP | Exit interface | Administrative Distance | Tag | Route Name | Metric |
| --- | ------------------ | ----------- | -------------- | ----------------------- | --- | ---------- | ------ |
| MGMT | 0.0.0.0/0 | 192.168.0.1 | - | 1 | - | - | - |
| VRF-NEXTGEN_MGMT | 0.0.0.0/0 | 10.0.70.4 | Port-Channel291.69 | 1 | - | Default_to_FWINT-VIP | - |
| VRF-NEXTGEN_MGMT_DMZ | 0.0.0.0/0 | 10.0.70.12 | Port-Channel291.70 | 1 | - | Default_to_FWINT-VIP | - |

#### Static Routes Device Configuration

```eos
!
ip route vrf MGMT 0.0.0.0/0 192.168.0.1
ip route vrf VRF-NEXTGEN_MGMT 0.0.0.0/0 Port-channel291.69 10.0.70.4 name Default_to_FWINT-VIP
ip route vrf VRF-NEXTGEN_MGMT_DMZ 0.0.0.0/0 Port-channel291.70 10.0.70.12 name Default_to_FWINT-VIP
```

### ARP

Global ARP timeout: 1500

#### ARP Device Configuration

```eos
!
arp aging timeout default 1500
```

### Router BGP

ASN Notation: asplain

#### Router BGP Summary

| BGP AS | Router ID |
| ------ | --------- |
| 65063 | 10.110.5.26 |

| BGP Tuning |
| ---------- |
| update wait-install |
| no bgp default ipv4-unicast |
| bgp asn notation asplain |
| distance bgp 20 200 200 |
| timers bgp 5 15 |
| neighbor default send-community |
| update wait-install |
| no bgp default ipv4-unicast |
| maximum-paths 128 ecmp 128 |

#### Router BGP Peer Groups

##### EVPN-OVERLAY-PEERS

| Settings | Value |
| -------- | ----- |
| Address Family | evpn |
| Source | Loopback0 |
| BFD | True |
| Ebgp multihop | 3 |
| Send community | all |
| Maximum routes | 0 (no limit) |

##### IPv4-UNDERLAY-PEERS

| Settings | Value |
| -------- | ----- |
| Address Family | ipv4 |
| Send community | all |
| Maximum routes | 12000 |

#### BGP Neighbors

| Neighbor | Remote AS | VRF | Shutdown | Send-community | Maximum-routes | Allowas-in | BFD | RIB Pre-Policy Retain | Route-Reflector Client | Passive | TTL Max Hops |
| -------- | --------- | --- | -------- | -------------- | -------------- | ---------- | --- | --------------------- | ---------------------- | ------- | ------------ |
| 10.110.1.5 | 65123 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | True | - | - | - | - |
| 10.110.1.7 | 65122 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | True | - | - | - | - |
| 10.110.5.1 | 65041 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 10.110.5.2 | 65041 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 10.110.8.252 | 65041 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 10.110.8.254 | 65041 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |

#### Router BGP EVPN Address Family

- VPN import pruning is **enabled**

##### EVPN Peer Groups

| Peer Group | Activate | Route-map In | Route-map Out | Peer-tag In | Peer-tag Out | Encapsulation | Next-hop-self Source Interface |
| ---------- | -------- | ------------ | ------------- | ----------- | ------------ | ------------- | ------------------------------ |
| EVPN-OVERLAY-PEERS | True | - | - | - | - | default | - |

#### Router BGP VLANs

| VLAN | Route-Distinguisher | Both Route-Target | Import Route Target | Export Route-Target | Redistribute |
| ---- | ------------------- | ----------------- | ------------------- | ------------------- | ------------ |
| 11 | 10.110.5.26:10011 | 10011:10011 | - | - | learned |
| 150 | 10.110.5.26:10150 | 10150:10150 | - | - | learned |
| 177 | 10.110.5.26:10177 | 10177:10177 | - | - | learned |
| 252 | 10.110.5.26:10252 | 10252:10252 | - | - | learned |
| 267 | 10.110.5.26:10267 | 10267:10267 | - | - | learned |
| 301 | 10.110.5.26:10301 | 10301:10301 | - | - | learned |
| 329 | 10.110.5.26:10329 | 10329:10329 | - | - | learned |
| 450 | 10.110.5.26:10450 | 10450:10450 | - | - | learned |
| 470 | 10.110.5.26:10470 | 10470:10470 | - | - | learned |
| 473 | 10.110.5.26:10473 | 10473:10473 | - | - | learned |

#### Router BGP VRFs

| VRF | Route-Distinguisher | Redistribute | Graceful Restart |
| --- | ------------------- | ------------ | ---------------- |
| VRF-NEXTGEN_DESARROLLO | 10.110.5.26:1002 | connected | - |
| VRF-NEXTGEN_DMZ_FRONT | 10.110.5.26:1004 | connected | - |
| VRF-NEXTGEN_DMZ_INT | 10.110.5.26:1003 | connected | - |
| VRF-NEXTGEN_MGMT | 10.110.5.26:1005 | connected<br>static | - |
| VRF-NEXTGEN_MGMT_DMZ | 10.110.5.26:1006 | connected<br>static | - |
| VRF-NEXTGEN_PRODUCCION | 10.110.5.26:1001 | connected | - |

#### Router BGP Device Configuration

```eos
!
router bgp 65063
   router-id 10.110.5.26
   update wait-install
   no bgp default ipv4-unicast
   maximum-paths 128 ecmp 128
   update wait-install
   no bgp default ipv4-unicast
   bgp asn notation asplain
   distance bgp 20 200 200
   timers bgp 5 15
   neighbor default send-community
   neighbor EVPN-OVERLAY-PEERS peer group
   neighbor EVPN-OVERLAY-PEERS update-source Loopback0
   neighbor EVPN-OVERLAY-PEERS bfd
   neighbor EVPN-OVERLAY-PEERS ebgp-multihop 3
   neighbor EVPN-OVERLAY-PEERS password 7 <removed>
   neighbor EVPN-OVERLAY-PEERS send-community
   neighbor EVPN-OVERLAY-PEERS maximum-routes 0
   neighbor IPv4-UNDERLAY-PEERS peer group
   neighbor IPv4-UNDERLAY-PEERS password 7 <removed>
   neighbor IPv4-UNDERLAY-PEERS send-community
   neighbor IPv4-UNDERLAY-PEERS maximum-routes 12000
   neighbor 10.110.1.5 peer group IPv4-UNDERLAY-PEERS
   neighbor 10.110.1.5 remote-as 65123
   neighbor 10.110.1.5 bfd
   neighbor 10.110.1.5 description ARI-BL-402-SKY
   neighbor 10.110.1.7 peer group IPv4-UNDERLAY-PEERS
   neighbor 10.110.1.7 remote-as 65122
   neighbor 10.110.1.7 bfd
   neighbor 10.110.1.7 description ARI-BL-401-SKY
   neighbor 10.110.5.1 peer group EVPN-OVERLAY-PEERS
   neighbor 10.110.5.1 remote-as 65041
   neighbor 10.110.5.1 description ARI-SP-301-MTZ_Loopback0
   neighbor 10.110.5.2 peer group EVPN-OVERLAY-PEERS
   neighbor 10.110.5.2 remote-as 65041
   neighbor 10.110.5.2 description ARI-SP-302-MTZ_Loopback0
   neighbor 10.110.8.252 peer group IPv4-UNDERLAY-PEERS
   neighbor 10.110.8.252 remote-as 65041
   neighbor 10.110.8.252 description ARI-SP-301-MTZ_Ethernet8
   neighbor 10.110.8.254 peer group IPv4-UNDERLAY-PEERS
   neighbor 10.110.8.254 remote-as 65041
   neighbor 10.110.8.254 description ARI-SP-302-MTZ_Ethernet8
   redistribute connected route-map RM-CONN-2-BGP
   !
   vlan 11
      rd 10.110.5.26:10011
      route-target both 10011:10011
      redistribute learned
   !
   vlan 150
      rd 10.110.5.26:10150
      route-target both 10150:10150
      redistribute learned
   !
   vlan 177
      rd 10.110.5.26:10177
      route-target both 10177:10177
      redistribute learned
   !
   vlan 252
      rd 10.110.5.26:10252
      route-target both 10252:10252
      redistribute learned
   !
   vlan 267
      rd 10.110.5.26:10267
      route-target both 10267:10267
      redistribute learned
   !
   vlan 301
      rd 10.110.5.26:10301
      route-target both 10301:10301
      redistribute learned
   !
   vlan 329
      rd 10.110.5.26:10329
      route-target both 10329:10329
      redistribute learned
   !
   vlan 450
      rd 10.110.5.26:10450
      route-target both 10450:10450
      redistribute learned
   !
   vlan 470
      rd 10.110.5.26:10470
      route-target both 10470:10470
      redistribute learned
   !
   vlan 473
      rd 10.110.5.26:10473
      route-target both 10473:10473
      redistribute learned
   !
   address-family evpn
      neighbor EVPN-OVERLAY-PEERS activate
      route import match-failure action discard
   !
   address-family ipv4
      no neighbor EVPN-OVERLAY-PEERS activate
      neighbor IPv4-UNDERLAY-PEERS activate
   !
   address-family rt-membership
      neighbor EVPN-OVERLAY-PEERS activate
   !
   vrf VRF-NEXTGEN_DESARROLLO
      rd 10.110.5.26:1002
      route-target import evpn 1002:1002
      route-target export evpn 1002:1002
      router-id 10.110.5.26
      redistribute connected
   !
   vrf VRF-NEXTGEN_DMZ_FRONT
      rd 10.110.5.26:1004
      route-target import evpn 1004:1004
      route-target export evpn 1004:1004
      router-id 10.110.5.26
      redistribute connected
   !
   vrf VRF-NEXTGEN_DMZ_INT
      rd 10.110.5.26:1003
      route-target import evpn 1003:1003
      route-target export evpn 1003:1003
      router-id 10.110.5.26
      redistribute connected
   !
   vrf VRF-NEXTGEN_MGMT
      rd 10.110.5.26:1005
      route-target import evpn 1005:1005
      route-target export evpn 1005:1005
      router-id 10.110.5.26
      redistribute connected
      redistribute static
   !
   vrf VRF-NEXTGEN_MGMT_DMZ
      rd 10.110.5.26:1006
      route-target import evpn 1006:1006
      route-target export evpn 1006:1006
      router-id 10.110.5.26
      redistribute connected
      redistribute static
   !
   vrf VRF-NEXTGEN_PRODUCCION
      rd 10.110.5.26:1001
      route-target import evpn 1001:1001
      route-target export evpn 1001:1001
      router-id 10.110.5.26
      redistribute connected
```

## BFD

### Router BFD

#### Router BFD Multihop Summary

| Interval | Minimum RX | Multiplier |
| -------- | ---------- | ---------- |
| 300 | 300 | 3 |

#### Router BFD Device Configuration

```eos
!
router bfd
   multihop interval 300 min-rx 300 multiplier 3
```

## Multicast

### IP IGMP Snooping

#### IP IGMP Snooping Summary

| IGMP Snooping | Fast Leave | Interface Restart Query | Proxy | Restart Query Interval | Robustness Variable |
| ------------- | ---------- | ----------------------- | ----- | ---------------------- | ------------------- |
| Disabled | - | - | - | - | - |

#### IP IGMP Snooping Device Configuration

```eos
!
no ip igmp snooping
```

## Filters

### Prefix-lists

#### Prefix-lists Summary

##### PL-LOOPBACKS-EVPN-OVERLAY

| Sequence | Action |
| -------- | ------ |
| 10 | permit 10.110.5.0/24 eq 32 |
| 20 | permit 10.110.6.0/24 eq 32 |

##### PL-NEXTGEN_VDC-SVI-IN

| Sequence | Action |
| -------- | ------ |
| 10 | permit 10.200.160.247/32 |
| 20 | permit 10.200.161.247/32 |

##### PL-NEXTGEN_VDC-SVI-OUT

| Sequence | Action |
| -------- | ------ |
| 10 | permit 10.201.198.0/25 |
| 20 | permit 10.201.202.160/27 |

#### Prefix-lists Device Configuration

```eos
!
ip prefix-list PL-LOOPBACKS-EVPN-OVERLAY
   seq 10 permit 10.110.5.0/24 eq 32
   seq 20 permit 10.110.6.0/24 eq 32
!
ip prefix-list PL-NEXTGEN_VDC-SVI-IN
   seq 10 permit 10.200.160.247/32
   seq 20 permit 10.200.161.247/32
!
ip prefix-list PL-NEXTGEN_VDC-SVI-OUT
   seq 10 permit 10.201.198.0/25
   seq 20 permit 10.201.202.160/27
```

### Route-maps

#### Route-maps Summary

##### RM-CONN-2-BGP

| Sequence | Type | Match | Set | Sub-Route-Map | Continue |
| -------- | ---- | ----- | --- | ------------- | -------- |
| 10 | permit | ip address prefix-list PL-LOOPBACKS-EVPN-OVERLAY | - | - | - |

##### RM-NEXTGEN_VDC-SVI-IN

| Sequence | Type | Match | Set | Sub-Route-Map | Continue |
| -------- | ---- | ----- | --- | ------------- | -------- |
| 10 | permit | ip address prefix-list PL-NEXTGEN_VDC-SVI-IN | - | - | - |

##### RM-NEXTGEN_VDC-SVI-OUT

| Sequence | Type | Match | Set | Sub-Route-Map | Continue |
| -------- | ---- | ----- | --- | ------------- | -------- |
| 10 | permit | ip address prefix-list PL-NEXTGEN_VDC-SVI-OUT | - | - | - |

#### Route-maps Device Configuration

```eos
!
route-map RM-CONN-2-BGP permit 10
   match ip address prefix-list PL-LOOPBACKS-EVPN-OVERLAY
!
route-map RM-NEXTGEN_VDC-SVI-IN permit 10
   match ip address prefix-list PL-NEXTGEN_VDC-SVI-IN
!
route-map RM-NEXTGEN_VDC-SVI-OUT permit 10
   match ip address prefix-list PL-NEXTGEN_VDC-SVI-OUT
```

## ACL

### Standard Access-lists

#### Standard Access-lists Summary

##### CVP-ACL

| Sequence | Action |
| -------- | ------ |
| 10 | permit 0.0.0.0/0 |

##### MGMT-ACL

| Sequence | Action |
| -------- | ------ |
| 10 | permit 0.0.0.0/0 |

#### Standard Access-lists Device Configuration

```eos
!
ip access-list standard CVP-ACL
   10 permit 0.0.0.0/0
!
ip access-list standard MGMT-ACL
   10 permit 0.0.0.0/0
```

## VRF Instances

### VRF Instances Summary

| VRF Name | IP Routing |
| -------- | ---------- |
| MGMT | disabled |
| VRF-NEXTGEN_DESARROLLO | enabled |
| VRF-NEXTGEN_DMZ_FRONT | enabled |
| VRF-NEXTGEN_DMZ_INT | enabled |
| VRF-NEXTGEN_MGMT | enabled |
| VRF-NEXTGEN_MGMT_DMZ | enabled |
| VRF-NEXTGEN_PRODUCCION | enabled |

### VRF Instances Device Configuration

```eos
!
vrf instance MGMT
!
vrf instance VRF-NEXTGEN_DESARROLLO
!
vrf instance VRF-NEXTGEN_DMZ_FRONT
!
vrf instance VRF-NEXTGEN_DMZ_INT
!
vrf instance VRF-NEXTGEN_MGMT
!
vrf instance VRF-NEXTGEN_MGMT_DMZ
!
vrf instance VRF-NEXTGEN_PRODUCCION
```

## Virtual Source NAT

### Virtual Source NAT Summary

| Source NAT VRF | Source NAT IPv4 Address | Source NAT IPv6 Address |
| -------------- | ----------------------- | ----------------------- |
| VRF-NEXTGEN_DESARROLLO | 10.110.7.26 | - |
| VRF-NEXTGEN_DMZ_FRONT | 10.110.7.26 | - |
| VRF-NEXTGEN_DMZ_INT | 10.110.7.26 | - |
| VRF-NEXTGEN_MGMT | 10.110.7.26 | - |
| VRF-NEXTGEN_MGMT_DMZ | 10.110.7.26 | - |
| VRF-NEXTGEN_PRODUCCION | 10.110.7.26 | - |

### Virtual Source NAT Configuration

```eos
!
ip address virtual source-nat vrf VRF-NEXTGEN_DESARROLLO address 10.110.7.26
ip address virtual source-nat vrf VRF-NEXTGEN_DMZ_FRONT address 10.110.7.26
ip address virtual source-nat vrf VRF-NEXTGEN_DMZ_INT address 10.110.7.26
ip address virtual source-nat vrf VRF-NEXTGEN_MGMT address 10.110.7.26
ip address virtual source-nat vrf VRF-NEXTGEN_MGMT_DMZ address 10.110.7.26
ip address virtual source-nat vrf VRF-NEXTGEN_PRODUCCION address 10.110.7.26
```

## Errdisable

### Errdisable Summary

Errdisable recovery timer interval: 30 seconds

```eos
!
errdisable recovery interval 30
```
