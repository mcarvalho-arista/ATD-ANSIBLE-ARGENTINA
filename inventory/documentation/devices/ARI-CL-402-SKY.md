# ARI-CL-402-SKY

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
| Management0 | OOB_MANAGEMENT | oob | MGMT | 192.168.0.123/24 | 192.168.0.1 |

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
   ip address 192.168.0.123/24
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

sFlow is disabled.

sFlow is disabled on all interfaces by default.

#### SFlow Device Configuration

```eos
!
sflow interface disable default
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

STP mode: **mstp**

STP Root Super: **True**

#### MSTP Instance and Priority

| Instance(s) | Priority |
| -------- | -------- |
| 0 | 32768 |

#### Global Spanning-Tree Settings

- Global BPDU Guard for Edge ports is enabled.

### Spanning Tree Device Configuration

```eos
!
spanning-tree mode mstp
spanning-tree edge-port bpduguard default
spanning-tree root super
spanning-tree mst 0 priority 32768
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
| 150 | NEXTGEN_PRODUCCION_Vl_150 | - |
| 177 | NEXTGEN_PRODUCCION_Vl_177 | - |

### VLANs Device Configuration

```eos
!
vlan 150
   name NEXTGEN_PRODUCCION_Vl_150
!
vlan 177
   name NEXTGEN_PRODUCCION_Vl_177
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
| Ethernet1 | SERVER_oh1xar2esxc0101_2/2 | trunk | 150-183,261-263,1280 | - | - | - |
| Ethernet2 | SERVER_oh1xar2esxc0101_3/2 | trunk | 150-183,261-263,1280 | - | - | - |
| Ethernet3 | SERVER_oh1xar2esxc0102_2/2 | trunk | 150-183,261-263,1280 | - | - | - |
| Ethernet4 | SERVER_oh1xar2esxc0102_3/2 | trunk | 150-183,261-263,1280 | - | - | - |
| Ethernet5 | SERVER_oh1xar2esxc0103_2/2 | trunk | 150-183,261-263,1280 | - | - | - |
| Ethernet6 | SERVER_oh1xar2esxc0103_3/2 | trunk | 150-183,261-263,1280 | - | - | - |
| Ethernet7 | SERVER_oh1xar2esxc0104_2/2 | trunk | 150-183,261-263,1280 | - | - | - |
| Ethernet8 | SERVER_oh1xar2esxc0104_3/2 | trunk | 150-183,261-263,1280 | - | - | - |
| Ethernet9 | SERVER_oh1xar2esxc0105_2/2 | trunk | 150-183,261-263,1280 | - | - | - |
| Ethernet10 | SERVER_oh1xar2esxc0105_3/2 | trunk | 150-183,261-263,1280 | - | - | - |
| Ethernet11 | SERVER_oh1xar2esxc0106_2/2 | trunk | 150-183,261-263,1280 | - | - | - |
| Ethernet12 | SERVER_oh1xar2esxc0106_3/2 | trunk | 150-183,261-263,1280 | - | - | - |
| Ethernet13 | SERVER_oh1xar2esxc0107_2/2 | trunk | 150-183,261-263,1280 | - | - | - |
| Ethernet14 | SERVER_oh1xar2esxc0107_3/2 | trunk | 150-183,261-263,1280 | - | - | - |
| Ethernet15 | SERVER_oh1xar2esxc0108_2/2 | trunk | 150-183,261-263,1280 | - | - | - |
| Ethernet16 | SERVER_oh1xar2esxc0108_3/2 | trunk | 150-183,261-263,1280 | - | - | - |
| Ethernet17 | SERVER_oh1xar2esxc0109_2/2 | trunk | 150-183,261-263,1280 | - | - | - |
| Ethernet18 | SERVER_oh1xar2esxc0109_3/2 | trunk | 150-183,261-263,1280 | - | - | - |
| Ethernet19 | SERVER_oh1xar2esxc0110_2/2 | trunk | 150-183,261-263,1280 | - | - | - |
| Ethernet20 | SERVER_oh1xar2esxc0110_3/2 | trunk | 150-183,261-263,1280 | - | - | - |
| Ethernet21 | SERVER_oh1xar2esxc0111_2/2 | trunk | 150-183,261-263,1280 | - | - | - |
| Ethernet22 | SERVER_oh1xar2esxc0111_3/2 | trunk | 150-183,261-263,1280 | - | - | - |
| Ethernet23 | SERVER_oh1xar2esxc0112_2/2 | trunk | 150-183,261-263,1280 | - | - | - |
| Ethernet24 | SERVER_oh1xar2esxc0112_3/2 | trunk | 150-183,261-263,1280 | - | - | - |

*Inherited from Port-Channel Interface

##### Link Tracking Groups

| Interface | Group Name | Direction |
| --------- | ---------- | --------- |
| Ethernet1 | LT_GROUP1 | downstream |
| Ethernet2 | LT_GROUP1 | downstream |
| Ethernet3 | LT_GROUP1 | downstream |
| Ethernet4 | LT_GROUP1 | downstream |
| Ethernet5 | LT_GROUP1 | downstream |
| Ethernet6 | LT_GROUP1 | downstream |
| Ethernet7 | LT_GROUP1 | downstream |
| Ethernet8 | LT_GROUP1 | downstream |
| Ethernet9 | LT_GROUP1 | downstream |
| Ethernet10 | LT_GROUP1 | downstream |
| Ethernet11 | LT_GROUP1 | downstream |
| Ethernet12 | LT_GROUP1 | downstream |
| Ethernet13 | LT_GROUP1 | downstream |
| Ethernet14 | LT_GROUP1 | downstream |
| Ethernet15 | LT_GROUP1 | downstream |
| Ethernet16 | LT_GROUP1 | downstream |
| Ethernet17 | LT_GROUP1 | downstream |
| Ethernet18 | LT_GROUP1 | downstream |
| Ethernet19 | LT_GROUP1 | downstream |
| Ethernet20 | LT_GROUP1 | downstream |
| Ethernet21 | LT_GROUP1 | downstream |
| Ethernet22 | LT_GROUP1 | downstream |
| Ethernet23 | LT_GROUP1 | downstream |
| Ethernet24 | LT_GROUP1 | downstream |

##### IPv4

| Interface | Description | Channel Group | IP Address | VRF |  MTU | Shutdown | ACL In | ACL Out |
| --------- | ----------- | ------------- | ---------- | ----| ---- | -------- | ------ | ------- |
| Ethernet2 | SERVER_oh1xar2esxc0101_3/2 | - | 10.111.8.13/31 | default | - | False | - | - |
| Ethernet3 | SERVER_oh1xar2esxc0102_2/2 | - | 10.111.8.15/31 | default | - | False | - | - |

#### Ethernet Interfaces Device Configuration

```eos
!
interface Ethernet1
   description SERVER_oh1xar2esxc0101_2/2
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
!
interface Ethernet2
   description SERVER_oh1xar2esxc0101_3/2
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   ip address 10.111.8.13/31
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
!
interface Ethernet3
   description SERVER_oh1xar2esxc0102_2/2
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   ip address 10.111.8.15/31
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
!
interface Ethernet4
   description SERVER_oh1xar2esxc0102_3/2
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
!
interface Ethernet5
   description SERVER_oh1xar2esxc0103_2/2
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
!
interface Ethernet6
   description SERVER_oh1xar2esxc0103_3/2
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
!
interface Ethernet7
   description SERVER_oh1xar2esxc0104_2/2
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
!
interface Ethernet8
   description SERVER_oh1xar2esxc0104_3/2
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
!
interface Ethernet9
   description SERVER_oh1xar2esxc0105_2/2
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
!
interface Ethernet10
   description SERVER_oh1xar2esxc0105_3/2
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
!
interface Ethernet11
   description SERVER_oh1xar2esxc0106_2/2
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
!
interface Ethernet12
   description SERVER_oh1xar2esxc0106_3/2
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
!
interface Ethernet13
   description SERVER_oh1xar2esxc0107_2/2
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
!
interface Ethernet14
   description SERVER_oh1xar2esxc0107_3/2
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
!
interface Ethernet15
   description SERVER_oh1xar2esxc0108_2/2
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
!
interface Ethernet16
   description SERVER_oh1xar2esxc0108_3/2
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
!
interface Ethernet17
   description SERVER_oh1xar2esxc0109_2/2
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
!
interface Ethernet18
   description SERVER_oh1xar2esxc0109_3/2
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
!
interface Ethernet19
   description SERVER_oh1xar2esxc0110_2/2
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
!
interface Ethernet20
   description SERVER_oh1xar2esxc0110_3/2
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
!
interface Ethernet21
   description SERVER_oh1xar2esxc0111_2/2
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
!
interface Ethernet22
   description SERVER_oh1xar2esxc0111_3/2
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
!
interface Ethernet23
   description SERVER_oh1xar2esxc0112_2/2
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
!
interface Ethernet24
   description SERVER_oh1xar2esxc0112_3/2
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
```

### Loopback Interfaces

#### Loopback Interfaces Summary

##### IPv4

| Interface | Description | VRF | IP Address |
| --------- | ----------- | --- | ---------- |
| Loopback0 | ROUTER_ID | default | 10.111.5.6/32 |
| Loopback1 | VXLAN_TUNNEL_SOURCE | default | 10.111.6.6/32 |
| Loopback1001 | DIAG_VRF_VRF-NEXTGEN_PRODUCCION | VRF-NEXTGEN_PRODUCCION | 10.111.7.6/32 |

##### IPv6

| Interface | Description | VRF | IPv6 Address |
| --------- | ----------- | --- | ------------ |
| Loopback0 | ROUTER_ID | default | - |
| Loopback1 | VXLAN_TUNNEL_SOURCE | default | - |
| Loopback1001 | DIAG_VRF_VRF-NEXTGEN_PRODUCCION | VRF-NEXTGEN_PRODUCCION | - |

#### Loopback Interfaces Device Configuration

```eos
!
interface Loopback0
   description ROUTER_ID
   no shutdown
   ip address 10.111.5.6/32
