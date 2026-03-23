# MAP-T Implementation in RDK-B — Open Source Contributions

This page documents my open source contributions to the MAP-T (Mapping of Address 
and Port — Translation) implementation in the RDK-B broadband gateway platform, 
deployed across SKY UK and SKY Italia broadband gateways.

For a full technical write-up of this work, see:  
**[How We Built One of Europe's First Large-Scale MAP-T Deployments on RDK-B]([https://dev.to/saheer_kottakkadan_e51832](https://dev.to/saheer_k6512/how-we-built-one-of-europes-first-large-scale-map-t-deployments-on-rdk-b-3go9])**

---

## Background

MAP-T (RFC 7599) is a stateless IPv6 transition mechanism that allows ISPs to operate 
a pure IPv6 core network while delivering IPv4 connectivity to subscribers — without 
maintaining per-session state on border routers. On 25 November 2019, RIPE NCC 
officially ran out of IPv4 addresses, making IPv6 transition mechanisms like MAP-T 
a critical infrastructure priority for European ISPs.

This work was implemented as part of SKY UK's broadband gateway programme on the 
RDK-B platform and subsequently contributed upstream to the open-source RDK-B 
codebase.

---

## Repositories and Commits

### 1. rdkcentral/wan-manager
**Repository:** https://github.com/rdkcentral/wan-manager  
**Description:** Core WAN state machine — manages WAN interface lifecycle, 
DHCPv6 provisioning, route monitoring, and connection recovery.

| Commit | Description |
|--------|-------------|
| `cd2c1ac` | Initial MAP-T integration in wan-manager state machine |
| `9d79cb5` | RFC data model implementation for MAP-T (RDKB-40298/40299) |
| `2f3f077` | MAP-T IPv6 default route management under route monitor |
| `e6b343b` | MAP-T support in Dibbler DHCPv6 client |
| `c9254e1` | MAP-T and IPv6 teardown on physical link down |
| `854451c` | Crash recovery handling in MAP-T setup |
| `de21f93` | Connection recovery after network outage |
| `6224130` | Fix udhcpc process not terminating in MAP-T mode |
| `5f83f98` | Standardise MAP-T log file naming |
| `d5ce0f3` | Fix MAP-T DMLs not enabled on WanAgent downgrade |
| `3efd7a9` | Fix MAP-T status showing N/A in WAN manager log |
| `7146ebb` | Move MAP-T logs to non-volatile memory |
| `a8d8715` | Fix MAP-T ratio showing 0 in 1:1 port ratio scenario |
| `bab53df` | Fix intermittent WAN IPv6 down issue |

---

### 2. lgirdk/ccsp-p-and-m
**Repository:** https://github.com/lgirdk/ccsp-p-and-m  
**Description:** CCSP Provisioning and Management component — TR-181 data model 
exposure over TR-069/WebPA, DHCPv6 client integration.

| Commit | Description |
|--------|-------------|
| `74323b21f` | MAP-T support in Dibbler DHCPv6 client and wan-manager |
| `d8a8a24ac` | RFC data model implementation for MAP-T (RDKB-40298/40299) |
| `b3436b4d7` | Implement MAP-T TR-181 data model |
| `071f3d834` | Implement MAP-T TR-181 data model (follow-up) |
| `c20bc1833` | Fix MAP-T data model IP prefix values |
| `bbd9ffd13` | Fix MAP-T data model IP prefix values (follow-up) |
| `8de60ee48` | Dibbler client restart via selfheal |
| `dd7d7c0d9` | Fix Dibbler server not running at bootup |
| `e071f6664` | Fix Dibbler server not running at bootup (follow-up) |
| `893b1aae8` | Fix IPv6 state in wanshow on lease period change |
| `cb0be6885` | Fix IPv6 state in wanshow on lease period change (follow-up) |

---

### 3. rdkcmf/rdkb-RdkVlanBridgingManager
**Repository:** https://github.com/rdkcmf/rdkb-RdkVlanBridgingManager  
**Description:** VLAN and bridging management — handles MAP-T virtual interface 
within the gateway bridging topology.

| Commit | Description |
|--------|-------------|
| `3239296` | Pointer initialisation fix in rbus API calls |

---

### 4. rdkcmf/rdk-rdk_logger
**Repository:** https://github.com/rdkcmf/rdk-rdk_logger  
**Description:** Platform logging component — routes MAP-T diagnostic logs to 
non-volatile storage for field diagnostics.

| Commit | Description |
|--------|-------------|
| `03cded2` | Move MAP-T logs to non-volatile memory |

---

## Summary

| Repository | Commits | Area |
|------------|---------|------|
| rdkcentral/wan-manager | 14 | WAN state machine, DHCPv6, route management |
| lgirdk/ccsp-p-and-m | 11 | TR-181 data model, DHCPv6 client |
| rdkcmf/rdkb-RdkVlanBridgingManager | 1 | VLAN/bridging |
| rdkcmf/rdk-rdk_logger | 1 | Platform logging |
| **Total** | **27** | |

---

## Technical Article

Full technical write-up covering the architecture, implementation details, 
and lessons learned:

👉 **[How We Built One of Europe's First Large-Scale MAP-T Deployments on RDK-B](https://dev.to/saheer_kottakkadan_e51832)**

---

## About

Senior Embedded Software Engineer with 12 years of experience in embedded Linux, 
IoT, and broadband gateway platforms.

- Blog: [dev.to/saheer_k](https://dev.to/saheer_k6512)
- GitHub: [github.com/saheerskt](https://github.com/saheerskt)
