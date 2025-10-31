# ARI-SP-401-SKY

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
  - [Spanning Tree](#spanning-tree)
    - [Spanning Tree Summary](#spanning-tree-summary)
    - [Spanning Tree Device Configuration](#spanning-tree-device-configuration)
  - [Internal VLAN Allocation Policy](#internal-vlan-allocation-policy)
    - [Internal VLAN Allocation Policy Summary](#internal-vlan-allocation-policy-summary)
    - [Internal VLAN Allocation Policy Device Configuration](#internal-vlan-allocation-policy-device-configuration)
  - [MAC Address Table](#mac-address-table)
    - [MAC Address Table Summary](#mac-address-table-summary)
    - [MAC Address Table Device Configuration](#mac-address-table-device-configuration)
  - [Interfaces](#interfaces)
    - [Switchport Default](#switchport-default)
    - [Interface Defaults](#interface-defaults)
    - [Ethernet Interfaces](#ethernet-interfaces)
    - [Loopback Interfaces](#loopback-interfaces)
  - [Routing](#routing)
    - [Service Routing Protocols Model](#service-routing-protocols-model)
    - [IP Routing](#ip-routing)
    - [IPv6 Routing](#ipv6-routing)
    - [Static Routes](#static-routes)
    - [ARP](#arp)
    - [Router BGP](#router-bgp)
  - [BFD](#bfd)
    - [Router BFD](#router-bfd)
  - [Filters](#filters)
    - [Prefix-lists](#prefix-lists)
    - [Route-maps](#route-maps)
  - [ACL](#acl)
    - [Standard Access-lists](#standard-access-lists)
  - [VRF Instances](#vrf-instances)
    - [VRF Instances Summary](#vrf-instances-summary)
    - [VRF Instances Device Configuration](#vrf-instances-device-configuration)
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
| Management0 | OOB_MANAGEMENT | oob | MGMT | 192.168.0.20/24 | 192.168.0.1 |

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
   ip address 192.168.0.20/24
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
| Ethernet4 | True | - |
| Ethernet5 | True | - |
| Ethernet7 | True | - |
| Ethernet8 | True | - |

#### SFlow Device Configuration

```eos
!
sflow sample 131072
sflow destination 127.0.0.1
sflow source-interface Loopback0
sflow interface disable default
sflow run
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

##### IPv4

| Interface | Description | Channel Group | IP Address | VRF |  MTU | Shutdown | ACL In | ACL Out |
| --------- | ----------- | ------------- | ---------- | ----| ---- | -------- | ------ | ------- |
| Ethernet2 | P2P_ARI-CL-401-SKY_Ethernet2 | - | 10.111.8.0/31 | default | 9214 | False | - | - |
| Ethernet3 | P2P_ARI-CL-402-SKY_Ethernet2 | - | 10.111.8.12/31 | default | 9214 | False | - | - |
| Ethernet4 | P2P_ARI-CL-403-SKY_Ethernet2 | - | 10.111.8.24/31 | default | 9214 | False | - | - |
| Ethernet5 | P2P_ARI-CL-404-SKY_Ethernet2 | - | 10.111.8.36/31 | default | 9214 | False | - | - |
| Ethernet7 | P2P_ARI-BL-401-SKY_Ethernet2 | - | 10.111.8.240/31 | default | 9214 | False | - | - |
| Ethernet8 | P2P_ARI-BL-402-SKY_Ethernet2 | - | 10.111.8.252/31 | default | 9214 | False | - | - |

#### Ethernet Interfaces Device Configuration

```eos
!
interface Ethernet2
   description P2P_ARI-CL-401-SKY_Ethernet2
   no shutdown
   mtu 9214
   speed forced 100g
   no switchport
   ip address 10.111.8.0/31
   service-profile santander_trust_dscp
   sflow enable
!
interface Ethernet3
   description P2P_ARI-CL-402-SKY_Ethernet2
   no shutdown
   mtu 9214
   speed forced 100g
   no switchport
   ip address 10.111.8.12/31
   service-profile santander_trust_dscp
   sflow enable
!
interface Ethernet4
   description P2P_ARI-CL-403-SKY_Ethernet2
   no shutdown
   mtu 9214
   speed forced 100g
   no switchport
   ip address 10.111.8.24/31
   service-profile santander_trust_dscp
   sflow enable
!
interface Ethernet5
   description P2P_ARI-CL-404-SKY_Ethernet2
   no shutdown
   mtu 9214
   speed forced 100g
   no switchport
   ip address 10.111.8.36/31
   service-profile santander_trust_dscp
   sflow enable
!
interface Ethernet7
   description P2P_ARI-BL-401-SKY_Ethernet2
   no shutdown
   mtu 9214
   speed forced 100g
   no switchport
   ip address 10.111.8.240/31
   service-profile santander_trust_dscp
   sflow enable
!
interface Ethernet8
   description P2P_ARI-BL-402-SKY_Ethernet2
   no shutdown
   mtu 9214
   speed forced 100g
   no switchport
   ip address 10.111.8.252/31
   service-profile santander_trust_dscp
   sflow enable
```

### Loopback Interfaces

#### Loopback Interfaces Summary

##### IPv4

| Interface | Description | VRF | IP Address |
| --------- | ----------- | --- | ---------- |
| Loopback0 | ROUTER_ID | default | 10.111.5.1/32 |

##### IPv6

| Interface | Description | VRF | IPv6 Address |
| --------- | ----------- | --- | ------------ |
| Loopback0 | ROUTER_ID | default | - |

#### Loopback Interfaces Device Configuration

```eos
!
interface Loopback0
   description ROUTER_ID
   no shutdown
   ip address 10.111.5.1/32
```

## Routing

### Service Routing Protocols Model

Multi agent routing protocol model enabled

```eos
!
service routing protocols model multi-agent
```

### IP Routing

#### IP Routing Summary

| VRF | Routing Enabled |
| --- | --------------- |
| default | True |
| MGMT | False |

#### IP Routing Device Configuration

```eos
!
ip routing
no ip icmp redirect
no ip routing vrf MGMT
```

### IPv6 Routing

#### IPv6 Routing Summary

| VRF | Routing Enabled |
| --- | --------------- |
| default | False |
| MGMT | false |

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
| 65101 | 10.111.5.1 |

| BGP Tuning |
| ---------- |
| update wait-for-convergence |
| update wait-install |
| bgp asn notation asplain |
| no bgp default ipv4-unicast |
| distance bgp 20 200 200 |
| timers bgp 5 15 |
| graceful-restart |
| graceful-restart restart-time 300 |
| neighbor default send-community |
| update wait-install |
| no bgp default ipv4-unicast |
| maximum-paths 128 ecmp 128 |

#### Router BGP Peer Groups

##### EVPN-OVERLAY-PEERS

| Settings | Value |
| -------- | ----- |
| Address Family | evpn |
| Next-hop unchanged | True |
| Source | Loopback0 |
| BFD | True |
| Ebgp multihop | 3 |
| Send community | all |
| Maximum routes | 0 (no limit) |

##### EVPN-OVERLAY-SPINES

| Settings | Value |
| -------- | ----- |
| Address Family | evpn |
| Remote AS | 65041 |
| Next-hop unchanged | True |
| Source | loopback0 |
| BFD | True |
| Ebgp multihop | 3 |
| Send community | all |

##### IPv4-UNDERLAY-PEERS

| Settings | Value |
| -------- | ----- |
| Address Family | ipv4 |
| Send community | all |
| Maximum routes | 12000 |

#### BGP Neighbors

| Neighbor | Remote AS | VRF | Shutdown | Send-community | Maximum-routes | Allowas-in | BFD | RIB Pre-Policy Retain | Route-Reflector Client | Passive | TTL Max Hops |
| -------- | --------- | --- | -------- | -------------- | -------------- | ---------- | --- | --------------------- | ---------------------- | ------- | ------------ |
| 10.110.5.1 | Inherited from peer group EVPN-OVERLAY-SPINES | default | - | Inherited from peer group EVPN-OVERLAY-SPINES | - | - | Inherited from peer group EVPN-OVERLAY-SPINES | - | - | - | - |
| 10.110.5.2 | Inherited from peer group EVPN-OVERLAY-SPINES | default | - | Inherited from peer group EVPN-OVERLAY-SPINES | - | - | Inherited from peer group EVPN-OVERLAY-SPINES | - | - | - | - |
| 10.111.5.5 | 65102 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 10.111.5.6 | 65103 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 10.111.5.7 | 65104 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 10.111.5.8 | 65105 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 10.111.5.25 | 65122 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 10.111.5.26 | 65123 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 10.111.8.1 | 65102 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 10.111.8.13 | 65103 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 10.111.8.25 | 65104 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 10.111.8.37 | 65105 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 10.111.8.241 | 65122 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 10.111.8.253 | 65123 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |

#### Router BGP EVPN Address Family

##### EVPN Peer Groups

| Peer Group | Activate | Route-map In | Route-map Out | Peer-tag In | Peer-tag Out | Encapsulation | Next-hop-self Source Interface |
| ---------- | -------- | ------------ | ------------- | ----------- | ------------ | ------------- | ------------------------------ |
| EVPN-OVERLAY-PEERS | True | - | - | - | - | default | - |
| EVPN-OVERLAY-SPINES | True | - | - | - | - | default | - |

#### Router BGP Device Configuration

```eos
!
router bgp 65101
   router-id 10.111.5.1
   update wait-install
   no bgp default ipv4-unicast
   maximum-paths 128 ecmp 128
   update wait-for-convergence
   update wait-install
   bgp asn notation asplain
   no bgp default ipv4-unicast
   distance bgp 20 200 200
   timers bgp 5 15
   graceful-restart
   graceful-restart restart-time 300
   neighbor default send-community
   neighbor EVPN-OVERLAY-PEERS peer group
   neighbor EVPN-OVERLAY-PEERS next-hop-unchanged
   neighbor EVPN-OVERLAY-PEERS update-source Loopback0
   neighbor EVPN-OVERLAY-PEERS bfd
   neighbor EVPN-OVERLAY-PEERS ebgp-multihop 3
   neighbor EVPN-OVERLAY-PEERS password 7 <removed>
   neighbor EVPN-OVERLAY-PEERS send-community
   neighbor EVPN-OVERLAY-PEERS maximum-routes 0
   neighbor EVPN-OVERLAY-SPINES peer group
   neighbor EVPN-OVERLAY-SPINES remote-as 65041
   neighbor EVPN-OVERLAY-SPINES next-hop-unchanged
   neighbor EVPN-OVERLAY-SPINES update-source loopback0
   neighbor EVPN-OVERLAY-SPINES bfd
   neighbor EVPN-OVERLAY-SPINES description EVPN to DC1 RR
   neighbor EVPN-OVERLAY-SPINES ebgp-multihop 3
   neighbor EVPN-OVERLAY-SPINES send-community
   neighbor IPv4-UNDERLAY-PEERS peer group
   neighbor IPv4-UNDERLAY-PEERS password 7 <removed>
   neighbor IPv4-UNDERLAY-PEERS send-community
   neighbor IPv4-UNDERLAY-PEERS maximum-routes 12000
   neighbor 10.110.5.1 peer group EVPN-OVERLAY-SPINES
   neighbor 10.110.5.2 peer group EVPN-OVERLAY-SPINES
   neighbor 10.111.5.5 peer group EVPN-OVERLAY-PEERS
   neighbor 10.111.5.5 remote-as 65102
   neighbor 10.111.5.5 description ARI-CL-401-SKY_Loopback0
   neighbor 10.111.5.6 peer group EVPN-OVERLAY-PEERS
   neighbor 10.111.5.6 remote-as 65103
   neighbor 10.111.5.6 description ARI-CL-402-SKY_Loopback0
   neighbor 10.111.5.7 peer group EVPN-OVERLAY-PEERS
   neighbor 10.111.5.7 remote-as 65104
   neighbor 10.111.5.7 description ARI-CL-403-SKY_Loopback0
   neighbor 10.111.5.8 peer group EVPN-OVERLAY-PEERS
   neighbor 10.111.5.8 remote-as 65105
   neighbor 10.111.5.8 description ARI-CL-404-SKY_Loopback0
   neighbor 10.111.5.25 peer group EVPN-OVERLAY-PEERS
   neighbor 10.111.5.25 remote-as 65122
   neighbor 10.111.5.25 description ARI-BL-401-SKY_Loopback0
   neighbor 10.111.5.26 peer group EVPN-OVERLAY-PEERS
   neighbor 10.111.5.26 remote-as 65123
   neighbor 10.111.5.26 description ARI-BL-402-SKY_Loopback0
   neighbor 10.111.8.1 peer group IPv4-UNDERLAY-PEERS
   neighbor 10.111.8.1 remote-as 65102
   neighbor 10.111.8.1 description ARI-CL-401-SKY_Ethernet2
   neighbor 10.111.8.13 peer group IPv4-UNDERLAY-PEERS
   neighbor 10.111.8.13 remote-as 65103
   neighbor 10.111.8.13 description ARI-CL-402-SKY_Ethernet2
   neighbor 10.111.8.25 peer group IPv4-UNDERLAY-PEERS
   neighbor 10.111.8.25 remote-as 65104
   neighbor 10.111.8.25 description ARI-CL-403-SKY_Ethernet2
   neighbor 10.111.8.37 peer group IPv4-UNDERLAY-PEERS
   neighbor 10.111.8.37 remote-as 65105
   neighbor 10.111.8.37 description ARI-CL-404-SKY_Ethernet2
   neighbor 10.111.8.241 peer group IPv4-UNDERLAY-PEERS
   neighbor 10.111.8.241 remote-as 65122
   neighbor 10.111.8.241 description ARI-BL-401-SKY_Ethernet2
   neighbor 10.111.8.253 peer group IPv4-UNDERLAY-PEERS
   neighbor 10.111.8.253 remote-as 65123
   neighbor 10.111.8.253 description ARI-BL-402-SKY_Ethernet2
   redistribute connected route-map RM-CONN-2-BGP
   !
   address-family evpn
      neighbor EVPN-OVERLAY-PEERS activate
      neighbor EVPN-OVERLAY-SPINES activate
   !
   address-family ipv4
      no neighbor EVPN-OVERLAY-PEERS activate
      neighbor IPv4-UNDERLAY-PEERS activate
   !
   address-family rt-membership
      neighbor EVPN-OVERLAY-PEERS activate
      neighbor EVPN-OVERLAY-PEERS default-route-target only
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

## Filters

### Prefix-lists

#### Prefix-lists Summary

##### PL-LOOPBACKS-EVPN-OVERLAY

| Sequence | Action |
| -------- | ------ |
| 10 | permit 10.111.5.0/24 eq 32 |

#### Prefix-lists Device Configuration

```eos
!
ip prefix-list PL-LOOPBACKS-EVPN-OVERLAY
   seq 10 permit 10.111.5.0/24 eq 32
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

### VRF Instances Device Configuration

```eos
!
vrf instance MGMT
```

## Errdisable

### Errdisable Summary

Errdisable recovery timer interval: 30 seconds

```eos
!
errdisable recovery interval 30
```
