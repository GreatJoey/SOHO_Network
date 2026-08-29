# SOHO_Network
A Simple Office/ Home Office network made in Cisco packet tracer. 

| Device 1 | Interface | Connection | Device 2     | Interface |
| -------- | --------- | ---------- | ------------ | --------- |
| R1       | G0/0      | ↔          | R2           | G0/1      |
| R2       | G0/0      | ↔          | SW1          | G0/1      |
| SW1      | F0/1      | ↔          | PC1          | NIC       |
| SW1      | F0/2      | ↔          | Laptop       | NIC       |
| SW1      | F0/3      | ↔          | Access Point | NIC       |

All you need is a 
- 2 2960 Routers
- 1 2911 Switch
- Access Point
- Some end devices
- Server (To act as internet)

Connect everything with straight-through cables. All devices have Auto-MDIX so don't worry about the cable types.

Then paste the commands from the Method of Procedures file.

**Network Topology**


<img width="750" height="500" alt="image" src="https://github.com/GreatJoey/SOHO_Network/blob/main/SOHO%20Network/SOHO_Topology.png" />
