# ARI-CL-403-SKY

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
| Management0 | OOB_MANAGEMENT | oob | MGMT | 192.168.0.124/24 | 192.168.0.1 |

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
   ip address 192.168.0.124/24
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
| 129 - 256 | - | - |

### LACP Device Configuration

```eos
!
lacp port-id range 129 256
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
| 151 | NEXTGEN_PRODUCCION_Vl_151 | - |
| 152 | NEXTGEN_PRODUCCION_Vl_152 | - |
| 153 | NEXTGEN_PRODUCCION_Vl_153 | - |
| 154 | NEXTGEN_PRODUCCION_Vl_154 | - |
| 155 | NEXTGEN_PRODUCCION_Vl_155 | - |
| 156 | NEXTGEN_PRODUCCION_Vl_156 | - |
| 157 | NEXTGEN_PRODUCCION_Vl_157 | - |
| 158 | NEXTGEN_PRODUCCION_Vl_158 | - |
| 159 | NEXTGEN_PRODUCCION_Vl_159 | - |
| 160 | NEXTGEN_PRODUCCION_Vl_160 | - |
| 161 | NEXTGEN_PRODUCCION_Vl_161 | - |
| 162 | NEXTGEN_PRODUCCION_Vl_162 | - |
| 163 | NEXTGEN_PRODUCCION_Vl_163 | - |
| 164 | NEXTGEN_PRODUCCION_Vl_164 | - |
| 165 | NEXTGEN_PRODUCCION_Vl_165 | - |
| 166 | NEXTGEN_PRODUCCION_Vl_166 | - |
| 167 | NEXTGEN_PRODUCCION_Vl_167 | - |
| 168 | NEXTGEN_PRODUCCION_Vl_168 | - |
| 169 | NEXTGEN_PRODUCCION_Vl_169 | - |
| 170 | NEXTGEN_PRODUCCION_Vl_170 | - |
| 171 | NEXTGEN_PRODUCCION_Vl_171 | - |
| 172 | NEXTGEN_PRODUCCION_Vl_172 | - |
| 173 | NEXTGEN_PRODUCCION_Vl_173 | - |
| 174 | NEXTGEN_PRODUCCION_Vl_174 | - |
| 175 | NEXTGEN_PRODUCCION_Vl_175 | - |
| 176 | NEXTGEN_PRODUCCION_Vl_176 | - |
| 177 | NEXTGEN_PRODUCCION_Vl_177 | - |
| 178 | NEXTGEN_PRODUCCION_Vl_178 | - |
| 179 | NEXTGEN_PRODUCCION_Vl_179 | - |
| 180 | NEXTGEN_PRODUCCION_Vl_180 | - |
| 181 | NEXTGEN_PRODUCCION_Vl_181 | - |
| 182 | NEXTGEN_PRODUCCION_Vl_182 | - |
| 183 | NEXTGEN_PRODUCCION_Vl_183 | - |
| 261 | NEXTGEN_MGMT_Vl_261 | - |
| 262 | NEXTGEN_MGMT_Vl_262 | - |
| 263 | NEXTGEN_MGMT_Vl_263 | - |
| 1280 | NEXTGEN_MGMT_Vl_1280 | - |

### VLANs Device Configuration

```eos
!
vlan 150
   name NEXTGEN_PRODUCCION_Vl_150
!
vlan 151
   name NEXTGEN_PRODUCCION_Vl_151
!
vlan 152
   name NEXTGEN_PRODUCCION_Vl_152
!
vlan 153
   name NEXTGEN_PRODUCCION_Vl_153
!
vlan 154
   name NEXTGEN_PRODUCCION_Vl_154
!
vlan 155
   name NEXTGEN_PRODUCCION_Vl_155
!
vlan 156
   name NEXTGEN_PRODUCCION_Vl_156
!
vlan 157
   name NEXTGEN_PRODUCCION_Vl_157
!
vlan 158
   name NEXTGEN_PRODUCCION_Vl_158
!
vlan 159
   name NEXTGEN_PRODUCCION_Vl_159
!
vlan 160
   name NEXTGEN_PRODUCCION_Vl_160
!
vlan 161
   name NEXTGEN_PRODUCCION_Vl_161
!
vlan 162
   name NEXTGEN_PRODUCCION_Vl_162
!
vlan 163
   name NEXTGEN_PRODUCCION_Vl_163
!
vlan 164
   name NEXTGEN_PRODUCCION_Vl_164
!
vlan 165
   name NEXTGEN_PRODUCCION_Vl_165
!
vlan 166
   name NEXTGEN_PRODUCCION_Vl_166
!
vlan 167
   name NEXTGEN_PRODUCCION_Vl_167
!
vlan 168
   name NEXTGEN_PRODUCCION_Vl_168
!
vlan 169
   name NEXTGEN_PRODUCCION_Vl_169
!
vlan 170
   name NEXTGEN_PRODUCCION_Vl_170
!
vlan 171
   name NEXTGEN_PRODUCCION_Vl_171
!
vlan 172
   name NEXTGEN_PRODUCCION_Vl_172
!
vlan 173
   name NEXTGEN_PRODUCCION_Vl_173
!
vlan 174
   name NEXTGEN_PRODUCCION_Vl_174
!
vlan 175
   name NEXTGEN_PRODUCCION_Vl_175
!
vlan 176
   name NEXTGEN_PRODUCCION_Vl_176
!
vlan 177
   name NEXTGEN_PRODUCCION_Vl_177
!
vlan 178
   name NEXTGEN_PRODUCCION_Vl_178
!
vlan 179
   name NEXTGEN_PRODUCCION_Vl_179
!
vlan 180
   name NEXTGEN_PRODUCCION_Vl_180
!
vlan 181
   name NEXTGEN_PRODUCCION_Vl_181
!
vlan 182
   name NEXTGEN_PRODUCCION_Vl_182
!
vlan 183
   name NEXTGEN_PRODUCCION_Vl_183
