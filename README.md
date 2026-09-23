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
🌐 VLAN Configuration
CLIENT Switch
VLAN	Purpose
VLAN 10	User Network
VLAN 20	User Network
VLAN 30	User Network
TRANSPARENT Switch
VLAN	Purpose
VLAN 40	Local VLAN
VLAN 50	Local VLAN
SERVER Switch
VLAN	Purpose
VLAN 10	User Network
VLAN 20	User Network
VLAN 30	User Network
🔧 Technologies
Cisco IOS
VTP
VTP Transparent Mode
802.1Q Trunking
VLAN
Layer 2 Switching
MAC Address Learning
⚙️ VTP Configuration
CLIENT Switch
VTP Mode: Server

The CLIENT switch operates as the VTP Server and maintains
the VLAN database for VLAN 10, VLAN 20, and VLAN 30.

TRANSPARENT Switch
VTP Mode: Transparent

The TRANSPARENT switch maintains its own local VLAN database.

It does not synchronize its VLAN database with the VTP Server.

Locally configured VLANs:

VLAN 40
VLAN 50
SERVER Switch
VTP Mode: Client

The SERVER switch receives VTP information and learns VLAN
information from the VTP domain.

🔗 Trunk Configuration

The inter-switch links are configured as 802.1Q trunks.

CLIENT
   |
   | 802.1Q Trunk
   |
TRANSPARENT
   |
   | 802.1Q Trunk
   |
SERVER

The trunk links allow multiple VLANs to traverse a single
physical connection.

🔍 Verification
Check VTP Status
show vtp status

Verify the VTP mode on each switch.

Expected:

CLIENT        → Server
TRANSPARENT   → Transparent
SERVER        → Client
Check VLAN Database
show vlan brief

Verify:

CLIENT → VLAN 10, 20, 30
TRANSPARENT → VLAN 40, 50
SERVER → VLAN 10, 20, 30
Check Trunk Status
show interfaces trunk

Verify that the inter-switch interfaces are operating as trunks.

Check VTP Configuration
show vtp status

Verify:

VTP domain
VTP mode
VTP version
Configuration revision
📊 Communication Process
VTP Transparent Operation
📌 VTP Transparent Behavior

The Transparent switch behaves differently from a VTP Client.

It:

Maintains its own VLAN database.
Does not learn VLAN configuration from the VTP Server.
Does not synchronize its local VLAN database.
Can have locally created VLANs such as VLAN 40 and VLAN 50.
Forwards VTP advertisements through trunk links when applicable.
🧪 VLAN Database Verification
CLIENT
show vlan brief

Expected VLANs:

10
20
30
TRANSPARENT
show vlan brief

Expected VLANs:

40
50
SERVER
show vlan brief

Expected VLANs:

10
20
30
🧠 Key Learning
VTP Server mode
VTP Client mode
VTP Transparent mode
VTP VLAN synchronization
VLAN database independence
VTP advertisement forwarding
802.1Q trunking
VLAN propagation
Layer 2 switching
✅ Result

The topology successfully demonstrates VTP Transparent mode.

The TRANSPARENT switch maintains its own local VLAN database
containing VLAN 40 and VLAN 50 instead of synchronizing its VLAN
database with the VTP Server.

The trunk links provide the Layer 2 path between the switches,
while the VTP modes determine how VLAN information is handled.
