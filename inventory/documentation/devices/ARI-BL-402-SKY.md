# ARI-BL-402-SKY

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
| Management0 | OOB_MANAGEMENT | oob | MGMT | 192.168.0.201/24 | 192.168.0.1 |

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
   ip address 192.168.0.201/24
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
| 12 | NEXTGEN_MGMT_Vl_12 | - |
| 13 | NEXTGEN_MGMT_Vl_13 | - |
| 16 | NEXTGEN_MGMT_Vl_16 | - |
| 18 | NEXTGEN_MGMT_Vl_18 | - |
| 19 | NEXTGEN_MGMT_Vl_19 | - |
| 20 | NEXTGEN_MGMT_Vl_20 | - |
| 21 | NEXTGEN_MGMT_Vl_21 | - |
| 45 | NEXTGEN_MGMT_Vl_45 | - |
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
| 200 | NEXTGEN_MGMT_Vl_200 | - |
| 205 | NEXTGEN_MGMT_Vl_205 | - |
| 232 | NEXTGEN_MGMT_Vl_232 | - |
| 233 | NEXTGEN_MGMT_Vl_233 | - |
| 252 | NEXTGEN_MGMT_Vl_252 | - |
| 253 | NEXTGEN_MGMT_Vl_253 | - |
| 254 | NEXTGEN_MGMT_Vl_254 | - |
| 258 | NEXTGEN_MGMT_Vl_258 | - |
| 259 | NEXTGEN_MGMT_Vl_259 | - |
| 260 | NEXTGEN_MGMT_Vl_260 | - |
| 261 | NEXTGEN_MGMT_Vl_261 | - |
| 262 | NEXTGEN_MGMT_Vl_262 | - |
| 263 | NEXTGEN_MGMT_Vl_263 | - |
| 267 | NEXTGEN_MGMT_DMZ_Vl_267 | - |
| 268 | NEXTGEN_MGMT_DMZ_Vl_268 | - |
| 269 | NEXTGEN_MGMT_DMZ_Vl_269 | - |
| 301 | NEXTGEN_DESARROLLO_Vl_301 | - |
| 302 | NEXTGEN_DESARROLLO_Vl_302 | - |
| 303 | NEXTGEN_DESARROLLO_Vl_303 | - |
| 304 | NEXTGEN_DESARROLLO_Vl_304 | - |
| 305 | NEXTGEN_DESARROLLO_Vl_305 | - |
| 306 | NEXTGEN_DESARROLLO_Vl_306 | - |
| 307 | NEXTGEN_DESARROLLO_Vl_307 | - |
| 308 | NEXTGEN_DESARROLLO_Vl_308 | - |
| 309 | NEXTGEN_DESARROLLO_Vl_309 | - |
| 310 | NEXTGEN_DESARROLLO_Vl_310 | - |
| 311 | NEXTGEN_DESARROLLO_Vl_311 | - |
| 312 | NEXTGEN_DESARROLLO_Vl_312 | - |
| 313 | NEXTGEN_DESARROLLO_Vl_313 | - |
| 314 | NEXTGEN_DESARROLLO_Vl_314 | - |
| 315 | NEXTGEN_DESARROLLO_Vl_315 | - |
| 316 | NEXTGEN_DESARROLLO_Vl_316 | - |
| 317 | NEXTGEN_DESARROLLO_Vl_317 | - |
| 318 | NEXTGEN_DESARROLLO_Vl_318 | - |
| 319 | NEXTGEN_DESARROLLO_Vl_319 | - |
| 320 | NEXTGEN_DESARROLLO_Vl_320 | - |
| 321 | NEXTGEN_DESARROLLO_Vl_321 | - |
| 322 | NEXTGEN_DESARROLLO_Vl_322 | - |
| 323 | NEXTGEN_DESARROLLO_Vl_323 | - |
| 324 | NEXTGEN_DESARROLLO_Vl_324 | - |
| 325 | NEXTGEN_DESARROLLO_Vl_325 | - |
| 326 | NEXTGEN_DESARROLLO_Vl_326 | - |
| 329 | NEXTGEN_DESARROLLO_Vl_329 | - |
| 450 | NEXTGEN_DMZ_INT_Vl_450 | - |
| 451 | NEXTGEN_DMZ_INT_Vl_451 | - |
| 452 | NEXTGEN_DMZ_INT_Vl_452 | - |
| 453 | NEXTGEN_DMZ_INT_Vl_453 | - |
| 454 | NEXTGEN_DMZ_INT_Vl_454 | - |
| 455 | NEXTGEN_DMZ_INT_Vl_455 | - |
| 456 | NEXTGEN_DMZ_INT_Vl_456 | - |
| 457 | NEXTGEN_DMZ_INT_Vl_457 | - |
| 458 | NEXTGEN_DMZ_INT_Vl_458 | - |
| 459 | NEXTGEN_DMZ_INT_Vl_459 | - |
| 460 | NEXTGEN_DMZ_INT_Vl_460 | - |
| 461 | NEXTGEN_DMZ_INT_Vl_461 | - |
| 470 | NEXTGEN_DMZ_FRONT_Vl_470 | - |
| 471 | NEXTGEN_DMZ_FRONT_Vl_471 | - |
| 472 | NEXTGEN_DMZ_FRONT_Vl_472 | - |
| 473 | NEXTGEN_DMZ_INT_Vl_473 | - |
| 600 | NEXTGEN_MGMT_Vl_600 | - |
| 601 | NEXTGEN_MGMT_Vl_601 | - |
| 620 | NEXTGEN_MGMT_Vl_620 | - |
| 640 | NEXTGEN_MGMT_DMZ_Vl_640 | - |
| 641 | NEXTGEN_MGMT_Vl_641 | - |
| 642 | NEXTGEN_MGMT_Vl_642 | - |
| 643 | NEXTGEN_MGMT_Vl_643 | - |
| 1280 | NEXTGEN_MGMT_Vl_1280 | - |
| 1400 | NEXTGEN_MGMT_Vl_1400 | - |

### VLANs Device Configuration