!
vlan 261
   name NEXTGEN_MGMT_Vl_261
!
vlan 262
   name NEXTGEN_MGMT_Vl_262
!
vlan 263
   name NEXTGEN_MGMT_Vl_263
!
vlan 1280
   name NEXTGEN_MGMT_Vl_1280
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
| Ethernet1 | SERVER_oh1xar2esxc0201_2/1 | trunk | 150-183,261-263,1280 | - | - | - |
| Ethernet2 | SERVER_oh1xar2esxc0201_3/1 | trunk | 150-183,261-263,1280 | - | - | - |
| Ethernet3 | SERVER_oh1xar2esxc0202_2/1 | trunk | 150-183,261-263,1280 | - | - | - |
| Ethernet4 | SERVER_oh1xar2esxc0202_3/1 | trunk | 150-183,261-263,1280 | - | - | - |
| Ethernet5 | SERVER_oh1xar2esxc0203_2/1 | trunk | 150-183,261-263,1280 | - | - | - |
| Ethernet6 | SERVER_oh1xar2esxc0203_3/1 | trunk | 150-183,261-263,1280 | - | - | - |
| Ethernet7 | SERVER_oh1xar2esxc0204_2/1 | trunk | 150-183,261-263,1280 | - | - | - |
| Ethernet8 | SERVER_oh1xar2esxc0204_3/1 | trunk | 150-183,261-263,1280 | - | - | - |
| Ethernet9 | SERVER_oh1xar2esxc0205_2/1 | trunk | 150-183,261-263,1280 | - | - | - |
| Ethernet10 | SERVER_oh1xar2esxc0205_3/1 | trunk | 150-183,261-263,1280 | - | - | - |
| Ethernet11 | SERVER_oh1xar2esxc0206_2/1 | trunk | 150-183,261-263,1280 | - | - | - |
| Ethernet12 | SERVER_oh1xar2esxc0206_3/1 | trunk | 150-183,261-263,1280 | - | - | - |
| Ethernet13 | SERVER_oh1xar2esxc0207_2/1 | trunk | 150-183,261-263,1280 | - | - | - |
| Ethernet14 | SERVER_oh1xar2esxc0207_3/1 | trunk | 150-183,261-263,1280 | - | - | - |
| Ethernet15 | SERVER_oh1xar2esxc0208_2/1 | trunk | 150-183,261-263,1280 | - | - | - |
| Ethernet16 | SERVER_oh1xar2esxc0208_3/1 | trunk | 150-183,261-263,1280 | - | - | - |
| Ethernet17 | SERVER_oh1xar2esxc0209_2/1 | trunk | 150-183,261-263,1280 | - | - | - |
| Ethernet18 | SERVER_oh1xar2esxc0209_3/1 | trunk | 150-183,261-263,1280 | - | - | - |
| Ethernet19 | SERVER_oh1xar2esxc0210_2/1 | trunk | 150-183,261-263,1280 | - | - | - |
| Ethernet20 | SERVER_oh1xar2esxc0210_3/1 | trunk | 150-183,261-263,1280 | - | - | - |
| Ethernet21 | SERVER_oh1xar2esxc0211_2/1 | trunk | 150-183,261-263,1280 | - | - | - |
| Ethernet22 | SERVER_oh1xar2esxc0211_3/1 | trunk | 150-183,261-263,1280 | - | - | - |
| Ethernet23 | SERVER_oh1xar2esxc0212_2/1 | trunk | 150-183,261-263,1280 | - | - | - |
| Ethernet24 | SERVER_oh1xar2esxc0212_3/1 | trunk | 150-183,261-263,1280 | - | - | - |

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
| Ethernet2 | SERVER_oh1xar2esxc0201_3/1 | - | 10.111.8.25/31 | default | - | False | - | - |
| Ethernet3 | SERVER_oh1xar2esxc0202_2/1 | - | 10.111.8.27/31 | default | - | False | - | - |

#### Ethernet Interfaces Device Configuration

```eos
!
interface Ethernet1
   description SERVER_oh1xar2esxc0201_2/1
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
!
interface Ethernet2
   description SERVER_oh1xar2esxc0201_3/1
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   ip address 10.111.8.25/31
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
!
interface Ethernet3
   description SERVER_oh1xar2esxc0202_2/1
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   ip address 10.111.8.27/31
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
!
interface Ethernet4
   description SERVER_oh1xar2esxc0202_3/1
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
!
interface Ethernet5
   description SERVER_oh1xar2esxc0203_2/1
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
!
interface Ethernet6
   description SERVER_oh1xar2esxc0203_3/1
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
!
interface Ethernet7
   description SERVER_oh1xar2esxc0204_2/1
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
!
interface Ethernet8
   description SERVER_oh1xar2esxc0204_3/1
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
!
interface Ethernet9
   description SERVER_oh1xar2esxc0205_2/1
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
!
interface Ethernet10
   description SERVER_oh1xar2esxc0205_3/1
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
!
interface Ethernet11
   description SERVER_oh1xar2esxc0206_2/1
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
!
interface Ethernet12
   description SERVER_oh1xar2esxc0206_3/1
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
!
interface Ethernet13
   description SERVER_oh1xar2esxc0207_2/1
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
!
interface Ethernet14
   description SERVER_oh1xar2esxc0207_3/1
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
!
interface Ethernet15
   description SERVER_oh1xar2esxc0208_2/1
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
!
interface Ethernet16
   description SERVER_oh1xar2esxc0208_3/1
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
!
interface Ethernet17
   description SERVER_oh1xar2esxc0209_2/1
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
!
interface Ethernet18
   description SERVER_oh1xar2esxc0209_3/1
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
!
interface Ethernet19
   description SERVER_oh1xar2esxc0210_2/1
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
!
interface Ethernet20
   description SERVER_oh1xar2esxc0210_3/1
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
!
interface Ethernet21
   description SERVER_oh1xar2esxc0211_2/1
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
!
interface Ethernet22
   description SERVER_oh1xar2esxc0211_3/1
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
!
interface Ethernet23
   description SERVER_oh1xar2esxc0212_2/1
   no shutdown
   speed 25g
   switchport trunk allowed vlan 150,151,152,153,154,155,156,157,158,159,160,161,162,163,164,165,166,167,168,169,170,171,172,173,174,175,176,177,178,179,180,181,182,183,261,262,263,1280
   switchport mode trunk
   switchport
   spanning-tree portfast
   link tracking group LT_GROUP1 downstream
!
interface Ethernet24
   description SERVER_oh1xar2esxc0212_3/1
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
| Loopback0 | ROUTER_ID | default | 10.111.5.7/32 |
| Loopback1 | VXLAN_TUNNEL_SOURCE | default | 10.111.6.7/32 |
| Loopback1001 | DIAG_VRF_VRF-NEXTGEN_PRODUCCION | VRF-NEXTGEN_PRODUCCION | 10.111.7.7/32 |
| Loopback1005 | DIAG_VRF_VRF-NEXTGEN_MGMT | VRF-NEXTGEN_MGMT | 10.111.7.7/32 |

##### IPv6

| Interface | Description | VRF | IPv6 Address |
| --------- | ----------- | --- | ------------ |
| Loopback0 | ROUTER_ID | default | - |
| Loopback1 | VXLAN_TUNNEL_SOURCE | default | - |
| Loopback1001 | DIAG_VRF_VRF-NEXTGEN_PRODUCCION | VRF-NEXTGEN_PRODUCCION | - |
| Loopback1005 | DIAG_VRF_VRF-NEXTGEN_MGMT | VRF-NEXTGEN_MGMT | - |

#### Loopback Interfaces Device Configuration

```eos
!
interface Loopback0
   description ROUTER_ID
   no shutdown
   ip address 10.111.5.7/32