!
interface Loopback1
   description VXLAN_TUNNEL_SOURCE
   no shutdown
   ip address 10.111.6.6/32
!
interface Loopback1001
   description DIAG_VRF_VRF-NEXTGEN_PRODUCCION
   no shutdown
   vrf VRF-NEXTGEN_PRODUCCION
   ip address 10.111.7.6/32
```

### VLAN Interfaces

#### VLAN Interfaces Summary

| Interface | Description | VRF |  MTU | Shutdown |
| --------- | ----------- | --- | ---- | -------- |
| Vlan150 | NEXTGEN_PRODUCCION_Vl_150 | VRF-NEXTGEN_PRODUCCION | - | True |

##### IPv4

| Interface | VRF | IP Address | IP Address Virtual | IP Router Virtual Address | ACL In | ACL Out |
| --------- | --- | ---------- | ------------------ | ------------------------- | ------ | ------- |
| Vlan150 |  VRF-NEXTGEN_PRODUCCION  |  -  |  10.40.0.1/20  |  -  |  -  |  -  |

#### VLAN Interfaces Device Configuration

```eos
!
interface Vlan150
   description NEXTGEN_PRODUCCION_Vl_150
   shutdown
   vrf VRF-NEXTGEN_PRODUCCION
   ip address virtual 10.40.0.1/20
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
| 150 | 10150 | - | - |
| 177 | 10177 | - | - |

