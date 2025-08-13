<h1>Secure Enterprise Network Design in Cisco Packet Tracer</h1>

<h2>Description</h2>
<p>This repository contains the Cisco Packet Tracer (`.pkt`) file that demonstrates a secure, scalable, and structured network built for a medium-sized enterprise. The project objective was to design a network for a 240-staff business, segmented into five departments across two floors, including a guest wireless network and capacity for 20% future growth. </p>

<h2>Network Topology Diagram</h2>
<p><b>The network follows a hierarchical design with a core router, two distribution-layer (L3) switches, and multiple access-layer (L2) switches to ensure scalability and efficient traffic management. Redundancy is built-in using the Spanning Tree Protocol (STP).</b></p> 

<h2>Key Design & Security Features</h2>
<ul>
<li><b>Structured Subnetting:</b>Utilizes Fixed-Length Subnet Masking (FLSM) with a `/23` subnet mask (`255.255.254.0`) to provide ample address space (510 usable IPs per subnet) for each department and for future expansion.</li>
<li><b>VLAN Segmentation:</b>The network is logically segmented into 7 VLANs to isolate broadcast domains, enhance security, and improve traffic management. Each department, plus the BYOD network and a future expansion space, resides on its own VLAN.</li>
<li><b>Layer 3 Switching:</b>Two multilayer switches are configured for high-performance inter-VLAN routing, offloading this task from the core router</li>
<li><b>ASA Firewall:</b>A Cisco ASA 5505 Firewall is deployed at the edge of the network to inspect traffic and enforce security policies between the trusted internal network (security-level 100) and the untrusted outside network (security-level 0).</li>
<li><b>Port Security:</b>Critical infrastructure, like the Finance server, is protected with port security measures that restrict access to a specific MAC address (`mac-address sticky`) and log any violation attempts (`violation restrict`).</li>
<li><b>Wireless Security:</b>The "Bring Your Own Device" (BYOD) wireless network is secured using **WPA2 with AES encryption**, configured via a Wireless LAN Controller (WLC).</li>
<li><b>Device Hardening:</b>All network devices (routers, switches) are hardened with encrypted `enable secret` passwords and `console line` passwords. All unused switch ports are administratively shut down to prevent unauthorized access.</li>
<li><b>Redundancy:</b>Spanning Tree Protocol (STP) is active to prevent switching loops and provide automatic path redundancy between daisy-chained switches. `PortFast` is enabled on access ports for faster convergence</li>
</ul>


<h2>IP Addressing & VLAN Scheme</h2>
<p>The assigned Class B network address is `138.141.0.0/16`. This was subnetted to create distinct networks for each department.</p>

<table>
  <thead>
    <tr>
      <th>Department / Use Case</th>
      <th>VLAN ID</th>
      <th>Network Address</th>
      <th>Usable IP Range</th>
      <th>Default Gateway</th>
      <th>Subnet Mask</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>Human Resources</strong></td>
      <td>10</td>
      <td><code>138.141.0.0/23</code></td>
      <td><code>138.141.0.1 - 138.141.1.254</code></td>
      <td><code>138.141.0.1</code></td>
      <td><code>255.255.254.0</code></td>
    </tr>
    <tr>
      <td><strong>Sales &amp; Marketing</strong></td>
      <td>20</td>
      <td><code>138.141.2.0/23</code></td>
      <td><code>138.141.2.1 - 138.141.3.254</code></td>
      <td><code>138.141.2.1</code></td>
      <td><code>255.255.254.0</code></td>
    </tr>
    <tr>
      <td><strong>Finance</strong></td>
      <td>30</td>
      <td><code>138.141.4.0/23</code></td>
      <td><code>138.141.4.1 - 138.141.5.254</code></td>
      <td><code>138.141.4.1</code></td>
      <td><code>255.255.254.0</code></td>
    </tr>
    <tr>
      <td><strong>IT Consulting</strong></td>
      <td>40</td>
      <td><code>138.141.6.0/23</code></td>
      <td><code>138.141.6.1 - 138.141.7.254</code></td>
      <td><code>138.141.6.1</code></td>
      <td><code>255.255.254.0</code></td>
    </tr>
    <tr>
      <td><strong>R&amp;D</strong></td>
      <td>50</td>
      <td><code>138.141.8.0/23</code></td>
      <td><code>138.141.8.1 - 138.141.9.254</code></td>
      <td><code>138.141.8.1</code></td>
      <td><code>255.255.254.0</code></td>
    </tr>
    <tr>
      <td><strong>BYOD Wireless</strong></td>
      <td>80</td>
      <td><code>138.141.10.0/23</code></td>
      <td><code>138.141.10.1 - 138.141.11.254</code></td>
      <td><code>138.141.10.1</code></td>
      <td><code>255.255.254.0</code></td>
    </tr>
    <tr>
      <td><strong>Future Expansion</strong></td>
      <td>99</td>
      <td><code>138.141.12.0/23</code></td>
      <td><code>138.141.12.1 - 138.141.13.254</code></td>
      <td><code>138.141.12.1</code></td>
      <td><code>255.255.254.0</code></td>
    </tr>
    <tr>
      <td><strong>Remote Management</strong></td>
      <td>1</td>
      <td><code>138.141.100.0/24</code></td>
      <td><code>138.141.100.1 - 100.3</code></td>
      <td>N/A</td>
      <td><code>255.255.255.0</code></td>
    </tr>
  </tbody>
</table>



<p align="center">
This is a Logical layout of this enterprise network: <br/>
<img src="https://i.imgur.com/xJm2qcj.png" height="80%" width="80%" alt="Assembly_Program_Runtime"/>
<br />
<br />
This is a screenshot of the CLI of a Multilayer Switch after it was configured: <br/>
<img src="https://i.imgur.com/QUoIPhz.png" height="80%" width="80%" alt="Assembly_Program_Runtime"/>
<br />
<br />
</p>