!
interface Loopback1
   description VXLAN_TUNNEL_SOURCE
   no shutdown
   ip address 10.111.6.7/32
!
interface Loopback1001
   description DIAG_VRF_VRF-NEXTGEN_PRODUCCION
   no shutdown
   vrf VRF-NEXTGEN_PRODUCCION
   ip address 10.111.7.7/32
!
interface Loopback1005
   description DIAG_VRF_VRF-NEXTGEN_MGMT
   no shutdown
   vrf VRF-NEXTGEN_MGMT
   ip address 10.111.7.7/32
```

### VLAN Interfaces

#### VLAN Interfaces Summary

| Interface | Description | VRF |  MTU | Shutdown |
| --------- | ----------- | --- | ---- | -------- |
| Vlan150 | NEXTGEN_PRODUCCION_Vl_150 | VRF-NEXTGEN_PRODUCCION | - | True |
| Vlan151 | NEXTGEN_PRODUCCION_Vl_151 | VRF-NEXTGEN_PRODUCCION | - | True |
| Vlan152 | NEXTGEN_PRODUCCION_Vl_152 | VRF-NEXTGEN_PRODUCCION | - | True |
| Vlan153 | NEXTGEN_PRODUCCION_Vl_153 | VRF-NEXTGEN_PRODUCCION | - | True |
| Vlan154 | NEXTGEN_PRODUCCION_Vl_154 | VRF-NEXTGEN_PRODUCCION | - | True |
| Vlan155 | NEXTGEN_PRODUCCION_Vl_155 | VRF-NEXTGEN_PRODUCCION | - | True |
| Vlan156 | NEXTGEN_PRODUCCION_Vl_156 | VRF-NEXTGEN_PRODUCCION | - | True |
| Vlan157 | NEXTGEN_PRODUCCION_Vl_157 | VRF-NEXTGEN_PRODUCCION | - | True |
| Vlan158 | NEXTGEN_PRODUCCION_Vl_158 | VRF-NEXTGEN_PRODUCCION | - | True |
| Vlan159 | NEXTGEN_PRODUCCION_Vl_159 | VRF-NEXTGEN_PRODUCCION | - | True |
| Vlan160 | NEXTGEN_PRODUCCION_Vl_160 | VRF-NEXTGEN_PRODUCCION | - | True |
| Vlan161 | NEXTGEN_PRODUCCION_Vl_161 | VRF-NEXTGEN_PRODUCCION | - | True |
| Vlan162 | NEXTGEN_PRODUCCION_Vl_162 | VRF-NEXTGEN_PRODUCCION | - | True |
| Vlan163 | NEXTGEN_PRODUCCION_Vl_163 | VRF-NEXTGEN_PRODUCCION | - | True |
| Vlan164 | NEXTGEN_PRODUCCION_Vl_164 | VRF-NEXTGEN_PRODUCCION | - | True |
| Vlan165 | NEXTGEN_PRODUCCION_Vl_165 | VRF-NEXTGEN_PRODUCCION | - | True |
| Vlan166 | NEXTGEN_PRODUCCION_Vl_166 | VRF-NEXTGEN_PRODUCCION | - | True |
| Vlan167 | NEXTGEN_PRODUCCION_Vl_167 | VRF-NEXTGEN_PRODUCCION | - | True |
| Vlan168 | NEXTGEN_PRODUCCION_Vl_168 | VRF-NEXTGEN_PRODUCCION | - | True |
| Vlan169 | NEXTGEN_PRODUCCION_Vl_169 | VRF-NEXTGEN_PRODUCCION | - | True |
| Vlan170 | NEXTGEN_PRODUCCION_Vl_170 | VRF-NEXTGEN_PRODUCCION | - | True |
| Vlan171 | NEXTGEN_PRODUCCION_Vl_171 | VRF-NEXTGEN_PRODUCCION | - | True |
| Vlan172 | NEXTGEN_PRODUCCION_Vl_172 | VRF-NEXTGEN_PRODUCCION | - | True |
| Vlan173 | NEXTGEN_PRODUCCION_Vl_173 | VRF-NEXTGEN_PRODUCCION | - | True |
| Vlan174 | NEXTGEN_PRODUCCION_Vl_174 | VRF-NEXTGEN_PRODUCCION | - | True |
| Vlan175 | NEXTGEN_PRODUCCION_Vl_175 | VRF-NEXTGEN_PRODUCCION | - | True |
| Vlan176 | NEXTGEN_PRODUCCION_Vl_176 | VRF-NEXTGEN_PRODUCCION | - | True |
| Vlan179 | NEXTGEN_PRODUCCION_Vl_179 | VRF-NEXTGEN_PRODUCCION | - | True |
| Vlan180 | NEXTGEN_PRODUCCION_Vl_180 | VRF-NEXTGEN_PRODUCCION | - | True |
| Vlan181 | NEXTGEN_PRODUCCION_Vl_181 | VRF-NEXTGEN_PRODUCCION | - | True |
| Vlan182 | NEXTGEN_PRODUCCION_Vl_182 | VRF-NEXTGEN_PRODUCCION | - | True |
| Vlan183 | NEXTGEN_PRODUCCION_Vl_183 | VRF-NEXTGEN_PRODUCCION | - | True |
| Vlan261 | NEXTGEN_MGMT_Vl_261 | VRF-NEXTGEN_MGMT | - | False |
| Vlan262 | NEXTGEN_MGMT_Vl_262 | VRF-NEXTGEN_MGMT | - | False |
| Vlan263 | NEXTGEN_MGMT_Vl_263 | VRF-NEXTGEN_MGMT | - | False |

##### IPv4

| Interface | VRF | IP Address | IP Address Virtual | IP Router Virtual Address | ACL In | ACL Out |
| --------- | --- | ---------- | ------------------ | ------------------------- | ------ | ------- |
| Vlan150 |  VRF-NEXTGEN_PRODUCCION  |  -  |  10.40.0.1/20  |  -  |  -  |  -  |
| Vlan151 |  VRF-NEXTGEN_PRODUCCION  |  -  |  10.40.16.1/20  |  -  |  -  |  -  |
| Vlan152 |  VRF-NEXTGEN_PRODUCCION  |  -  |  10.40.32.1/20  |  -  |  -  |  -  |
| Vlan153 |  VRF-NEXTGEN_PRODUCCION  |  -  |  10.40.49.1/25  |  -  |  -  |  -  |
| Vlan154 |  VRF-NEXTGEN_PRODUCCION  |  -  |  10.40.49.129/25  |  -  |  -  |  -  |
| Vlan155 |  VRF-NEXTGEN_PRODUCCION  |  -  |  10.40.51.1/24  |  -  |  -  |  -  |
| Vlan156 |  VRF-NEXTGEN_PRODUCCION  |  -  |  10.40.57.1/26  |  -  |  -  |  -  |
| Vlan157 |  VRF-NEXTGEN_PRODUCCION  |  -  |  10.40.57.65/27  |  -  |  -  |  -  |
| Vlan158 |  VRF-NEXTGEN_PRODUCCION  |  -  |  10.40.57.97/27  |  -  |  -  |  -  |
| Vlan159 |  VRF-NEXTGEN_PRODUCCION  |  -  |  10.40.65.1/24  |  -  |  -  |  -  |
| Vlan160 |  VRF-NEXTGEN_PRODUCCION  |  -  |  10.40.48.1/24  |  -  |  -  |  -  |
| Vlan161 |  VRF-NEXTGEN_PRODUCCION  |  -  |  10.40.50.1/25  |  -  |  -  |  -  |
| Vlan162 |  VRF-NEXTGEN_PRODUCCION  |  -  |  10.40.50.129/25  |  -  |  -  |  -  |
| Vlan163 |  VRF-NEXTGEN_PRODUCCION  |  -  |  10.40.52.1/24  |  -  |  -  |  -  |
| Vlan164 |  VRF-NEXTGEN_PRODUCCION  |  -  |  10.40.53.1/24  |  -  |  -  |  -  |
| Vlan165 |  VRF-NEXTGEN_PRODUCCION  |  -  |  10.40.54.1/25  |  -  |  -  |  -  |
| Vlan166 |  VRF-NEXTGEN_PRODUCCION  |  -  |  10.40.55.1/24  |  -  |  -  |  -  |
| Vlan167 |  VRF-NEXTGEN_PRODUCCION  |  -  |  10.40.56.1/24  |  -  |  -  |  -  |
| Vlan168 |  VRF-NEXTGEN_PRODUCCION  |  -  |  10.40.58.1/24  |  -  |  -  |  -  |
| Vlan169 |  VRF-NEXTGEN_PRODUCCION  |  -  |  10.40.59.1/24  |  -  |  -  |  -  |
| Vlan170 |  VRF-NEXTGEN_PRODUCCION  |  -  |  10.40.60.1/24  |  -  |  -  |  -  |
| Vlan171 |  VRF-NEXTGEN_PRODUCCION  |  -  |  10.40.61.1/24  |  -  |  -  |  -  |
| Vlan172 |  VRF-NEXTGEN_PRODUCCION  |  -  |  10.40.62.1/24  |  -  |  -  |  -  |
| Vlan173 |  VRF-NEXTGEN_PRODUCCION  |  -  |  10.40.63.1/24  |  -  |  -  |  -  |
| Vlan174 |  VRF-NEXTGEN_PRODUCCION  |  -  |  10.110.64.1/25  |  -  |  -  |  -  |
| Vlan175 |  VRF-NEXTGEN_PRODUCCION  |  -  |  10.110.64.129/25  |  -  |  -  |  -  |
| Vlan176 |  VRF-NEXTGEN_PRODUCCION  |  -  |  10.110.100.1/24  |  -  |  -  |  -  |
| Vlan179 |  VRF-NEXTGEN_PRODUCCION  |  -  |  10.40.64.1/27  |  -  |  -  |  -  |
| Vlan180 |  VRF-NEXTGEN_PRODUCCION  |  -  |  10.40.66.1/25  |  -  |  -  |  -  |
| Vlan181 |  VRF-NEXTGEN_PRODUCCION  |  -  |  10.40.66.129/25  |  -  |  -  |  -  |
| Vlan182 |  VRF-NEXTGEN_PRODUCCION  |  -  |  10.40.67.1/25  |  -  |  -  |  -  |
| Vlan183 |  VRF-NEXTGEN_PRODUCCION  |  -  |  10.40.67.129/25  |  -  |  -  |  -  |
| Vlan261 |  VRF-NEXTGEN_MGMT  |  -  |  10.114.2.1/23  |  -  |  -  |  -  |
| Vlan262 |  VRF-NEXTGEN_MGMT  |  -  |  10.114.14.1/23  |  -  |  -  |  -  |
| Vlan263 |  VRF-NEXTGEN_MGMT  |  -  |  10.114.16.1/23  |  -  |  -  |  -  |

#### VLAN Interfaces Device Configuration

```eos
!
interface Vlan150
   description NEXTGEN_PRODUCCION_Vl_150
   shutdown
   vrf VRF-NEXTGEN_PRODUCCION
   ip address virtual 10.40.0.1/20
