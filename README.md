# KRITIS_Cross_Domain_Resilience_Dashboard
Cross-Domain Resilience Dashboard: Cyber + Physical (NIS2 + KRITIS-DachG)
The Problem: The KRITIS-DachG (in force since March 17, 2026) is the first German law mandating physical and organizational resilience alongside cybersecurity. Operators must now report incidents to both the BSI (cyber) and the BBK (physical) within 24 hours, maintain 24/7 contact points, and conduct risk analyses covering natural disasters, sabotage, and terrorism—not just cyber threats. Most SOCs have no tooling to correlate cyber and physical security events. ​
Project Overview: Create a unified SOC analyst frontend that:
 
Correlates cyber alerts (SIEM, IDS) with physical security events (access control logs, CCTV motion detection, perimeter breach sensors, building management systems)
 
Flags incidents that trigger both BSI (cyber) and BBK (physical) reporting obligations under the dual-reporting regime
 
Visualizes facility risk posture with cyber-physical heatmaps (e.g., "Server room access breach + failed VPN login = potential insider threat")
 
Manages the 24/7 contact point roster and escalation chains required by §8 KRITIS-DachG
 
Tracks resilience plan compliance (business continuity, emergency procedures, staff training) against the 4-year risk assessment cycle
Frontend Features: Dual-pane incident view (cyber vs. physical), unified reporting decision tree (BSI only / BBK only / both), facility floor plan overlay with security event markers, contact point availability dashboard, and resilience plan task tracker with BBK audit evidence collection.
Why It Matters: This is a brand-new market gap. The KRITIS-DachG registration deadline is July 17, 2026, and initial BBK audits are planned for 2027. Companies are scrambling to integrate physical and cyber security operations. Management is now personally liable for non-compliance (up to €10M fines), so boards urgently need visibility into cross-domain resilience.
