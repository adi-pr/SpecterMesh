# SpecterMesh

Autonomous lateral movement and multi-hop P2P routing simulation.

SpecterMesh is a Linux network security project that simulates passive network reconnaissance, host pivoting, and decentralized peer-to-peer (P2P) command-and-control (C2) overlays within containerized environments.

Instead of relying on loud active network scanning or direct, visible outbound phone calls, SpecterMesh operates entirely via passive local inference and recursive multi-hop transport.

An agent deployed on a foothold machine maps adjacent infrastructure silently, propagates itself across authorized boundaries, and weaves an encrypted, ad-hoc communications mesh that relays telemetry back through intermediate nodes.

SpecterMesh does not use zero-day exploits or unpatched vulnerabilities. Propagation and routing are driven by local artifact parsing, concurrent worker pools, secure native protocols (SSH/SCP), and a custom multi-hop packet relay engine.

> One mesh network. Invisible egress routing.

## The Idea

Traditional adversary emulation frameworks are predictable: compromised endpoints communicate directly back to a single, static internet-facing command server.

Modern network monitoring can identify these unique outbound connection anomalies and block them.

They all try to answer:

> "Where is this compromised machine phone-homing to?"

SpecterMesh explores a second question:

> "Can an adversary navigate an infrastructure and exfiltrate telemetry entirely through internal peer-to-peer relationships?"

Instead of forcing every node to establish direct outbound egress traffic, SpecterMesh treats the infected cluster as a cooperative network, leveraging adjacent nodes as secure data relays to bypass perimeter defenses.

## Status

Early development / research phase. The architecture will change substantially.

SpecterMesh is currently a personal research project. I am building this to learn more about how network worms propagate, how decentralized P2P routing overlays operate, and how these techniques can be analyzed for security defense.

| Phase | Goal | Status |
|---|---|---|
| 1 — Map | Parse local kernel endpoints, discover neighbors quietly, and enforce subnet constraints. | In progress |
| 2 — Propagate | Establish a concurrent worker pool to transfer and run the binary on neighbors via authorized SSH/SCP. | Planned |
| 3 — Connect | Build a lightweight, custom TCP socket layer between parents and spawned child nodes. | Planned |
| 4 — Route | Give different observers different, evolving topologies | Planned |
| 5 — Enclave | Bundle the agent into a single, highly packable Go binary for local sandboxed environments. | Planned |

Dynamic P2P multi-hop routing comes only after the local discovery and transport foundations are stable.


## ⚠️ Scope & Safety Warning

SpecterMesh is an authorized adversary emulation tool designed strictly for infrastructure security research, academic study, and detection engineering analysis.

## Explicit Boundaries

* All discovery and movement routines are programmatically limited to explicitly defined target subnets.

* No Exploitation: The tool utilizes authorized authentication frameworks, such as pre-configured SSH keys, to simulate lateral movement safely. It contains no weaponized exploits.

* Execution Environment: This software should only be executed within isolated sandbox virtual networks or environments where you possess explicit, written authorization.