!
interface Vlan151
   description NEXTGEN_PRODUCCION_Vl_151
   shutdown
   vrf VRF-NEXTGEN_PRODUCCION
   ip address virtual 10.40.16.1/20
!
interface Vlan152
   description NEXTGEN_PRODUCCION_Vl_152
   shutdown
   vrf VRF-NEXTGEN_PRODUCCION
   ip address virtual 10.40.32.1/20
!
interface Vlan153
   description NEXTGEN_PRODUCCION_Vl_153
   shutdown
   vrf VRF-NEXTGEN_PRODUCCION
   ip address virtual 10.40.49.1/25
!
interface Vlan154
   description NEXTGEN_PRODUCCION_Vl_154
   shutdown
   vrf VRF-NEXTGEN_PRODUCCION
   ip address virtual 10.40.49.129/25
!
interface Vlan155
   description NEXTGEN_PRODUCCION_Vl_155
   shutdown
   vrf VRF-NEXTGEN_PRODUCCION
   ip address virtual 10.40.51.1/24
!
interface Vlan156
   description NEXTGEN_PRODUCCION_Vl_156
   shutdown
   vrf VRF-NEXTGEN_PRODUCCION
   ip address virtual 10.40.57.1/26
!
interface Vlan157
   description NEXTGEN_PRODUCCION_Vl_157
   shutdown
   vrf VRF-NEXTGEN_PRODUCCION
   ip address virtual 10.40.57.65/27