```eos
!
vlan 11
   name NEXTGEN_MGMT_Vl_11
!
vlan 12
   name NEXTGEN_MGMT_Vl_12
!
vlan 13
   name NEXTGEN_MGMT_Vl_13
!
vlan 16
   name NEXTGEN_MGMT_Vl_16
!
vlan 18
   name NEXTGEN_MGMT_Vl_18
!
vlan 19
   name NEXTGEN_MGMT_Vl_19
!
vlan 20
   name NEXTGEN_MGMT_Vl_20
!
vlan 21
   name NEXTGEN_MGMT_Vl_21
!
vlan 45
   name NEXTGEN_MGMT_Vl_45
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
vlan 200
   name NEXTGEN_MGMT_Vl_200
!
vlan 205
   name NEXTGEN_MGMT_Vl_205
!
vlan 232
   name NEXTGEN_MGMT_Vl_232
!
vlan 233
   name NEXTGEN_MGMT_Vl_233
!
vlan 252
   name NEXTGEN_MGMT_Vl_252
!
vlan 253
   name NEXTGEN_MGMT_Vl_253
!
vlan 254
   name NEXTGEN_MGMT_Vl_254
!
vlan 258
   name NEXTGEN_MGMT_Vl_258
!
vlan 259
   name NEXTGEN_MGMT_Vl_259
!
vlan 260
   name NEXTGEN_MGMT_Vl_260
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
vlan 267
   name NEXTGEN_MGMT_DMZ_Vl_267
!
vlan 268
   name NEXTGEN_MGMT_DMZ_Vl_268
!
vlan 269
   name NEXTGEN_MGMT_DMZ_Vl_269
!
vlan 301
   name NEXTGEN_DESARROLLO_Vl_301
!
vlan 302
   name NEXTGEN_DESARROLLO_Vl_302
!
vlan 303
   name NEXTGEN_DESARROLLO_Vl_303
!
vlan 304
   name NEXTGEN_DESARROLLO_Vl_304
!
vlan 305
   name NEXTGEN_DESARROLLO_Vl_305
!
vlan 306
   name NEXTGEN_DESARROLLO_Vl_306
!
vlan 307
   name NEXTGEN_DESARROLLO_Vl_307
!
vlan 308
   name NEXTGEN_DESARROLLO_Vl_308
!
vlan 309
   name NEXTGEN_DESARROLLO_Vl_309
!
vlan 310
   name NEXTGEN_DESARROLLO_Vl_310
!
vlan 311
   name NEXTGEN_DESARROLLO_Vl_311
!
vlan 312
   name NEXTGEN_DESARROLLO_Vl_312
!
vlan 313
   name NEXTGEN_DESARROLLO_Vl_313
!
vlan 314
   name NEXTGEN_DESARROLLO_Vl_314
!
vlan 315
   name NEXTGEN_DESARROLLO_Vl_315
!
vlan 316
   name NEXTGEN_DESARROLLO_Vl_316
!
vlan 317
   name NEXTGEN_DESARROLLO_Vl_317
!
vlan 318
   name NEXTGEN_DESARROLLO_Vl_318
!
vlan 319
   name NEXTGEN_DESARROLLO_Vl_319
!
vlan 320
   name NEXTGEN_DESARROLLO_Vl_320
!
vlan 321
   name NEXTGEN_DESARROLLO_Vl_321
!
vlan 322
   name NEXTGEN_DESARROLLO_Vl_322
!
vlan 323
   name NEXTGEN_DESARROLLO_Vl_323
!
vlan 324
   name NEXTGEN_DESARROLLO_Vl_324
!
vlan 325
   name NEXTGEN_DESARROLLO_Vl_325
!
vlan 326
   name NEXTGEN_DESARROLLO_Vl_326
!
vlan 329
   name NEXTGEN_DESARROLLO_Vl_329
!
vlan 450
   name NEXTGEN_DMZ_INT_Vl_450
!
vlan 451
   name NEXTGEN_DMZ_INT_Vl_451
!
vlan 452
   name NEXTGEN_DMZ_INT_Vl_452
!
vlan 453
   name NEXTGEN_DMZ_INT_Vl_453
!
vlan 454
   name NEXTGEN_DMZ_INT_Vl_454
!
vlan 455
   name NEXTGEN_DMZ_INT_Vl_455
!
vlan 456
   name NEXTGEN_DMZ_INT_Vl_456
!
vlan 457
   name NEXTGEN_DMZ_INT_Vl_457
!
vlan 458
   name NEXTGEN_DMZ_INT_Vl_458
!
vlan 459
   name NEXTGEN_DMZ_INT_Vl_459
!
vlan 460
   name NEXTGEN_DMZ_INT_Vl_460
!
vlan 461
   name NEXTGEN_DMZ_INT_Vl_461
!
vlan 470
   name NEXTGEN_DMZ_FRONT_Vl_470
!
vlan 471
   name NEXTGEN_DMZ_FRONT_Vl_471
!
vlan 472
   name NEXTGEN_DMZ_FRONT_Vl_472
!
vlan 473
   name NEXTGEN_DMZ_INT_Vl_473
!
vlan 600
   name NEXTGEN_MGMT_Vl_600
!
vlan 601
   name NEXTGEN_MGMT_Vl_601
!
vlan 620
   name NEXTGEN_MGMT_Vl_620
!
vlan 640
   name NEXTGEN_MGMT_DMZ_Vl_640
!
vlan 641
   name NEXTGEN_MGMT_Vl_641
!
vlan 642
   name NEXTGEN_MGMT_Vl_642
!
vlan 643
   name NEXTGEN_MGMT_Vl_643
!
vlan 1280
   name NEXTGEN_MGMT_Vl_1280
!
vlan 1400
   name NEXTGEN_MGMT_Vl_1400
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
| Port-Channel291.69 | ARI-MG-DL-01-02-SKY - MLAG51 - Vlan69 | - | 69 | - |
| Port-Channel291.70 | ARI-MG-DL-01-02-SKY - MLAG51 - Vlan70 | - | 70 | - |

##### Link Tracking Groups

| Interface | Group Name | Direction |
| --------- | ---------- | --------- |
| Ethernet2 | LT_GROUP1 | upstream |
| Ethernet3 | LT_GROUP1 | upstream |

##### IPv4

| Interface | Description | Channel Group | IP Address | VRF |  MTU | Shutdown | ACL In | ACL Out |
| --------- | ----------- | ------------- | ---------- | ----| ---- | -------- | ------ | ------- |
| Ethernet2 | P2P_ARI-SP-401-SKY_Ethernet8 | - | 10.111.8.253/31 | default | 9214 | False | - | - |
| Ethernet3 | P2P_ARI-SP-402-SKY_Ethernet8 | - | 10.111.8.255/31 | default | 9214 | False | - | - |
| Ethernet33 | P2P_ARI-BL-302-MTZ_Ethernet33 | - | 10.110.1.5/31 | default | 9214 | False | - | - |
| Ethernet34 | P2P_ARI-BL-301-MTZ_Ethernet34 | - | 10.110.1.3/31 | default | 9214 | False | - | - |
| Port-Channel291.69 | ARI-MG-DL-01-02-SKY - MLAG51 - Vlan69 | - | 10.0.70.3/29 | VRF-NEXTGEN_MGMT | - | False | - | - |
| Port-Channel291.70 | ARI-MG-DL-01-02-SKY - MLAG51 - Vlan70 | - | 10.0.70.11/29 | VRF-NEXTGEN_MGMT_DMZ | - | False | - | - |

##### VRRP Details

| Interface | VRRP-ID | Priority | Advertisement Interval | Preempt | Tracked Object Name(s) | Tracked Object Action(s) | IPv4 Virtual IPs | IPv4 VRRP Version | IPv6 Virtual IPs | Peer Authentication Mode |
| --------- | ------- | -------- | ---------------------- | --------| ---------------------- | ------------------------ | ---------------- | ----------------- | ---------------- | ------------------------ |
| Port-Channel291.69 | 69 | 150 | - | Enabled | - | - | 10.0.70.1 | 3 | - | - |
| Port-Channel291.70 | 70 | 150 | - | Enabled | - | - | 10.0.70.9 | 3 | - | - |

#### Ethernet Interfaces Device Configuration

```eos
!
interface Ethernet2
   description P2P_ARI-SP-401-SKY_Ethernet8
   no shutdown
   mtu 9214
   speed forced 100g
   no switchport
   ip address 10.111.8.253/31
   service-profile santander_trust_dscp
   sflow enable
   link tracking group LT_GROUP1 upstream
!
interface Ethernet3
   description P2P_ARI-SP-402-SKY_Ethernet8
   no shutdown
   mtu 9214
   speed forced 100g
   no switchport
   ip address 10.111.8.255/31
   service-profile santander_trust_dscp
   sflow enable
   link tracking group LT_GROUP1 upstream
!
interface Ethernet33
   description P2P_ARI-BL-302-MTZ_Ethernet33
   no shutdown
   mtu 9214
   speed 10g
   no switchport
   ip address 10.110.1.5/31
   service-profile santander_trust_dscp
   sflow enable
!
interface Ethernet34
   description P2P_ARI-BL-301-MTZ_Ethernet34
   no shutdown
   mtu 9214
   speed 10g
   no switchport
   ip address 10.110.1.3/31
   service-profile santander_trust_dscp
   sflow enable
!
interface Port-Channel291.69
   description ARI-MG-DL-01-02-SKY - MLAG51 - Vlan69
   no shutdown
   encapsulation dot1q vlan 69
   vrf VRF-NEXTGEN_MGMT
   ip address 10.0.70.3/29
   vrrp 69 priority-level 150
   vrrp 69 ipv4 10.0.70.1
   vrrp 69 ipv4 version 3
!
interface Port-Channel291.70
   description ARI-MG-DL-01-02-SKY - MLAG51 - Vlan70
   no shutdown
   encapsulation dot1q vlan 70
   vrf VRF-NEXTGEN_MGMT_DMZ
   ip address 10.0.70.11/29
   vrrp 70 priority-level 150
   vrrp 70 ipv4 10.0.70.9
   vrrp 70 ipv4 version 3