##### VRF to VNI and Multicast Group Mappings

| VRF | VNI | Overlay Multicast Group to Encap Mappings |
| --- | --- | ----------------------------------------- |
| VRF-NEXTGEN_PRODUCCION | 1001 | - |

#### VXLAN Interface Device Configuration

```eos
!
interface Vxlan1
   description ARI-CL-402-SKY_VTEP
   vxlan source-interface Loopback1
   vxlan udp-port 4789
   vxlan vlan 150 vni 10150
   vxlan vlan 177 vni 10177
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
| VRF-NEXTGEN_PRODUCCION | True |

#### IP Routing Device Configuration

```eos
!
ip routing
no ip icmp redirect
no ip routing vrf MGMT
ip routing vrf VRF-NEXTGEN_PRODUCCION
```

### IPv6 Routing

#### IPv6 Routing Summary

| VRF | Routing Enabled |
| --- | --------------- |
| default | False |
| MGMT | false |
| VRF-NEXTGEN_PRODUCCION | false |

### Static Routes

#### Static Routes Summary

| VRF | Destination Prefix | Next Hop IP | Exit interface | Administrative Distance | Tag | Route Name | Metric |
| --- | ------------------ | ----------- | -------------- | ----------------------- | --- | ---------- | ------ |
| MGMT | 0.0.0.0/0 | 192.168.0.1 | - | 1 | - | - | - |

#### Static Routes Device Configuration

```eos
!
ip route vrf MGMT 0.0.0.0/0 192.168.0.1
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
| 65103 | 10.111.5.6 |

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
| 10.111.5.1 | 65101 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 10.111.5.2 | 65101 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 10.111.8.12 | 65101 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 10.111.8.14 | 65101 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |

#### Router BGP EVPN Address Family

- VPN import pruning is **enabled**

##### EVPN Peer Groups

| Peer Group | Activate | Route-map In | Route-map Out | Peer-tag In | Peer-tag Out | Encapsulation | Next-hop-self Source Interface |
| ---------- | -------- | ------------ | ------------- | ----------- | ------------ | ------------- | ------------------------------ |
| EVPN-OVERLAY-PEERS | True | - | - | - | - | default | - |

#### Router BGP VLANs

| VLAN | Route-Distinguisher | Both Route-Target | Import Route Target | Export Route-Target | Redistribute |
| ---- | ------------------- | ----------------- | ------------------- | ------------------- | ------------ |
| 150 | 10.111.5.6:10150 | 10150:10150 | - | - | learned |
| 177 | 10.111.5.6:10177 | 10177:10177 | - | - | learned |

#### Router BGP VRFs

| VRF | Route-Distinguisher | Redistribute | Graceful Restart |
| --- | ------------------- | ------------ | ---------------- |
| VRF-NEXTGEN_PRODUCCION | 10.111.5.6:1001 | connected | - |

#### Router BGP Device Configuration

```eos
!
router bgp 65103
   router-id 10.111.5.6
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
   neighbor 10.111.5.1 peer group EVPN-OVERLAY-PEERS
   neighbor 10.111.5.1 remote-as 65101
   neighbor 10.111.5.1 description ARI-SP-401-SKY_Loopback0
   neighbor 10.111.5.2 peer group EVPN-OVERLAY-PEERS
   neighbor 10.111.5.2 remote-as 65101
   neighbor 10.111.5.2 description ARI-SP-402-SKY_Loopback0
   neighbor 10.111.8.12 peer group IPv4-UNDERLAY-PEERS
   neighbor 10.111.8.12 remote-as 65101
   neighbor 10.111.8.12 description ARI-SP-401-SKY_Ethernet3
   neighbor 10.111.8.14 peer group IPv4-UNDERLAY-PEERS
   neighbor 10.111.8.14 remote-as 65101
   neighbor 10.111.8.14 description ARI-SP-402-SKY_Ethernet3
   redistribute connected route-map RM-CONN-2-BGP
   !
   vlan 150
      rd 10.111.5.6:10150
      route-target both 10150:10150
      redistribute learned
   !
   vlan 177
      rd 10.111.5.6:10177
      route-target both 10177:10177
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
   vrf VRF-NEXTGEN_PRODUCCION
      rd 10.111.5.6:1001
      route-target import evpn 1001:1001
      route-target export evpn 1001:1001
      router-id 10.111.5.6
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
| 10 | permit 10.111.5.0/24 eq 32 |
| 20 | permit 10.111.6.0/24 eq 32 |

#### Prefix-lists Device Configuration

```eos
!
ip prefix-list PL-LOOPBACKS-EVPN-OVERLAY
   seq 10 permit 10.111.5.0/24 eq 32
   seq 20 permit 10.111.6.0/24 eq 32
```

### Route-maps

#### Route-maps Summary

##### RM-CONN-2-BGP

| Sequence | Type | Match | Set | Sub-Route-Map | Continue |
| -------- | ---- | ----- | --- | ------------- | -------- |
| 10 | permit | ip address prefix-list PL-LOOPBACKS-EVPN-OVERLAY | - | - | - |

#### Route-maps Device Configuration

```eos
!
route-map RM-CONN-2-BGP permit 10
   match ip address prefix-list PL-LOOPBACKS-EVPN-OVERLAY
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
| VRF-NEXTGEN_PRODUCCION | enabled |

### VRF Instances Device Configuration

```eos
!
vrf instance MGMT
!
vrf instance VRF-NEXTGEN_PRODUCCION
```

## Virtual Source NAT

### Virtual Source NAT Summary

| Source NAT VRF | Source NAT IPv4 Address | Source NAT IPv6 Address |
| -------------- | ----------------------- | ----------------------- |
| VRF-NEXTGEN_PRODUCCION | 10.111.7.6 | - |

### Virtual Source NAT Configuration

```eos
!
ip address virtual source-nat vrf VRF-NEXTGEN_PRODUCCION address 10.111.7.6
```

## Errdisable

### Errdisable Summary

Errdisable recovery timer interval: 30 seconds

```eos
!
errdisable recovery interval 30
```