!
interface Vlan158
   description NEXTGEN_PRODUCCION_Vl_158
   shutdown
   vrf VRF-NEXTGEN_PRODUCCION
   ip address virtual 10.40.57.97/27
!
interface Vlan159
   description NEXTGEN_PRODUCCION_Vl_159
   shutdown
   vrf VRF-NEXTGEN_PRODUCCION
   ip address virtual 10.40.65.1/24
!
interface Vlan160
   description NEXTGEN_PRODUCCION_Vl_160
   shutdown
   vrf VRF-NEXTGEN_PRODUCCION
   ip address virtual 10.40.48.1/24
!
interface Vlan161
   description NEXTGEN_PRODUCCION_Vl_161
   shutdown
   vrf VRF-NEXTGEN_PRODUCCION
   ip address virtual 10.40.50.1/25
!
interface Vlan162
   description NEXTGEN_PRODUCCION_Vl_162
   shutdown
   vrf VRF-NEXTGEN_PRODUCCION
   ip address virtual 10.40.50.129/25
!
interface Vlan163
   description NEXTGEN_PRODUCCION_Vl_163
   shutdown
   vrf VRF-NEXTGEN_PRODUCCION
   ip address virtual 10.40.52.1/24
!
interface Vlan164
   description NEXTGEN_PRODUCCION_Vl_164
   shutdown
   vrf VRF-NEXTGEN_PRODUCCION
   ip address virtual 10.40.53.1/24
!
interface Vlan165
   description NEXTGEN_PRODUCCION_Vl_165
   shutdown
   vrf VRF-NEXTGEN_PRODUCCION
   ip address virtual 10.40.54.1/25
!
interface Vlan166
   description NEXTGEN_PRODUCCION_Vl_166
   shutdown
   vrf VRF-NEXTGEN_PRODUCCION
   ip address virtual 10.40.55.1/24
!
interface Vlan167
   description NEXTGEN_PRODUCCION_Vl_167
   shutdown
   vrf VRF-NEXTGEN_PRODUCCION
   ip address virtual 10.40.56.1/24
!
interface Vlan168
   description NEXTGEN_PRODUCCION_Vl_168
   shutdown
   vrf VRF-NEXTGEN_PRODUCCION
   ip helper-address 180.166.34.37
   ip helper-address 180.166.34.91
   ip address virtual 10.40.58.1/24
!
interface Vlan169
   description NEXTGEN_PRODUCCION_Vl_169
   shutdown
   vrf VRF-NEXTGEN_PRODUCCION
   ip helper-address 180.166.34.37
   ip helper-address 180.166.34.91
   ip address virtual 10.40.59.1/24
!
interface Vlan170
   description NEXTGEN_PRODUCCION_Vl_170
   shutdown
   vrf VRF-NEXTGEN_PRODUCCION
   ip helper-address 180.166.34.37
   ip helper-address 180.166.34.91
   ip address virtual 10.40.60.1/24
!
interface Vlan171
   description NEXTGEN_PRODUCCION_Vl_171
   shutdown
   vrf VRF-NEXTGEN_PRODUCCION
   ip helper-address 180.166.34.37
   ip helper-address 180.166.34.91
   ip address virtual 10.40.61.1/24