```

### Loopback Interfaces

#### Loopback Interfaces Summary

##### IPv4

| Interface | Description | VRF | IP Address |
| --------- | ----------- | --- | ---------- |
| Loopback0 | ROUTER_ID | default | 10.111.5.26/32 |
| Loopback1 | VXLAN_TUNNEL_SOURCE | default | 10.111.6.26/32 |
| Loopback1001 | DIAG_VRF_VRF-NEXTGEN_PRODUCCION | VRF-NEXTGEN_PRODUCCION | 10.111.7.26/32 |
| Loopback1002 | DIAG_VRF_VRF-NEXTGEN_DESARROLLO | VRF-NEXTGEN_DESARROLLO | 10.111.7.26/32 |
| Loopback1003 | DIAG_VRF_VRF-NEXTGEN_DMZ_INT | VRF-NEXTGEN_DMZ_INT | 10.111.7.26/32 |
| Loopback1004 | DIAG_VRF_VRF-NEXTGEN_DMZ_FRONT | VRF-NEXTGEN_DMZ_FRONT | 10.111.7.26/32 |
| Loopback1005 | DIAG_VRF_VRF-NEXTGEN_MGMT | VRF-NEXTGEN_MGMT | 10.111.7.26/32 |
| Loopback1006 | DIAG_VRF_VRF-NEXTGEN_MGMT_DMZ | VRF-NEXTGEN_MGMT_DMZ | 10.111.7.26/32 |

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
   ip address 10.111.5.26/32
!
interface Loopback1
   description VXLAN_TUNNEL_SOURCE
   no shutdown
   ip address 10.111.6.26/32
!
interface Loopback1001
   description DIAG_VRF_VRF-NEXTGEN_PRODUCCION
   no shutdown
   vrf VRF-NEXTGEN_PRODUCCION
   ip address 10.111.7.26/32
!
interface Loopback1002
   description DIAG_VRF_VRF-NEXTGEN_DESARROLLO
   no shutdown
   vrf VRF-NEXTGEN_DESARROLLO
   ip address 10.111.7.26/32
!
interface Loopback1003
   description DIAG_VRF_VRF-NEXTGEN_DMZ_INT
   no shutdown
   vrf VRF-NEXTGEN_DMZ_INT
   ip address 10.111.7.26/32
!
interface Loopback1004
   description DIAG_VRF_VRF-NEXTGEN_DMZ_FRONT
   no shutdown
   vrf VRF-NEXTGEN_DMZ_FRONT
   ip address 10.111.7.26/32
!
interface Loopback1005
   description DIAG_VRF_VRF-NEXTGEN_MGMT
   no shutdown
   vrf VRF-NEXTGEN_MGMT
   ip address 10.111.7.26/32
!
interface Loopback1006
   description DIAG_VRF_VRF-NEXTGEN_MGMT_DMZ
   no shutdown
   vrf VRF-NEXTGEN_MGMT_DMZ
   ip address 10.111.7.26/32
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
| Vlan252 | NEXTGEN_MGMT_Vl_252 | VRF-NEXTGEN_MGMT | - | False |
| Vlan253 | NEXTGEN_MGMT_Vl_253 | VRF-NEXTGEN_MGMT | - | False |
| Vlan254 | NEXTGEN_MGMT_Vl_254 | VRF-NEXTGEN_MGMT | - | False |
| Vlan258 | NEXTGEN_MGMT_Vl_258 | VRF-NEXTGEN_MGMT | - | False |
| Vlan259 | NEXTGEN_MGMT_Vl_259 | VRF-NEXTGEN_MGMT | - | False |
| Vlan260 | NEXTGEN_MGMT_Vl_260 | VRF-NEXTGEN_MGMT | - | False |
| Vlan261 | NEXTGEN_MGMT_Vl_261 | VRF-NEXTGEN_MGMT | - | False |
| Vlan262 | NEXTGEN_MGMT_Vl_262 | VRF-NEXTGEN_MGMT | - | False |
| Vlan263 | NEXTGEN_MGMT_Vl_263 | VRF-NEXTGEN_MGMT | - | False |
| Vlan267 | NEXTGEN_MGMT_DMZ_Vl_267 | VRF-NEXTGEN_MGMT_DMZ | - | False |
| Vlan268 | NEXTGEN_MGMT_DMZ_Vl_268 | VRF-NEXTGEN_MGMT_DMZ | - | False |
| Vlan269 | NEXTGEN_MGMT_DMZ_Vl_269 | VRF-NEXTGEN_MGMT_DMZ | - | False |
| Vlan301 | NEXTGEN_DESARROLLO_Vl_301 | VRF-NEXTGEN_DESARROLLO | - | True |
| Vlan302 | NEXTGEN_DESARROLLO_Vl_302 | VRF-NEXTGEN_DESARROLLO | - | True |
| Vlan303 | NEXTGEN_DESARROLLO_Vl_303 | VRF-NEXTGEN_DESARROLLO | - | True |
| Vlan304 | NEXTGEN_DESARROLLO_Vl_304 | VRF-NEXTGEN_DESARROLLO | - | True |
| Vlan305 | NEXTGEN_DESARROLLO_Vl_305 | VRF-NEXTGEN_DESARROLLO | - | True |
| Vlan306 | NEXTGEN_DESARROLLO_Vl_306 | VRF-NEXTGEN_DESARROLLO | - | True |
| Vlan307 | NEXTGEN_DESARROLLO_Vl_307 | VRF-NEXTGEN_DESARROLLO | - | True |
| Vlan308 | NEXTGEN_DESARROLLO_Vl_308 | VRF-NEXTGEN_DESARROLLO | - | True |
| Vlan309 | NEXTGEN_DESARROLLO_Vl_309 | VRF-NEXTGEN_DESARROLLO | - | True |
| Vlan310 | NEXTGEN_DESARROLLO_Vl_310 | VRF-NEXTGEN_DESARROLLO | - | True |
| Vlan311 | NEXTGEN_DESARROLLO_Vl_311 | VRF-NEXTGEN_DESARROLLO | - | True |
| Vlan312 | NEXTGEN_DESARROLLO_Vl_312 | VRF-NEXTGEN_DESARROLLO | - | True |
| Vlan313 | NEXTGEN_DESARROLLO_Vl_313 | VRF-NEXTGEN_DESARROLLO | - | True |
| Vlan314 | NEXTGEN_DESARROLLO_Vl_314 | VRF-NEXTGEN_DESARROLLO | - | True |
| Vlan315 | NEXTGEN_DESARROLLO_Vl_315 | VRF-NEXTGEN_DESARROLLO | - | True |
| Vlan316 | NEXTGEN_DESARROLLO_Vl_316 | VRF-NEXTGEN_DESARROLLO | - | True |
| Vlan317 | NEXTGEN_DESARROLLO_Vl_317 | VRF-NEXTGEN_DESARROLLO | - | True |
| Vlan318 | NEXTGEN_DESARROLLO_Vl_318 | VRF-NEXTGEN_DESARROLLO | - | True |
| Vlan319 | NEXTGEN_DESARROLLO_Vl_319 | VRF-NEXTGEN_DESARROLLO | - | True |
| Vlan320 | NEXTGEN_DESARROLLO_Vl_320 | VRF-NEXTGEN_DESARROLLO | - | True |
| Vlan321 | NEXTGEN_DESARROLLO_Vl_321 | VRF-NEXTGEN_DESARROLLO | - | True |
| Vlan322 | NEXTGEN_DESARROLLO_Vl_322 | VRF-NEXTGEN_DESARROLLO | - | True |
| Vlan323 | NEXTGEN_DESARROLLO_Vl_323 | VRF-NEXTGEN_DESARROLLO | - | True |
| Vlan324 | NEXTGEN_DESARROLLO_Vl_324 | VRF-NEXTGEN_DESARROLLO | - | True |
| Vlan325 | NEXTGEN_DESARROLLO_Vl_325 | VRF-NEXTGEN_DESARROLLO | - | True |
| Vlan326 | NEXTGEN_DESARROLLO_Vl_326 | VRF-NEXTGEN_DESARROLLO | - | True |
| Vlan450 | NEXTGEN_DMZ_INT_Vl_450 | VRF-NEXTGEN_DMZ_INT | - | True |
| Vlan451 | NEXTGEN_DMZ_INT_Vl_451 | VRF-NEXTGEN_DMZ_INT | - | True |
| Vlan452 | NEXTGEN_DMZ_INT_Vl_452 | VRF-NEXTGEN_DMZ_INT | - | True |
| Vlan453 | NEXTGEN_DMZ_INT_Vl_453 | VRF-NEXTGEN_DMZ_INT | - | True |
| Vlan454 | NEXTGEN_DMZ_INT_Vl_454 | VRF-NEXTGEN_DMZ_INT | - | True |
| Vlan455 | NEXTGEN_DMZ_INT_Vl_455 | VRF-NEXTGEN_DMZ_INT | - | True |
| Vlan456 | NEXTGEN_DMZ_INT_Vl_456 | VRF-NEXTGEN_DMZ_INT | - | True |
| Vlan457 | NEXTGEN_DMZ_INT_Vl_457 | VRF-NEXTGEN_DMZ_INT | - | True |
| Vlan458 | NEXTGEN_DMZ_INT_Vl_458 | VRF-NEXTGEN_DMZ_INT | - | True |
| Vlan459 | NEXTGEN_DMZ_INT_Vl_459 | VRF-NEXTGEN_DMZ_INT | - | True |
| Vlan460 | NEXTGEN_DMZ_INT_Vl_460 | VRF-NEXTGEN_DMZ_INT | - | True |
| Vlan461 | NEXTGEN_DMZ_INT_Vl_461 | VRF-NEXTGEN_DMZ_INT | - | True |
| Vlan470 | NEXTGEN_DMZ_FRONT_Vl_470 | VRF-NEXTGEN_DMZ_FRONT | - | True |
| Vlan471 | NEXTGEN_DMZ_FRONT_Vl_471 | VRF-NEXTGEN_DMZ_FRONT | - | True |
| Vlan472 | NEXTGEN_DMZ_FRONT_Vl_472 | VRF-NEXTGEN_DMZ_FRONT | - | True |

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
| Vlan252 |  VRF-NEXTGEN_MGMT  |  -  |  10.114.0.1/23  |  -  |  -  |  -  |
| Vlan253 |  VRF-NEXTGEN_MGMT  |  -  |  10.114.8.1/23  |  -  |  -  |  -  |
| Vlan254 |  VRF-NEXTGEN_MGMT  |  -  |  10.114.10.1/24  |  -  |  -  |  -  |
| Vlan258 |  VRF-NEXTGEN_MGMT  |  -  |  10.114.12.1/24  |  -  |  -  |  -  |
| Vlan259 |  VRF-NEXTGEN_MGMT  |  -  |  10.114.13.129/26  |  -  |  -  |  -  |
| Vlan260 |  VRF-NEXTGEN_MGMT  |  -  |  10.114.13.193/26  |  -  |  -  |  -  |
| Vlan261 |  VRF-NEXTGEN_MGMT  |  -  |  10.114.2.1/23  |  -  |  -  |  -  |
| Vlan262 |  VRF-NEXTGEN_MGMT  |  -  |  10.114.14.1/23  |  -  |  -  |  -  |
| Vlan263 |  VRF-NEXTGEN_MGMT  |  -  |  10.114.16.1/23  |  -  |  -  |  -  |
| Vlan267 |  VRF-NEXTGEN_MGMT_DMZ  |  -  |  10.114.6.1/23  |  -  |  -  |  -  |
| Vlan268 |  VRF-NEXTGEN_MGMT_DMZ  |  -  |  10.114.22.1/23  |  -  |  -  |  -  |
| Vlan269 |  VRF-NEXTGEN_MGMT_DMZ  |  -  |  10.114.24.1/23  |  -  |  -  |  -  |
| Vlan301 |  VRF-NEXTGEN_DESARROLLO  |  -  |  10.70.0.1/20  |  -  |  -  |  -  |
| Vlan302 |  VRF-NEXTGEN_DESARROLLO  |  -  |  10.70.16.1/20  |  -  |  -  |  -  |
| Vlan303 |  VRF-NEXTGEN_DESARROLLO  |  -  |  10.70.32.1/20  |  -  |  -  |  -  |
| Vlan304 |  VRF-NEXTGEN_DESARROLLO  |  -  |  10.70.48.1/24  |  -  |  -  |  -  |
| Vlan305 |  VRF-NEXTGEN_DESARROLLO  |  -  |  10.70.49.1/24  |  -  |  -  |  -  |
| Vlan306 |  VRF-NEXTGEN_DESARROLLO  |  -  |  10.70.50.1/24  |  -  |  -  |  -  |
| Vlan307 |  VRF-NEXTGEN_DESARROLLO  |  -  |  10.70.51.1/24  |  -  |  -  |  -  |
| Vlan308 |  VRF-NEXTGEN_DESARROLLO  |  -  |  10.70.53.1/24  |  -  |  -  |  -  |
| Vlan309 |  VRF-NEXTGEN_DESARROLLO  |  -  |  10.70.54.1/25  |  -  |  -  |  -  |
| Vlan310 |  VRF-NEXTGEN_DESARROLLO  |  -  |  10.70.55.1/24  |  -  |  -  |  -  |
| Vlan311 |  VRF-NEXTGEN_DESARROLLO  |  -  |  10.70.56.1/24  |  -  |  -  |  -  |
| Vlan312 |  VRF-NEXTGEN_DESARROLLO  |  -  |  10.70.57.1/24  |  -  |  -  |  -  |
| Vlan313 |  VRF-NEXTGEN_DESARROLLO  |  -  |  10.70.58.1/24  |  -  |  -  |  -  |
| Vlan314 |  VRF-NEXTGEN_DESARROLLO  |  -  |  10.70.59.1/24  |  -  |  -  |  -  |
| Vlan315 |  VRF-NEXTGEN_DESARROLLO  |  -  |  10.70.60.1/24  |  -  |  -  |  -  |
| Vlan316 |  VRF-NEXTGEN_DESARROLLO  |  -  |  10.70.61.1/24  |  -  |  -  |  -  |
| Vlan317 |  VRF-NEXTGEN_DESARROLLO  |  -  |  10.70.62.1/24  |  -  |  -  |  -  |
| Vlan318 |  VRF-NEXTGEN_DESARROLLO  |  -  |  10.70.63.1/24  |  -  |  -  |  -  |
| Vlan319 |  VRF-NEXTGEN_DESARROLLO  |  -  |  180.166.89.1/24  |  -  |  -  |  -  |
| Vlan320 |  VRF-NEXTGEN_DESARROLLO  |  -  |  10.70.64.1/25  |  -  |  -  |  -  |
| Vlan321 |  VRF-NEXTGEN_DESARROLLO  |  -  |  10.70.64.129/25  |  -  |  -  |  -  |
| Vlan322 |  VRF-NEXTGEN_DESARROLLO  |  -  |  10.70.65.1/25  |  -  |  -  |  -  |
| Vlan323 |  VRF-NEXTGEN_DESARROLLO  |  -  |  10.70.66.1/25  |  -  |  -  |  -  |
| Vlan324 |  VRF-NEXTGEN_DESARROLLO  |  -  |  10.70.66.129/25  |  -  |  -  |  -  |
| Vlan325 |  VRF-NEXTGEN_DESARROLLO  |  -  |  10.70.67.1/25  |  -  |  -  |  -  |
| Vlan326 |  VRF-NEXTGEN_DESARROLLO  |  -  |  10.70.67.129/25  |  -  |  -  |  -  |
| Vlan450 |  VRF-NEXTGEN_DMZ_INT  |  -  |  10.30.16.1/20  |  -  |  -  |  -  |
| Vlan451 |  VRF-NEXTGEN_DMZ_INT  |  -  |  10.30.36.1/24  |  -  |  -  |  -  |
| Vlan452 |  VRF-NEXTGEN_DMZ_INT  |  -  |  10.30.37.1/25  |  -  |  -  |  -  |
| Vlan453 |  VRF-NEXTGEN_DMZ_INT  |  -  |  10.30.37.129/25  |  -  |  -  |  -  |
| Vlan454 |  VRF-NEXTGEN_DMZ_INT  |  -  |  10.30.38.1/25  |  -  |  -  |  -  |
| Vlan455 |  VRF-NEXTGEN_DMZ_INT  |  -  |  10.30.38.129/25  |  -  |  -  |  -  |
| Vlan456 |  VRF-NEXTGEN_DMZ_INT  |  -  |  10.30.39.1/24  |  -  |  -  |  -  |
| Vlan457 |  VRF-NEXTGEN_DMZ_INT  |  -  |  10.30.40.1/24  |  -  |  -  |  -  |
| Vlan458 |  VRF-NEXTGEN_DMZ_INT  |  -  |  10.30.41.1/24  |  -  |  -  |  -  |
| Vlan459 |  VRF-NEXTGEN_DMZ_INT  |  -  |  10.30.53.1/24  |  -  |  -  |  -  |
| Vlan460 |  VRF-NEXTGEN_DMZ_INT  |  -  |  10.30.54.1/25  |  -  |  -  |  -  |
| Vlan461 |  VRF-NEXTGEN_DMZ_INT  |  -  |  10.30.61.1/24  |  -  |  -  |  -  |
| Vlan470 |  VRF-NEXTGEN_DMZ_FRONT  |  -  |  10.30.0.1/20  |  -  |  -  |  -  |
| Vlan471 |  VRF-NEXTGEN_DMZ_FRONT  |  -  |  10.30.32.1/24  |  -  |  -  |  -  |
| Vlan472 |  VRF-NEXTGEN_DMZ_FRONT  |  -  |  10.30.72.1/24  |  -  |  -  |  -  |

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
interface Vlan252
   description NEXTGEN_MGMT_Vl_252
   no shutdown
   vrf VRF-NEXTGEN_MGMT
   ip address virtual 10.114.0.1/23
!
interface Vlan253
   description NEXTGEN_MGMT_Vl_253
   no shutdown
   vrf VRF-NEXTGEN_MGMT
   ip address virtual 10.114.8.1/23
!
interface Vlan254
   description NEXTGEN_MGMT_Vl_254
   no shutdown
   vrf VRF-NEXTGEN_MGMT
   ip address virtual 10.114.10.1/24
!
interface Vlan258
   description NEXTGEN_MGMT_Vl_258
   no shutdown
   vrf VRF-NEXTGEN_MGMT
   ip address virtual 10.114.12.1/24
!
interface Vlan259
   description NEXTGEN_MGMT_Vl_259
   no shutdown
   vrf VRF-NEXTGEN_MGMT
   ip address virtual 10.114.13.129/26
!
interface Vlan260
   description NEXTGEN_MGMT_Vl_260
   no shutdown
   vrf VRF-NEXTGEN_MGMT
   ip address virtual 10.114.13.193/26
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
!
interface Vlan267
   description NEXTGEN_MGMT_DMZ_Vl_267
   no shutdown
   vrf VRF-NEXTGEN_MGMT_DMZ
   ip address virtual 10.114.6.1/23
!
interface Vlan268
   description NEXTGEN_MGMT_DMZ_Vl_268
   no shutdown
   vrf VRF-NEXTGEN_MGMT_DMZ
   ip address virtual 10.114.22.1/23
!
interface Vlan269
   description NEXTGEN_MGMT_DMZ_Vl_269
   no shutdown
   vrf VRF-NEXTGEN_MGMT_DMZ
   ip address virtual 10.114.24.1/23
!
interface Vlan301
   description NEXTGEN_DESARROLLO_Vl_301
   shutdown
   vrf VRF-NEXTGEN_DESARROLLO
   ip address virtual 10.70.0.1/20
!
interface Vlan302
   description NEXTGEN_DESARROLLO_Vl_302
   shutdown
   vrf VRF-NEXTGEN_DESARROLLO
   ip address virtual 10.70.16.1/20
!
interface Vlan303
   description NEXTGEN_DESARROLLO_Vl_303
   shutdown
   vrf VRF-NEXTGEN_DESARROLLO
   ip address virtual 10.70.32.1/20
!
interface Vlan304
   description NEXTGEN_DESARROLLO_Vl_304
   shutdown
   vrf VRF-NEXTGEN_DESARROLLO
   ip address virtual 10.70.48.1/24
!
interface Vlan305
   description NEXTGEN_DESARROLLO_Vl_305
   shutdown
   vrf VRF-NEXTGEN_DESARROLLO
   ip address virtual 10.70.49.1/24
!
interface Vlan306
   description NEXTGEN_DESARROLLO_Vl_306
   shutdown
   vrf VRF-NEXTGEN_DESARROLLO
   ip address virtual 10.70.50.1/24
!
interface Vlan307
   description NEXTGEN_DESARROLLO_Vl_307
   shutdown
   vrf VRF-NEXTGEN_DESARROLLO
   ip address virtual 10.70.51.1/24
!
interface Vlan308
   description NEXTGEN_DESARROLLO_Vl_308
   shutdown
   vrf VRF-NEXTGEN_DESARROLLO
   ip address virtual 10.70.53.1/24
!
interface Vlan309
   description NEXTGEN_DESARROLLO_Vl_309
   shutdown
   vrf VRF-NEXTGEN_DESARROLLO
   ip address virtual 10.70.54.1/25
!
interface Vlan310
   description NEXTGEN_DESARROLLO_Vl_310
   shutdown
   vrf VRF-NEXTGEN_DESARROLLO
   ip address virtual 10.70.55.1/24
!
interface Vlan311
   description NEXTGEN_DESARROLLO_Vl_311
   shutdown
   vrf VRF-NEXTGEN_DESARROLLO
   ip address virtual 10.70.56.1/24
!
interface Vlan312
   description NEXTGEN_DESARROLLO_Vl_312
   shutdown
   vrf VRF-NEXTGEN_DESARROLLO
   ip address virtual 10.70.57.1/24
!
interface Vlan313
   description NEXTGEN_DESARROLLO_Vl_313
   shutdown
   vrf VRF-NEXTGEN_DESARROLLO
   ip address virtual 10.70.58.1/24
!
interface Vlan314
   description NEXTGEN_DESARROLLO_Vl_314
   shutdown
   vrf VRF-NEXTGEN_DESARROLLO
   ip helper-address 180.166.34.37
   ip helper-address 180.166.34.91
   ip address virtual 10.70.59.1/24
!
interface Vlan315
   description NEXTGEN_DESARROLLO_Vl_315
   shutdown
   vrf VRF-NEXTGEN_DESARROLLO
   ip address virtual 10.70.60.1/24
!
interface Vlan316
   description NEXTGEN_DESARROLLO_Vl_316
   shutdown
   vrf VRF-NEXTGEN_DESARROLLO
   ip address virtual 10.70.61.1/24
!
interface Vlan317
   description NEXTGEN_DESARROLLO_Vl_317
   shutdown
   vrf VRF-NEXTGEN_DESARROLLO
   ip address virtual 10.70.62.1/24
!
interface Vlan318
   description NEXTGEN_DESARROLLO_Vl_318
   shutdown
   vrf VRF-NEXTGEN_DESARROLLO
   ip helper-address 180.166.34.37
   ip helper-address 180.166.34.91
   ip address virtual 10.70.63.1/24
!
interface Vlan319
   description NEXTGEN_DESARROLLO_Vl_319
   shutdown
   vrf VRF-NEXTGEN_DESARROLLO
   ip address virtual 180.166.89.1/24
!
interface Vlan320
   description NEXTGEN_DESARROLLO_Vl_320
   shutdown
   vrf VRF-NEXTGEN_DESARROLLO
   ip address virtual 10.70.64.1/25
!
interface Vlan321
   description NEXTGEN_DESARROLLO_Vl_321
   shutdown
   vrf VRF-NEXTGEN_DESARROLLO
   ip address virtual 10.70.64.129/25
!
interface Vlan322
   description NEXTGEN_DESARROLLO_Vl_322
   shutdown
   vrf VRF-NEXTGEN_DESARROLLO
   ip address virtual 10.70.65.1/25
!
interface Vlan323
   description NEXTGEN_DESARROLLO_Vl_323
   shutdown
   vrf VRF-NEXTGEN_DESARROLLO
   ip address virtual 10.70.66.1/25
!
interface Vlan324
   description NEXTGEN_DESARROLLO_Vl_324
   shutdown
   vrf VRF-NEXTGEN_DESARROLLO
   ip address virtual 10.70.66.129/25
!
interface Vlan325
   description NEXTGEN_DESARROLLO_Vl_325
   shutdown
   vrf VRF-NEXTGEN_DESARROLLO
   ip address virtual 10.70.67.1/25
!
interface Vlan326
   description NEXTGEN_DESARROLLO_Vl_326
   shutdown
   vrf VRF-NEXTGEN_DESARROLLO
   ip address virtual 10.70.67.129/25
!
interface Vlan450
   description NEXTGEN_DMZ_INT_Vl_450
   shutdown
   vrf VRF-NEXTGEN_DMZ_INT
   ip address virtual 10.30.16.1/20
!
interface Vlan451
   description NEXTGEN_DMZ_INT_Vl_451
   shutdown
   vrf VRF-NEXTGEN_DMZ_INT
   ip address virtual 10.30.36.1/24
!
interface Vlan452
   description NEXTGEN_DMZ_INT_Vl_452
   shutdown
   vrf VRF-NEXTGEN_DMZ_INT
   ip address virtual 10.30.37.1/25
!
interface Vlan453
   description NEXTGEN_DMZ_INT_Vl_453
   shutdown
   vrf VRF-NEXTGEN_DMZ_INT
   ip address virtual 10.30.37.129/25
!
interface Vlan454
   description NEXTGEN_DMZ_INT_Vl_454
   shutdown
   vrf VRF-NEXTGEN_DMZ_INT
   ip address virtual 10.30.38.1/25
!
interface Vlan455
   description NEXTGEN_DMZ_INT_Vl_455
   shutdown
   vrf VRF-NEXTGEN_DMZ_INT
   ip address virtual 10.30.38.129/25
!
interface Vlan456
   description NEXTGEN_DMZ_INT_Vl_456
   shutdown
   vrf VRF-NEXTGEN_DMZ_INT
   ip address virtual 10.30.39.1/24
!
interface Vlan457
   description NEXTGEN_DMZ_INT_Vl_457
   shutdown
   vrf VRF-NEXTGEN_DMZ_INT
   ip address virtual 10.30.40.1/24
!
interface Vlan458
   description NEXTGEN_DMZ_INT_Vl_458
   shutdown
   vrf VRF-NEXTGEN_DMZ_INT
   ip address virtual 10.30.41.1/24
!
interface Vlan459
   description NEXTGEN_DMZ_INT_Vl_459
   shutdown
   vrf VRF-NEXTGEN_DMZ_INT
   ip address virtual 10.30.53.1/24
!
interface Vlan460
   description NEXTGEN_DMZ_INT_Vl_460
   shutdown
   vrf VRF-NEXTGEN_DMZ_INT
   ip address virtual 10.30.54.1/25
!
interface Vlan461
   description NEXTGEN_DMZ_INT_Vl_461
   shutdown
   vrf VRF-NEXTGEN_DMZ_INT
   ip address virtual 10.30.61.1/24
!
interface Vlan470
   description NEXTGEN_DMZ_FRONT_Vl_470
   shutdown
   vrf VRF-NEXTGEN_DMZ_FRONT
   ip address virtual 10.30.0.1/20
!
interface Vlan471
   description NEXTGEN_DMZ_FRONT_Vl_471
   shutdown
   vrf VRF-NEXTGEN_DMZ_FRONT
   ip address virtual 10.30.32.1/24
!
interface Vlan472
   description NEXTGEN_DMZ_FRONT_Vl_472
   shutdown
   vrf VRF-NEXTGEN_DMZ_FRONT
   ip address virtual 10.30.72.1/24
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
| 12 | 10012 | - | - |
| 13 | 10013 | - | - |
| 16 | 10016 | - | - |
| 18 | 10018 | - | - |
| 19 | 10019 | - | - |
| 20 | 10020 | - | - |
| 21 | 10021 | - | - |
| 45 | 10045 | - | - |
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
| 200 | 10200 | - | - |
| 205 | 10205 | - | - |
| 232 | 10232 | - | - |
| 233 | 10233 | - | - |
| 252 | 10252 | - | - |
| 253 | 10253 | - | - |
| 254 | 10254 | - | - |
| 258 | 10258 | - | - |
| 259 | 10259 | - | - |
| 260 | 10260 | - | - |
| 261 | 10261 | - | - |
| 262 | 10262 | - | - |
| 263 | 10263 | - | - |
| 267 | 10267 | - | - |
| 268 | 10268 | - | - |
| 269 | 10269 | - | - |
| 301 | 10301 | - | - |
| 302 | 10302 | - | - |
| 303 | 10303 | - | - |
| 304 | 10304 | - | - |
| 305 | 10305 | - | - |
| 306 | 10306 | - | - |
| 307 | 10307 | - | - |
| 308 | 10308 | - | - |
| 309 | 10309 | - | - |
| 310 | 10310 | - | - |
| 311 | 10311 | - | - |
| 312 | 10312 | - | - |
| 313 | 10313 | - | - |
| 314 | 10314 | - | - |
| 315 | 10315 | - | - |
| 316 | 10316 | - | - |
| 317 | 10317 | - | - |
| 318 | 10318 | - | - |
| 319 | 10319 | - | - |
| 320 | 10320 | - | - |
| 321 | 10321 | - | - |
| 322 | 10322 | - | - |
| 323 | 10323 | - | - |
| 324 | 10324 | - | - |
| 325 | 10325 | - | - |
| 326 | 10326 | - | - |
| 329 | 10329 | - | - |
| 450 | 10450 | - | - |
| 451 | 10451 | - | - |
| 452 | 10452 | - | - |
| 453 | 10453 | - | - |
| 454 | 10454 | - | - |
| 455 | 10455 | - | - |
| 456 | 10456 | - | - |
| 457 | 10457 | - | - |
| 458 | 10458 | - | - |
| 459 | 10459 | - | - |
| 460 | 10460 | - | - |
| 461 | 10461 | - | - |
| 470 | 10470 | - | - |
| 471 | 10471 | - | - |
| 472 | 10472 | - | - |
| 473 | 10473 | - | - |
| 600 | 10600 | - | - |
| 601 | 10601 | - | - |
| 620 | 10620 | - | - |
| 640 | 10640 | - | - |
| 641 | 10641 | - | - |
| 642 | 10642 | - | - |
| 643 | 10643 | - | - |
| 1280 | 11280 | - | - |
| 1400 | 11400 | - | - |

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
   description ARI-BL-402-SKY_VTEP
   vxlan source-interface Loopback1
   vxlan udp-port 4789
   vxlan vlan 11 vni 10011
   vxlan vlan 12 vni 10012
   vxlan vlan 13 vni 10013
   vxlan vlan 16 vni 10016
   vxlan vlan 18 vni 10018
   vxlan vlan 19 vni 10019
   vxlan vlan 20 vni 10020
   vxlan vlan 21 vni 10021
   vxlan vlan 45 vni 10045
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
   vxlan vlan 200 vni 10200
   vxlan vlan 205 vni 10205
   vxlan vlan 232 vni 10232
   vxlan vlan 233 vni 10233
   vxlan vlan 252 vni 10252
   vxlan vlan 253 vni 10253
   vxlan vlan 254 vni 10254
   vxlan vlan 258 vni 10258
   vxlan vlan 259 vni 10259
   vxlan vlan 260 vni 10260
   vxlan vlan 261 vni 10261
   vxlan vlan 262 vni 10262
   vxlan vlan 263 vni 10263
   vxlan vlan 267 vni 10267
   vxlan vlan 268 vni 10268
   vxlan vlan 269 vni 10269
   vxlan vlan 301 vni 10301
   vxlan vlan 302 vni 10302
   vxlan vlan 303 vni 10303
   vxlan vlan 304 vni 10304
   vxlan vlan 305 vni 10305
   vxlan vlan 306 vni 10306
   vxlan vlan 307 vni 10307
   vxlan vlan 308 vni 10308
   vxlan vlan 309 vni 10309
   vxlan vlan 310 vni 10310
   vxlan vlan 311 vni 10311
   vxlan vlan 312 vni 10312
   vxlan vlan 313 vni 10313
   vxlan vlan 314 vni 10314
   vxlan vlan 315 vni 10315
   vxlan vlan 316 vni 10316
   vxlan vlan 317 vni 10317
   vxlan vlan 318 vni 10318
   vxlan vlan 319 vni 10319
   vxlan vlan 320 vni 10320
   vxlan vlan 321 vni 10321
   vxlan vlan 322 vni 10322
   vxlan vlan 323 vni 10323
   vxlan vlan 324 vni 10324
   vxlan vlan 325 vni 10325
   vxlan vlan 326 vni 10326
   vxlan vlan 329 vni 10329
   vxlan vlan 450 vni 10450
   vxlan vlan 451 vni 10451
   vxlan vlan 452 vni 10452
   vxlan vlan 453 vni 10453
   vxlan vlan 454 vni 10454
   vxlan vlan 455 vni 10455
   vxlan vlan 456 vni 10456
   vxlan vlan 457 vni 10457
   vxlan vlan 458 vni 10458
   vxlan vlan 459 vni 10459
   vxlan vlan 460 vni 10460
   vxlan vlan 461 vni 10461
   vxlan vlan 470 vni 10470
   vxlan vlan 471 vni 10471
   vxlan vlan 472 vni 10472
   vxlan vlan 473 vni 10473
   vxlan vlan 600 vni 10600
   vxlan vlan 601 vni 10601
   vxlan vlan 620 vni 10620
   vxlan vlan 640 vni 10640
   vxlan vlan 641 vni 10641
   vxlan vlan 642 vni 10642
   vxlan vlan 643 vni 10643
   vxlan vlan 1280 vni 11280
   vxlan vlan 1400 vni 11400
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
| 65123 | 10.111.5.26 |

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
| 10.110.1.2 | 65062 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | True | - | - | - | - |
| 10.110.1.4 | 65063 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | True | - | - | - | - |
| 10.111.5.1 | 65101 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 10.111.5.2 | 65101 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 10.111.8.252 | 65101 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 10.111.8.254 | 65101 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |

#### Router BGP EVPN Address Family

- VPN import pruning is **enabled**

##### EVPN Peer Groups

| Peer Group | Activate | Route-map In | Route-map Out | Peer-tag In | Peer-tag Out | Encapsulation | Next-hop-self Source Interface |
| ---------- | -------- | ------------ | ------------- | ----------- | ------------ | ------------- | ------------------------------ |
| EVPN-OVERLAY-PEERS | True | - | - | - | - | default | - |

#### Router BGP VLANs

| VLAN | Route-Distinguisher | Both Route-Target | Import Route Target | Export Route-Target | Redistribute |
| ---- | ------------------- | ----------------- | ------------------- | ------------------- | ------------ |
| 11 | 10.111.5.26:10011 | 10011:10011 | - | - | learned |
| 12 | 10.111.5.26:10012 | 10012:10012 | - | - | learned |
| 13 | 10.111.5.26:10013 | 10013:10013 | - | - | learned |
| 16 | 10.111.5.26:10016 | 10016:10016 | - | - | learned |
| 18 | 10.111.5.26:10018 | 10018:10018 | - | - | learned |
| 19 | 10.111.5.26:10019 | 10019:10019 | - | - | learned |
| 20 | 10.111.5.26:10020 | 10020:10020 | - | - | learned |
| 21 | 10.111.5.26:10021 | 10021:10021 | - | - | learned |
| 45 | 10.111.5.26:10045 | 10045:10045 | - | - | learned |
| 150 | 10.111.5.26:10150 | 10150:10150 | - | - | learned |
| 151 | 10.111.5.26:10151 | 10151:10151 | - | - | learned |
| 152 | 10.111.5.26:10152 | 10152:10152 | - | - | learned |
| 153 | 10.111.5.26:10153 | 10153:10153 | - | - | learned |
| 154 | 10.111.5.26:10154 | 10154:10154 | - | - | learned |
| 155 | 10.111.5.26:10155 | 10155:10155 | - | - | learned |
| 156 | 10.111.5.26:10156 | 10156:10156 | - | - | learned |
| 157 | 10.111.5.26:10157 | 10157:10157 | - | - | learned |
| 158 | 10.111.5.26:10158 | 10158:10158 | - | - | learned |
| 159 | 10.111.5.26:10159 | 10159:10159 | - | - | learned |
| 160 | 10.111.5.26:10160 | 10160:10160 | - | - | learned |
| 161 | 10.111.5.26:10161 | 10161:10161 | - | - | learned |
| 162 | 10.111.5.26:10162 | 10162:10162 | - | - | learned |
| 163 | 10.111.5.26:10163 | 10163:10163 | - | - | learned |
| 164 | 10.111.5.26:10164 | 10164:10164 | - | - | learned |
| 165 | 10.111.5.26:10165 | 10165:10165 | - | - | learned |
| 166 | 10.111.5.26:10166 | 10166:10166 | - | - | learned |
| 167 | 10.111.5.26:10167 | 10167:10167 | - | - | learned |
| 168 | 10.111.5.26:10168 | 10168:10168 | - | - | learned |
| 169 | 10.111.5.26:10169 | 10169:10169 | - | - | learned |
| 170 | 10.111.5.26:10170 | 10170:10170 | - | - | learned |
| 171 | 10.111.5.26:10171 | 10171:10171 | - | - | learned |
| 172 | 10.111.5.26:10172 | 10172:10172 | - | - | learned |
| 173 | 10.111.5.26:10173 | 10173:10173 | - | - | learned |
| 174 | 10.111.5.26:10174 | 10174:10174 | - | - | learned |
| 175 | 10.111.5.26:10175 | 10175:10175 | - | - | learned |
| 176 | 10.111.5.26:10176 | 10176:10176 | - | - | learned |
| 177 | 10.111.5.26:10177 | 10177:10177 | - | - | learned |
| 178 | 10.111.5.26:10178 | 10178:10178 | - | - | learned |
| 179 | 10.111.5.26:10179 | 10179:10179 | - | - | learned |
| 180 | 10.111.5.26:10180 | 10180:10180 | - | - | learned |
| 181 | 10.111.5.26:10181 | 10181:10181 | - | - | learned |
| 182 | 10.111.5.26:10182 | 10182:10182 | - | - | learned |
| 183 | 10.111.5.26:10183 | 10183:10183 | - | - | learned |
| 200 | 10.111.5.26:10200 | 10200:10200 | - | - | learned |
| 205 | 10.111.5.26:10205 | 10205:10205 | - | - | learned |
| 232 | 10.111.5.26:10232 | 10232:10232 | - | - | learned |
| 233 | 10.111.5.26:10233 | 10233:10233 | - | - | learned |
| 252 | 10.111.5.26:10252 | 10252:10252 | - | - | learned |
| 253 | 10.111.5.26:10253 | 10253:10253 | - | - | learned |
| 254 | 10.111.5.26:10254 | 10254:10254 | - | - | learned |
| 258 | 10.111.5.26:10258 | 10258:10258 | - | - | learned |
| 259 | 10.111.5.26:10259 | 10259:10259 | - | - | learned |
| 260 | 10.111.5.26:10260 | 10260:10260 | - | - | learned |
| 261 | 10.111.5.26:10261 | 10261:10261 | - | - | learned |
| 262 | 10.111.5.26:10262 | 10262:10262 | - | - | learned |
| 263 | 10.111.5.26:10263 | 10263:10263 | - | - | learned |
| 267 | 10.111.5.26:10267 | 10267:10267 | - | - | learned |
| 268 | 10.111.5.26:10268 | 10268:10268 | - | - | learned |
| 269 | 10.111.5.26:10269 | 10269:10269 | - | - | learned |
| 301 | 10.111.5.26:10301 | 10301:10301 | - | - | learned |
| 302 | 10.111.5.26:10302 | 10302:10302 | - | - | learned |
| 303 | 10.111.5.26:10303 | 10303:10303 | - | - | learned |
| 304 | 10.111.5.26:10304 | 10304:10304 | - | - | learned |
| 305 | 10.111.5.26:10305 | 10305:10305 | - | - | learned |
| 306 | 10.111.5.26:10306 | 10306:10306 | - | - | learned |
| 307 | 10.111.5.26:10307 | 10307:10307 | - | - | learned |
| 308 | 10.111.5.26:10308 | 10308:10308 | - | - | learned |
| 309 | 10.111.5.26:10309 | 10309:10309 | - | - | learned |
| 310 | 10.111.5.26:10310 | 10310:10310 | - | - | learned |
| 311 | 10.111.5.26:10311 | 10311:10311 | - | - | learned |
| 312 | 10.111.5.26:10312 | 10312:10312 | - | - | learned |
| 313 | 10.111.5.26:10313 | 10313:10313 | - | - | learned |
| 314 | 10.111.5.26:10314 | 10314:10314 | - | - | learned |
| 315 | 10.111.5.26:10315 | 10315:10315 | - | - | learned |
| 316 | 10.111.5.26:10316 | 10316:10316 | - | - | learned |
| 317 | 10.111.5.26:10317 | 10317:10317 | - | - | learned |
| 318 | 10.111.5.26:10318 | 10318:10318 | - | - | learned |
| 319 | 10.111.5.26:10319 | 10319:10319 | - | - | learned |
| 320 | 10.111.5.26:10320 | 10320:10320 | - | - | learned |
| 321 | 10.111.5.26:10321 | 10321:10321 | - | - | learned |
| 322 | 10.111.5.26:10322 | 10322:10322 | - | - | learned |
| 323 | 10.111.5.26:10323 | 10323:10323 | - | - | learned |
| 324 | 10.111.5.26:10324 | 10324:10324 | - | - | learned |
| 325 | 10.111.5.26:10325 | 10325:10325 | - | - | learned |
| 326 | 10.111.5.26:10326 | 10326:10326 | - | - | learned |
| 329 | 10.111.5.26:10329 | 10329:10329 | - | - | learned |
| 450 | 10.111.5.26:10450 | 10450:10450 | - | - | learned |
| 451 | 10.111.5.26:10451 | 10451:10451 | - | - | learned |
| 452 | 10.111.5.26:10452 | 10452:10452 | - | - | learned |
| 453 | 10.111.5.26:10453 | 10453:10453 | - | - | learned |
| 454 | 10.111.5.26:10454 | 10454:10454 | - | - | learned |
| 455 | 10.111.5.26:10455 | 10455:10455 | - | - | learned |
| 456 | 10.111.5.26:10456 | 10456:10456 | - | - | learned |
| 457 | 10.111.5.26:10457 | 10457:10457 | - | - | learned |
| 458 | 10.111.5.26:10458 | 10458:10458 | - | - | learned |
| 459 | 10.111.5.26:10459 | 10459:10459 | - | - | learned |
| 460 | 10.111.5.26:10460 | 10460:10460 | - | - | learned |
| 461 | 10.111.5.26:10461 | 10461:10461 | - | - | learned |
| 470 | 10.111.5.26:10470 | 10470:10470 | - | - | learned |
| 471 | 10.111.5.26:10471 | 10471:10471 | - | - | learned |
| 472 | 10.111.5.26:10472 | 10472:10472 | - | - | learned |
| 473 | 10.111.5.26:10473 | 10473:10473 | - | - | learned |
| 600 | 10.111.5.26:10600 | 10600:10600 | - | - | learned |
| 601 | 10.111.5.26:10601 | 10601:10601 | - | - | learned |
| 620 | 10.111.5.26:10620 | 10620:10620 | - | - | learned |
| 640 | 10.111.5.26:10640 | 10640:10640 | - | - | learned |
| 641 | 10.111.5.26:10641 | 10641:10641 | - | - | learned |
| 642 | 10.111.5.26:10642 | 10642:10642 | - | - | learned |
| 643 | 10.111.5.26:10643 | 10643:10643 | - | - | learned |
| 1280 | 10.111.5.26:11280 | 11280:11280 | - | - | learned |
| 1400 | 10.111.5.26:11400 | 11400:11400 | - | - | learned |

#### Router BGP VRFs

| VRF | Route-Distinguisher | Redistribute | Graceful Restart |
| --- | ------------------- | ------------ | ---------------- |
| VRF-NEXTGEN_DESARROLLO | 10.111.5.26:1002 | connected | - |
| VRF-NEXTGEN_DMZ_FRONT | 10.111.5.26:1004 | connected | - |
| VRF-NEXTGEN_DMZ_INT | 10.111.5.26:1003 | connected | - |
| VRF-NEXTGEN_MGMT | 10.111.5.26:1005 | connected<br>static | - |
| VRF-NEXTGEN_MGMT_DMZ | 10.111.5.26:1006 | connected<br>static | - |
| VRF-NEXTGEN_PRODUCCION | 10.111.5.26:1001 | connected | - |

#### Router BGP Device Configuration

```eos
!
router bgp 65123
   router-id 10.111.5.26
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
   neighbor 10.110.1.2 peer group IPv4-UNDERLAY-PEERS
   neighbor 10.110.1.2 remote-as 65062
   neighbor 10.110.1.2 bfd
   neighbor 10.110.1.2 description ARI-BL-301-MTZ
   neighbor 10.110.1.4 peer group IPv4-UNDERLAY-PEERS
   neighbor 10.110.1.4 remote-as 65063
   neighbor 10.110.1.4 bfd
   neighbor 10.110.1.4 description ARI-BL-302-MTZ
   neighbor 10.111.5.1 peer group EVPN-OVERLAY-PEERS
   neighbor 10.111.5.1 remote-as 65101
   neighbor 10.111.5.1 description ARI-SP-401-SKY_Loopback0
   neighbor 10.111.5.2 peer group EVPN-OVERLAY-PEERS
   neighbor 10.111.5.2 remote-as 65101
   neighbor 10.111.5.2 description ARI-SP-402-SKY_Loopback0
   neighbor 10.111.8.252 peer group IPv4-UNDERLAY-PEERS
   neighbor 10.111.8.252 remote-as 65101
   neighbor 10.111.8.252 description ARI-SP-401-SKY_Ethernet8
   neighbor 10.111.8.254 peer group IPv4-UNDERLAY-PEERS
   neighbor 10.111.8.254 remote-as 65101
   neighbor 10.111.8.254 description ARI-SP-402-SKY_Ethernet8
   redistribute connected route-map RM-CONN-2-BGP
   !
   vlan 11
      rd 10.111.5.26:10011
      route-target both 10011:10011
      redistribute learned
   !
   vlan 12
      rd 10.111.5.26:10012
      route-target both 10012:10012
      redistribute learned
   !
   vlan 13
      rd 10.111.5.26:10013
      route-target both 10013:10013
      redistribute learned
   !
   vlan 16
      rd 10.111.5.26:10016
      route-target both 10016:10016
      redistribute learned
   !
   vlan 18
      rd 10.111.5.26:10018
      route-target both 10018:10018
      redistribute learned
   !
   vlan 19
      rd 10.111.5.26:10019
      route-target both 10019:10019
      redistribute learned
   !
   vlan 20
      rd 10.111.5.26:10020
      route-target both 10020:10020
      redistribute learned
   !
   vlan 21
      rd 10.111.5.26:10021
      route-target both 10021:10021
      redistribute learned
   !
   vlan 45
      rd 10.111.5.26:10045
      route-target both 10045:10045
      redistribute learned
   !
   vlan 150
      rd 10.111.5.26:10150
      route-target both 10150:10150
      redistribute learned
   !
   vlan 151
      rd 10.111.5.26:10151
      route-target both 10151:10151
      redistribute learned
   !
   vlan 152
      rd 10.111.5.26:10152
      route-target both 10152:10152
      redistribute learned
   !
   vlan 153
      rd 10.111.5.26:10153
      route-target both 10153:10153
      redistribute learned
   !
   vlan 154
      rd 10.111.5.26:10154
      route-target both 10154:10154
      redistribute learned
   !
   vlan 155
      rd 10.111.5.26:10155
      route-target both 10155:10155
      redistribute learned
   !
   vlan 156
      rd 10.111.5.26:10156
      route-target both 10156:10156
      redistribute learned
   !
   vlan 157
      rd 10.111.5.26:10157
      route-target both 10157:10157
      redistribute learned
   !
   vlan 158
      rd 10.111.5.26:10158
      route-target both 10158:10158
      redistribute learned
   !
   vlan 159
      rd 10.111.5.26:10159
      route-target both 10159:10159
      redistribute learned
   !
   vlan 160
      rd 10.111.5.26:10160
      route-target both 10160:10160
      redistribute learned
   !
   vlan 161
      rd 10.111.5.26:10161
      route-target both 10161:10161
      redistribute learned
   !
   vlan 162
      rd 10.111.5.26:10162
      route-target both 10162:10162
      redistribute learned
   !
   vlan 163
      rd 10.111.5.26:10163
      route-target both 10163:10163
      redistribute learned
   !
   vlan 164
      rd 10.111.5.26:10164
      route-target both 10164:10164
      redistribute learned
   !
   vlan 165
      rd 10.111.5.26:10165
      route-target both 10165:10165
      redistribute learned
   !
   vlan 166
      rd 10.111.5.26:10166
      route-target both 10166:10166
      redistribute learned
   !
   vlan 167
      rd 10.111.5.26:10167
      route-target both 10167:10167
      redistribute learned
   !
   vlan 168
      rd 10.111.5.26:10168
      route-target both 10168:10168
      redistribute learned
   !
   vlan 169
      rd 10.111.5.26:10169
      route-target both 10169:10169
      redistribute learned
   !
   vlan 170
      rd 10.111.5.26:10170
      route-target both 10170:10170
      redistribute learned
   !
   vlan 171
      rd 10.111.5.26:10171
      route-target both 10171:10171
      redistribute learned
   !
   vlan 172
      rd 10.111.5.26:10172
      route-target both 10172:10172
      redistribute learned
   !
   vlan 173
      rd 10.111.5.26:10173
      route-target both 10173:10173
      redistribute learned
   !
   vlan 174
      rd 10.111.5.26:10174
      route-target both 10174:10174
      redistribute learned
   !
   vlan 175
      rd 10.111.5.26:10175
      route-target both 10175:10175
      redistribute learned
   !
   vlan 176
      rd 10.111.5.26:10176
      route-target both 10176:10176
      redistribute learned
   !
   vlan 177
      rd 10.111.5.26:10177
      route-target both 10177:10177
      redistribute learned
   !
   vlan 178
      rd 10.111.5.26:10178
      route-target both 10178:10178
      redistribute learned
   !
   vlan 179
      rd 10.111.5.26:10179
      route-target both 10179:10179
      redistribute learned
   !
   vlan 180
      rd 10.111.5.26:10180
      route-target both 10180:10180
      redistribute learned
   !
   vlan 181
      rd 10.111.5.26:10181
      route-target both 10181:10181
      redistribute learned
   !
   vlan 182
      rd 10.111.5.26:10182
      route-target both 10182:10182
      redistribute learned
   !
   vlan 183
      rd 10.111.5.26:10183
      route-target both 10183:10183
      redistribute learned
   !
   vlan 200
      rd 10.111.5.26:10200
      route-target both 10200:10200
      redistribute learned
   !
   vlan 205
      rd 10.111.5.26:10205
      route-target both 10205:10205
      redistribute learned
   !
   vlan 232
      rd 10.111.5.26:10232
      route-target both 10232:10232
      redistribute learned
   !
   vlan 233
      rd 10.111.5.26:10233
      route-target both 10233:10233
      redistribute learned
   !
   vlan 252
      rd 10.111.5.26:10252
      route-target both 10252:10252
      redistribute learned
   !
   vlan 253
      rd 10.111.5.26:10253
      route-target both 10253:10253
      redistribute learned
   !
   vlan 254
      rd 10.111.5.26:10254
      route-target both 10254:10254
      redistribute learned
   !
   vlan 258
      rd 10.111.5.26:10258
      route-target both 10258:10258
      redistribute learned
   !
   vlan 259
      rd 10.111.5.26:10259
      route-target both 10259:10259
      redistribute learned
   !
   vlan 260
      rd 10.111.5.26:10260
      route-target both 10260:10260
      redistribute learned
   !
   vlan 261
      rd 10.111.5.26:10261
      route-target both 10261:10261
      redistribute learned
   !
   vlan 262
      rd 10.111.5.26:10262
      route-target both 10262:10262
      redistribute learned
   !
   vlan 263
      rd 10.111.5.26:10263
      route-target both 10263:10263
      redistribute learned
   !
   vlan 267
      rd 10.111.5.26:10267
      route-target both 10267:10267
      redistribute learned
   !
   vlan 268
      rd 10.111.5.26:10268
      route-target both 10268:10268
      redistribute learned
   !
   vlan 269
      rd 10.111.5.26:10269
      route-target both 10269:10269
      redistribute learned
   !
   vlan 301
      rd 10.111.5.26:10301
      route-target both 10301:10301
      redistribute learned
   !
   vlan 302
      rd 10.111.5.26:10302
      route-target both 10302:10302
      redistribute learned
   !
   vlan 303
      rd 10.111.5.26:10303
      route-target both 10303:10303
      redistribute learned
   !
   vlan 304
      rd 10.111.5.26:10304
      route-target both 10304:10304
      redistribute learned
   !
   vlan 305
      rd 10.111.5.26:10305
      route-target both 10305:10305
      redistribute learned
   !
   vlan 306
      rd 10.111.5.26:10306
      route-target both 10306:10306
      redistribute learned
   !
   vlan 307
      rd 10.111.5.26:10307
      route-target both 10307:10307
      redistribute learned
   !
   vlan 308
      rd 10.111.5.26:10308
      route-target both 10308:10308
      redistribute learned
   !
   vlan 309
      rd 10.111.5.26:10309
      route-target both 10309:10309
      redistribute learned
   !
   vlan 310
      rd 10.111.5.26:10310
      route-target both 10310:10310
      redistribute learned
   !
   vlan 311
      rd 10.111.5.26:10311
      route-target both 10311:10311
      redistribute learned
   !
   vlan 312
      rd 10.111.5.26:10312
      route-target both 10312:10312
      redistribute learned
   !
   vlan 313
      rd 10.111.5.26:10313
      route-target both 10313:10313
      redistribute learned
   !
   vlan 314
      rd 10.111.5.26:10314
      route-target both 10314:10314
      redistribute learned
   !
   vlan 315
      rd 10.111.5.26:10315
      route-target both 10315:10315
      redistribute learned
   !
   vlan 316
      rd 10.111.5.26:10316
      route-target both 10316:10316
      redistribute learned
   !
   vlan 317
      rd 10.111.5.26:10317
      route-target both 10317:10317
      redistribute learned
   !
   vlan 318
      rd 10.111.5.26:10318
      route-target both 10318:10318
      redistribute learned
   !
   vlan 319
      rd 10.111.5.26:10319
      route-target both 10319:10319
      redistribute learned
   !
   vlan 320
      rd 10.111.5.26:10320
      route-target both 10320:10320
      redistribute learned
   !
   vlan 321
      rd 10.111.5.26:10321
      route-target both 10321:10321
      redistribute learned
   !
   vlan 322
      rd 10.111.5.26:10322
      route-target both 10322:10322
      redistribute learned
   !
   vlan 323
      rd 10.111.5.26:10323
      route-target both 10323:10323
      redistribute learned
   !
   vlan 324
      rd 10.111.5.26:10324
      route-target both 10324:10324
      redistribute learned
   !
   vlan 325
      rd 10.111.5.26:10325
      route-target both 10325:10325
      redistribute learned
   !
   vlan 326
      rd 10.111.5.26:10326
      route-target both 10326:10326
      redistribute learned
   !
   vlan 329
      rd 10.111.5.26:10329
      route-target both 10329:10329
      redistribute learned
   !
   vlan 450
      rd 10.111.5.26:10450
      route-target both 10450:10450
      redistribute learned
   !
   vlan 451
      rd 10.111.5.26:10451
      route-target both 10451:10451
      redistribute learned
   !
   vlan 452
      rd 10.111.5.26:10452
      route-target both 10452:10452
      redistribute learned
   !
   vlan 453
      rd 10.111.5.26:10453
      route-target both 10453:10453
      redistribute learned
   !
   vlan 454
      rd 10.111.5.26:10454
      route-target both 10454:10454
      redistribute learned
   !
   vlan 455
      rd 10.111.5.26:10455
      route-target both 10455:10455
      redistribute learned
   !
   vlan 456
      rd 10.111.5.26:10456
      route-target both 10456:10456
      redistribute learned
   !
   vlan 457
      rd 10.111.5.26:10457
      route-target both 10457:10457
      redistribute learned
   !
   vlan 458
      rd 10.111.5.26:10458
      route-target both 10458:10458
      redistribute learned
   !
   vlan 459
      rd 10.111.5.26:10459
      route-target both 10459:10459
      redistribute learned
   !
   vlan 460
      rd 10.111.5.26:10460
      route-target both 10460:10460
      redistribute learned
   !
   vlan 461
      rd 10.111.5.26:10461
      route-target both 10461:10461
      redistribute learned
   !
   vlan 470
      rd 10.111.5.26:10470
      route-target both 10470:10470
      redistribute learned
   !
   vlan 471
      rd 10.111.5.26:10471
      route-target both 10471:10471
      redistribute learned
   !
   vlan 472
      rd 10.111.5.26:10472
      route-target both 10472:10472
      redistribute learned
   !
   vlan 473
      rd 10.111.5.26:10473
      route-target both 10473:10473
      redistribute learned
   !
   vlan 600
      rd 10.111.5.26:10600
      route-target both 10600:10600
      redistribute learned
   !
   vlan 601
      rd 10.111.5.26:10601
      route-target both 10601:10601
      redistribute learned
   !
   vlan 620
      rd 10.111.5.26:10620
      route-target both 10620:10620
      redistribute learned
   !
   vlan 640
      rd 10.111.5.26:10640
      route-target both 10640:10640
      redistribute learned
   !
   vlan 641
      rd 10.111.5.26:10641
      route-target both 10641:10641
      redistribute learned
   !
   vlan 642
      rd 10.111.5.26:10642
      route-target both 10642:10642
      redistribute learned
   !
   vlan 643
      rd 10.111.5.26:10643
      route-target both 10643:10643
      redistribute learned
   !
   vlan 1280
      rd 10.111.5.26:11280
      route-target both 11280:11280
      redistribute learned
   !
   vlan 1400
      rd 10.111.5.26:11400
      route-target both 11400:11400
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
      rd 10.111.5.26:1002
      route-target import evpn 1002:1002
      route-target export evpn 1002:1002
      router-id 10.111.5.26
      redistribute connected
   !
   vrf VRF-NEXTGEN_DMZ_FRONT
      rd 10.111.5.26:1004
      route-target import evpn 1004:1004
      route-target export evpn 1004:1004
      router-id 10.111.5.26
      redistribute connected
   !
   vrf VRF-NEXTGEN_DMZ_INT
      rd 10.111.5.26:1003
      route-target import evpn 1003:1003
      route-target export evpn 1003:1003
      router-id 10.111.5.26
      redistribute connected
   !
   vrf VRF-NEXTGEN_MGMT
      rd 10.111.5.26:1005
      route-target import evpn 1005:1005
      route-target export evpn 1005:1005
      router-id 10.111.5.26
      redistribute connected
      redistribute static
   !
   vrf VRF-NEXTGEN_MGMT_DMZ
      rd 10.111.5.26:1006
      route-target import evpn 1006:1006
      route-target export evpn 1006:1006
      router-id 10.111.5.26
      redistribute connected
      redistribute static
   !
   vrf VRF-NEXTGEN_PRODUCCION
      rd 10.111.5.26:1001
      route-target import evpn 1001:1001
      route-target export evpn 1001:1001
      router-id 10.111.5.26
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
   seq 10 permit 10.111.5.0/24 eq 32
   seq 20 permit 10.111.6.0/24 eq 32
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
| VRF-NEXTGEN_DESARROLLO | 10.111.7.26 | - |
| VRF-NEXTGEN_DMZ_FRONT | 10.111.7.26 | - |
| VRF-NEXTGEN_DMZ_INT | 10.111.7.26 | - |
| VRF-NEXTGEN_MGMT | 10.111.7.26 | - |
| VRF-NEXTGEN_MGMT_DMZ | 10.111.7.26 | - |
| VRF-NEXTGEN_PRODUCCION | 10.111.7.26 | - |

### Virtual Source NAT Configuration

```eos
!
ip address virtual source-nat vrf VRF-NEXTGEN_DESARROLLO address 10.111.7.26
ip address virtual source-nat vrf VRF-NEXTGEN_DMZ_FRONT address 10.111.7.26
ip address virtual source-nat vrf VRF-NEXTGEN_DMZ_INT address 10.111.7.26
ip address virtual source-nat vrf VRF-NEXTGEN_MGMT address 10.111.7.26
ip address virtual source-nat vrf VRF-NEXTGEN_MGMT_DMZ address 10.111.7.26
ip address virtual source-nat vrf VRF-NEXTGEN_PRODUCCION address 10.111.7.26
```

## Errdisable

### Errdisable Summary

Errdisable recovery timer interval: 30 seconds

```eos
!
errdisable recovery interval 30
```
