# 🧪 VTP Transparent Mode Lab

## 🎯 Objective

Configure a Cisco switching topology using VTP Transparent mode
to understand how a transparent switch maintains its own VLAN
database and forwards VTP advertisements without synchronizing
its local VLAN information with other switches.

This lab demonstrates:

- VTP Server mode
- VTP Transparent mode
- Local VLAN creation
- VLAN database independence
- 802.1Q trunking
- VLAN propagation across trunk links
- VTP advertisement forwarding

## 🖥️ Topology

```text
        CLIENT
   VLAN 10 / 20 / 30
          |
        Gi0/0
          |
        Gi0/1
     TRANSPARENT
      VLAN 40 / 50
        Gi0/0
          |
        Gi0/0
          |
        SERVER
   VLAN 10 / 20 / 30
```
<br>
🌐 VLAN Configuration
🔴 CLIENT Switch
VLAN	Purpose
VLAN 10	User Network
VLAN 20	User Network
VLAN 30	User Network
<br>
🔵 TRANSPARENT Switch
VLAN	Purpose
VLAN 40	Local VLAN
VLAN 50	Local VLAN
<br>
🔴 SERVER Switch
VLAN	Purpose
VLAN 10	User Network
VLAN 20	User Network
VLAN 30	User Network
<br>
🔧 Technologies
Cisco IOS
VTP
VTP Transparent Mode
VTP Server Mode
VTP Client Mode
802.1Q Trunking
VLAN
Layer 2 Switching
MAC Address Learning
<br>
⚙️ VTP Configuration
🔴 CLIENT Switch

VTP Mode: Server

The CLIENT switch operates as the VTP Server and maintains
the VLAN database for:

VLAN 10
VLAN 20
VLAN 30
<br>
🔵 TRANSPARENT Switch

VTP Mode: Transparent

The TRANSPARENT switch maintains its own local VLAN database.

It does not synchronize its VLAN database with the VTP Server.

Locally configured VLANs:

VLAN 40
VLAN 50
<br>
🔴 SERVER Switch

VTP Mode: Client

The SERVER switch operates as a VTP Client and receives VLAN
information through VTP advertisements.

Expected VLANs:

VLAN 10
VLAN 20
VLAN 30
<br>
🔗 Trunk Configuration

The inter-switch links are configured as 802.1Q trunk links.

CLIENT
   |
   | 802.1Q Trunk
   |
TRANSPARENT
   |
   | 802.1Q Trunk
   |
SERVER
<br>

The trunk links allow multiple VLANs to traverse a single
physical connection.

<br>
🔍 Verification
📋 Check VTP Status
show vtp status

Verify the VTP mode on each switch.

Expected:

CLIENT        → Server
TRANSPARENT   → Transparent
SERVER        → Client
<br>
📋 Check VLAN Database
show vlan brief

Verify:

CLIENT        → VLAN 10, 20, 30
TRANSPARENT   → VLAN 40, 50
SERVER        → VLAN 10, 20, 30
<br>
📋 Check Trunk Status
show interfaces trunk

Verify that the inter-switch interfaces are operating as
802.1Q trunk links.

<br>
📋 Check VTP Configuration
show vtp status

Verify:

VTP Domain
VTP Mode
VTP Version
Configuration Revision
<br>
📊 VTP Communication Process
🔄 VTP Transparent Operation
<br>
📌 VTP Transparent Behavior

The Transparent switch behaves differently from a VTP Client.

It:

Maintains its own VLAN database.
Does not synchronize its VLAN database with the VTP Server.
Can create VLANs locally.
Maintains locally configured VLANs such as VLAN 40 and VLAN 50.
Forwards VTP advertisements through trunk links when applicable.
<br>
🧪 VLAN Database Verification
🔴 CLIENT
show vlan brief

Expected VLANs:

10
20
30
<br>
🔵 TRANSPARENT
show vlan brief

Expected VLANs:

40
50
<br>
🔴 SERVER
show vlan brief

Expected VLANs:

10
20
30
<br>
🧠 Key Learning
VTP Server Mode
VTP Client Mode
VTP Transparent Mode
VTP VLAN Synchronization
VLAN Database Independence
VTP Advertisement Forwarding
802.1Q Trunking
VLAN Propagation
Layer 2 Switching
VLAN Database Verification
<br>
✅ Result

The topology successfully demonstrates VTP Transparent mode.

The TRANSPARENT switch maintains its own local VLAN database
containing VLAN 40 and VLAN 50 instead of synchronizing its
local VLAN database with the VTP Server.

The inter-switch links operate as 802.1Q trunks, allowing
VLAN traffic and VTP advertisements to traverse the links.

This lab demonstrates how VTP Server, Client, and Transparent
modes behave differently within a Cisco switching environment.

<br>