!
interface Vlan172
   description NEXTGEN_PRODUCCION_Vl_172
   shutdown
   vrf VRF-NEXTGEN_PRODUCCION
   ip helper-address 180.166.34.37
   ip helper-address 180.166.34.91
   ip address virtual 10.40.62.1/24
!
interface Vlan173
   description NEXTGEN_PRODUCCION_Vl_173
   shutdown
   vrf VRF-NEXTGEN_PRODUCCION
   ip address virtual 10.40.63.1/24
!
interface Vlan174
   description NEXTGEN_PRODUCCION_Vl_174
   shutdown
   vrf VRF-NEXTGEN_PRODUCCION
   ip address virtual 10.110.64.1/25
!
interface Vlan175
   description NEXTGEN_PRODUCCION_Vl_175
   shutdown
   vrf VRF-NEXTGEN_PRODUCCION
   ip address virtual 10.110.64.129/25
!
interface Vlan176
   description NEXTGEN_PRODUCCION_Vl_176
   shutdown
   vrf VRF-NEXTGEN_PRODUCCION
   ip address virtual 10.110.100.1/24
!
interface Vlan179
   description NEXTGEN_PRODUCCION_Vl_179
   shutdown
   vrf VRF-NEXTGEN_PRODUCCION
   ip address virtual 10.40.64.1/27
!
interface Vlan180
   description NEXTGEN_PRODUCCION_Vl_180
   shutdown
   vrf VRF-NEXTGEN_PRODUCCION
   ip address virtual 10.40.66.1/25
!
interface Vlan181
   description NEXTGEN_PRODUCCION_Vl_181
   shutdown
   vrf VRF-NEXTGEN_PRODUCCION
   ip address virtual 10.40.66.129/25
!
interface Vlan182
   description NEXTGEN_PRODUCCION_Vl_182
   shutdown
   vrf VRF-NEXTGEN_PRODUCCION
   ip address virtual 10.40.67.1/25
!
interface Vlan183
   description NEXTGEN_PRODUCCION_Vl_183
   shutdown
   vrf VRF-NEXTGEN_PRODUCCION
   ip address virtual 10.40.67.129/25
!
interface Vlan261
   description NEXTGEN_MGMT_Vl_261
   no shutdown
   vrf VRF-NEXTGEN_MGMT
   ip address virtual 10.114.2.1/23
!
interface Vlan262
   description NEXTGEN_MGMT_Vl_262
   no shutdown
   vrf VRF-NEXTGEN_MGMT
   ip address virtual 10.114.14.1/23
!
interface Vlan263
   description NEXTGEN_MGMT_Vl_263
   no shutdown
   vrf VRF-NEXTGEN_MGMT
   ip address virtual 10.114.16.1/23
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
| 151 | 10151 | - | - |
| 152 | 10152 | - | - |
| 153 | 10153 | - | - |
| 154 | 10154 | - | - |
| 155 | 10155 | - | - |
| 156 | 10156 | - | - |
| 157 | 10157 | - | - |
| 158 | 10158 | - | - |
| 159 | 10159 | - | - |
| 160 | 10160 | - | - |
| 161 | 10161 | - | - |
| 162 | 10162 | - | - |
| 163 | 10163 | - | - |
| 164 | 10164 | - | - |
| 165 | 10165 | - | - |
| 166 | 10166 | - | - |
| 167 | 10167 | - | - |
| 168 | 10168 | - | - |
| 169 | 10169 | - | - |
| 170 | 10170 | - | - |
| 171 | 10171 | - | - |
| 172 | 10172 | - | - |
| 173 | 10173 | - | - |
| 174 | 10174 | - | - |
| 175 | 10175 | - | - |
| 176 | 10176 | - | - |
| 177 | 10177 | - | - |
| 178 | 10178 | - | - |
| 179 | 10179 | - | - |
| 180 | 10180 | - | - |
| 181 | 10181 | - | - |
| 182 | 10182 | - | - |
| 183 | 10183 | - | - |
| 261 | 10261 | - | - |
| 262 | 10262 | - | - |
| 263 | 10263 | - | - |
| 1280 | 11280 | - | - |

##### VRF to VNI and Multicast Group Mappings

| VRF | VNI | Overlay Multicast Group to Encap Mappings |
| --- | --- | ----------------------------------------- |
| VRF-NEXTGEN_MGMT | 1005 | - |
| VRF-NEXTGEN_PRODUCCION | 1001 | - |

#### VXLAN Interface Device Configuration

```eos
!
interface Vxlan1
   description ARI-CL-403-SKY_VTEP
   vxlan source-interface Loopback1
   vxlan udp-port 4789
   vxlan vlan 150 vni 10150
   vxlan vlan 151 vni 10151
   vxlan vlan 152 vni 10152
   vxlan vlan 153 vni 10153
   vxlan vlan 154 vni 10154
   vxlan vlan 155 vni 10155
   vxlan vlan 156 vni 10156
   vxlan vlan 157 vni 10157
   vxlan vlan 158 vni 10158
   vxlan vlan 159 vni 10159
   vxlan vlan 160 vni 10160
   vxlan vlan 161 vni 10161
   vxlan vlan 162 vni 10162
   vxlan vlan 163 vni 10163
   vxlan vlan 164 vni 10164
   vxlan vlan 165 vni 10165
   vxlan vlan 166 vni 10166
   vxlan vlan 167 vni 10167
   vxlan vlan 168 vni 10168
   vxlan vlan 169 vni 10169
   vxlan vlan 170 vni 10170
   vxlan vlan 171 vni 10171
   vxlan vlan 172 vni 10172
   vxlan vlan 173 vni 10173
   vxlan vlan 174 vni 10174
   vxlan vlan 175 vni 10175
   vxlan vlan 176 vni 10176
   vxlan vlan 177 vni 10177
   vxlan vlan 178 vni 10178
   vxlan vlan 179 vni 10179
   vxlan vlan 180 vni 10180
   vxlan vlan 181 vni 10181
   vxlan vlan 182 vni 10182
   vxlan vlan 183 vni 10183
   vxlan vlan 261 vni 10261
   vxlan vlan 262 vni 10262
   vxlan vlan 263 vni 10263
   vxlan vlan 1280 vni 11280
   vxlan vrf VRF-NEXTGEN_MGMT vni 1005
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
| VRF-NEXTGEN_MGMT | True |
| VRF-NEXTGEN_PRODUCCION | True |

#### IP Routing Device Configuration

```eos
!
ip routing
no ip icmp redirect
no ip routing vrf MGMT
ip routing vrf VRF-NEXTGEN_MGMT
ip routing vrf VRF-NEXTGEN_PRODUCCION
```

### IPv6 Routing

#### IPv6 Routing Summary

| VRF | Routing Enabled |
| --- | --------------- |
| default | False |
| MGMT | false |
| VRF-NEXTGEN_MGMT | false |
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
| 65104 | 10.111.5.7 |

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
| 10.111.8.24 | 65101 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 10.111.8.26 | 65101 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |

#### Router BGP EVPN Address Family

- VPN import pruning is **enabled**

##### EVPN Peer Groups

| Peer Group | Activate | Route-map In | Route-map Out | Peer-tag In | Peer-tag Out | Encapsulation | Next-hop-self Source Interface |
| ---------- | -------- | ------------ | ------------- | ----------- | ------------ | ------------- | ------------------------------ |
| EVPN-OVERLAY-PEERS | True | - | - | - | - | default | - |

#### Router BGP VLANs

| VLAN | Route-Distinguisher | Both Route-Target | Import Route Target | Export Route-Target | Redistribute |
| ---- | ------------------- | ----------------- | ------------------- | ------------------- | ------------ |
| 150 | 10.111.5.7:10150 | 10150:10150 | - | - | learned |
| 151 | 10.111.5.7:10151 | 10151:10151 | - | - | learned |
| 152 | 10.111.5.7:10152 | 10152:10152 | - | - | learned |
| 153 | 10.111.5.7:10153 | 10153:10153 | - | - | learned |
| 154 | 10.111.5.7:10154 | 10154:10154 | - | - | learned |
| 155 | 10.111.5.7:10155 | 10155:10155 | - | - | learned |
| 156 | 10.111.5.7:10156 | 10156:10156 | - | - | learned |
| 157 | 10.111.5.7:10157 | 10157:10157 | - | - | learned |
| 158 | 10.111.5.7:10158 | 10158:10158 | - | - | learned |
| 159 | 10.111.5.7:10159 | 10159:10159 | - | - | learned |
| 160 | 10.111.5.7:10160 | 10160:10160 | - | - | learned |
| 161 | 10.111.5.7:10161 | 10161:10161 | - | - | learned |
| 162 | 10.111.5.7:10162 | 10162:10162 | - | - | learned |
| 163 | 10.111.5.7:10163 | 10163:10163 | - | - | learned |
| 164 | 10.111.5.7:10164 | 10164:10164 | - | - | learned |
| 165 | 10.111.5.7:10165 | 10165:10165 | - | - | learned |
| 166 | 10.111.5.7:10166 | 10166:10166 | - | - | learned |
| 167 | 10.111.5.7:10167 | 10167:10167 | - | - | learned |
| 168 | 10.111.5.7:10168 | 10168:10168 | - | - | learned |
| 169 | 10.111.5.7:10169 | 10169:10169 | - | - | learned |
| 170 | 10.111.5.7:10170 | 10170:10170 | - | - | learned |
| 171 | 10.111.5.7:10171 | 10171:10171 | - | - | learned |
| 172 | 10.111.5.7:10172 | 10172:10172 | - | - | learned |
| 173 | 10.111.5.7:10173 | 10173:10173 | - | - | learned |
| 174 | 10.111.5.7:10174 | 10174:10174 | - | - | learned |
| 175 | 10.111.5.7:10175 | 10175:10175 | - | - | learned |
| 176 | 10.111.5.7:10176 | 10176:10176 | - | - | learned |
| 177 | 10.111.5.7:10177 | 10177:10177 | - | - | learned |
| 178 | 10.111.5.7:10178 | 10178:10178 | - | - | learned |
| 179 | 10.111.5.7:10179 | 10179:10179 | - | - | learned |
| 180 | 10.111.5.7:10180 | 10180:10180 | - | - | learned |
| 181 | 10.111.5.7:10181 | 10181:10181 | - | - | learned |
| 182 | 10.111.5.7:10182 | 10182:10182 | - | - | learned |
| 183 | 10.111.5.7:10183 | 10183:10183 | - | - | learned |
| 261 | 10.111.5.7:10261 | 10261:10261 | - | - | learned |
| 262 | 10.111.5.7:10262 | 10262:10262 | - | - | learned |
| 263 | 10.111.5.7:10263 | 10263:10263 | - | - | learned |
| 1280 | 10.111.5.7:11280 | 11280:11280 | - | - | learned |

#### Router BGP VRFs

| VRF | Route-Distinguisher | Redistribute | Graceful Restart |
| --- | ------------------- | ------------ | ---------------- |
| VRF-NEXTGEN_MGMT | 10.111.5.7:1005 | connected | - |
| VRF-NEXTGEN_PRODUCCION | 10.111.5.7:1001 | connected | - |

#### Router BGP Device Configuration

```eos
!
router bgp 65104
   router-id 10.111.5.7
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
   neighbor 10.111.8.24 peer group IPv4-UNDERLAY-PEERS
   neighbor 10.111.8.24 remote-as 65101
   neighbor 10.111.8.24 description ARI-SP-401-SKY_Ethernet4
   neighbor 10.111.8.26 peer group IPv4-UNDERLAY-PEERS
   neighbor 10.111.8.26 remote-as 65101
   neighbor 10.111.8.26 description ARI-SP-402-SKY_Ethernet4
   redistribute connected route-map RM-CONN-2-BGP
   !
   vlan 150
      rd 10.111.5.7:10150
      route-target both 10150:10150
      redistribute learned
   !
   vlan 151
      rd 10.111.5.7:10151
      route-target both 10151:10151
      redistribute learned
   !
   vlan 152
      rd 10.111.5.7:10152
      route-target both 10152:10152
      redistribute learned
   !
   vlan 153
      rd 10.111.5.7:10153
      route-target both 10153:10153
      redistribute learned
   !
   vlan 154
      rd 10.111.5.7:10154
      route-target both 10154:10154
      redistribute learned
   !
   vlan 155
      rd 10.111.5.7:10155
      route-target both 10155:10155
      redistribute learned
   !
   vlan 156
      rd 10.111.5.7:10156
      route-target both 10156:10156
      redistribute learned
   !
   vlan 157
      rd 10.111.5.7:10157
      route-target both 10157:10157
      redistribute learned
   !
   vlan 158
      rd 10.111.5.7:10158
      route-target both 10158:10158
      redistribute learned
   !
   vlan 159
      rd 10.111.5.7:10159
      route-target both 10159:10159
      redistribute learned
   !
   vlan 160
      rd 10.111.5.7:10160
      route-target both 10160:10160
      redistribute learned
   !
   vlan 161
      rd 10.111.5.7:10161
      route-target both 10161:10161
      redistribute learned
   !
   vlan 162
      rd 10.111.5.7:10162
      route-target both 10162:10162
      redistribute learned
   !
   vlan 163
      rd 10.111.5.7:10163
      route-target both 10163:10163
      redistribute learned
   !
   vlan 164
      rd 10.111.5.7:10164
      route-target both 10164:10164
      redistribute learned
   !
   vlan 165
      rd 10.111.5.7:10165
      route-target both 10165:10165
      redistribute learned
   !
   vlan 166
      rd 10.111.5.7:10166
      route-target both 10166:10166
      redistribute learned
   !
   vlan 167
      rd 10.111.5.7:10167
      route-target both 10167:10167
      redistribute learned
   !
   vlan 168
      rd 10.111.5.7:10168
      route-target both 10168:10168
      redistribute learned
   !
   vlan 169
      rd 10.111.5.7:10169
      route-target both 10169:10169
      redistribute learned
   !
   vlan 170
      rd 10.111.5.7:10170
      route-target both 10170:10170
      redistribute learned
   !
   vlan 171
      rd 10.111.5.7:10171
      route-target both 10171:10171
      redistribute learned
   !
   vlan 172
      rd 10.111.5.7:10172
      route-target both 10172:10172
      redistribute learned
   !
   vlan 173
      rd 10.111.5.7:10173
      route-target both 10173:10173
      redistribute learned
   !
   vlan 174
      rd 10.111.5.7:10174
      route-target both 10174:10174
      redistribute learned
   !
   vlan 175
      rd 10.111.5.7:10175
      route-target both 10175:10175
      redistribute learned
   !
   vlan 176
      rd 10.111.5.7:10176
      route-target both 10176:10176
      redistribute learned
   !
   vlan 177
      rd 10.111.5.7:10177
      route-target both 10177:10177
      redistribute learned
   !
   vlan 178
      rd 10.111.5.7:10178
      route-target both 10178:10178
      redistribute learned
   !
   vlan 179
      rd 10.111.5.7:10179
      route-target both 10179:10179
      redistribute learned
   !
   vlan 180
      rd 10.111.5.7:10180
      route-target both 10180:10180
      redistribute learned
   !
   vlan 181
      rd 10.111.5.7:10181
      route-target both 10181:10181
      redistribute learned
   !
   vlan 182
      rd 10.111.5.7:10182
      route-target both 10182:10182
      redistribute learned
   !
   vlan 183
      rd 10.111.5.7:10183
      route-target both 10183:10183
      redistribute learned
   !
   vlan 261
      rd 10.111.5.7:10261
      route-target both 10261:10261
      redistribute learned
   !
   vlan 262
      rd 10.111.5.7:10262
      route-target both 10262:10262
      redistribute learned
   !
   vlan 263
      rd 10.111.5.7:10263
      route-target both 10263:10263
      redistribute learned
   !
   vlan 1280
      rd 10.111.5.7:11280
      route-target both 11280:11280
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
   vrf VRF-NEXTGEN_MGMT
      rd 10.111.5.7:1005
      route-target import evpn 1005:1005
      route-target export evpn 1005:1005
      router-id 10.111.5.7
      redistribute connected
   !
   vrf VRF-NEXTGEN_PRODUCCION
      rd 10.111.5.7:1001
      route-target import evpn 1001:1001
      route-target export evpn 1001:1001
      router-id 10.111.5.7
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
| VRF-NEXTGEN_MGMT | enabled |
| VRF-NEXTGEN_PRODUCCION | enabled |

### VRF Instances Device Configuration

```eos
!
vrf instance MGMT
!
vrf instance VRF-NEXTGEN_MGMT
!
vrf instance VRF-NEXTGEN_PRODUCCION
```

## Virtual Source NAT

### Virtual Source NAT Summary

| Source NAT VRF | Source NAT IPv4 Address | Source NAT IPv6 Address |
| -------------- | ----------------------- | ----------------------- |
| VRF-NEXTGEN_MGMT | 10.111.7.7 | - |
| VRF-NEXTGEN_PRODUCCION | 10.111.7.7 | - |

### Virtual Source NAT Configuration

```eos
!
ip address virtual source-nat vrf VRF-NEXTGEN_MGMT address 10.111.7.7
ip address virtual source-nat vrf VRF-NEXTGEN_PRODUCCION address 10.111.7.7
```

## Errdisable

### Errdisable Summary

Errdisable recovery timer interval: 30 seconds

```eos
!
errdisable recovery interval 30
```
