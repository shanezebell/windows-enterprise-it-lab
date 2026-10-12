# Active Directory and virtual network foundation

[Back to portfolio](../../README.md)

## Objective

Establish a Windows Server domain and join a Windows 11 workstation in a UTM lab.

**Technologies:** UTM, Windows Server 2025, Windows 11, AD DS, DNS, PowerShell

## Implementation and results

The sequence begins with server setup and initial connectivity tests, then moves to an isolated UTM network and the `10.10.10.0/24` lab subnet. DC01 is shown at `10.10.10.10`; PC01 initially uses `10.10.10.20`. Domain discovery identifies `lab.test`, and the workstation displays a successful domain-join confirmation. A later ADUC view shows the PC01 computer object.

**Troubleshooting:** An initial ping fails, an inbound ICMP rule is added, and a subsequent ping succeeds. DNS lookups later show timeouts even while an explicit SRV query returns DC01. The final domain-controller discovery succeeds; the screenshots do not establish that every DNS timeout was resolved.

**Evidence limits:** UTM screenshots show Host Only / Network 0, whereas the earlier write-up calls the network bridged. This portfolio follows the screenshots for that stage. VM architecture, memory allocation, reverse lookup zones, and the later Endpoints OU placement need separate verification.

## Result at a glance

![Active Directory and virtual network foundation result](screenshots/20-pc01-domain-join-confirmation.png)

## Evidence walkthrough

Screenshots are numbered chronologically within this module. Capture times come from original filenames; guest operating-system clocks may differ. Error screens are retained to show the troubleshooting sequence.

| Step | Evidence | Capture time |
| --- | --- | --- |
| 01 | [Windows server installation ready](screenshots/01-windows-server-installation-ready.png) | 2026-09-13 at 10.56.10 |
| 02 | [Dc01 server manager baseline](screenshots/02-dc01-server-manager-baseline.png) | 2026-09-13 at 11.15.28 |
| 03 | [Dc01 initial ip configuration](screenshots/03-dc01-initial-ip-configuration.png) | 2026-09-13 at 11.16.14 |
| 04 | [Pc01 initial ping timeout](screenshots/04-pc01-initial-ping-timeout.png) | 2026-09-13 at 11.38.32 |
| 05 | [Dc01 allow client icmp](screenshots/05-dc01-allow-client-icmp.png) | 2026-09-13 at 11.39.26 |
| 06 | [Pc01 ping succeeds after firewall rule](screenshots/06-pc01-ping-succeeds-after-firewall-rule.png) | 2026-09-13 at 11.39.47 |
| 07 | [Install active directory domain services](screenshots/07-install-active-directory-domain-services.png) | 2026-09-13 at 11.40.58 |
| 08 | [Inspect host virtual network](screenshots/08-inspect-host-virtual-network.png) | 2026-09-13 at 11.42.31 |
| 09 | [Utm default host only network](screenshots/09-utm-default-host-only-network.png) | 2026-09-13 at 11.44.29 |
| 10 | [Dc01 select isolated network](screenshots/10-dc01-select-isolated-network.png) | 2026-09-13 at 11.44.56 |
| 11 | [Pc01 select isolated network](screenshots/11-pc01-select-isolated-network.png) | 2026-09-13 at 11.45.10 |
| 12 | [Dc01 static ip configuration](screenshots/12-dc01-static-ip-configuration.png) | 2026-09-13 at 11.48.47 |
| 13 | [Update icmp rule for lab subnet](screenshots/13-update-icmp-rule-for-lab-subnet.png) | 2026-09-13 at 11.51.35 |
| 14 | [Pc01 ping domain controller](screenshots/14-pc01-ping-domain-controller.png) | 2026-09-13 at 11.52.00 |
| 15 | [Verify lab test domain](screenshots/15-verify-lab-test-domain.png) | 2026-09-13 at 12.03.46 |
| 16 | [Query domain srv record and set dns](screenshots/16-query-domain-srv-record-and-set-dns.png) | 2026-09-13 at 12.12.55 |
| 17 | [Dns lookup timeout during troubleshooting](screenshots/17-dns-lookup-timeout-during-troubleshooting.png) | 2026-09-13 at 12.13.23 |
| 18 | [Inspect client dns server addresses](screenshots/18-inspect-client-dns-server-addresses.png) | 2026-09-13 at 12.13.38 |
| 19 | [Domain controller discovery succeeds](screenshots/19-domain-controller-discovery-succeeds.png) | 2026-09-13 at 12.24.22 |
| 20 | [Pc01 domain join confirmation](screenshots/20-pc01-domain-join-confirmation.png) | 2026-09-13 at 18.44.29 |
| 21 | [Pc01 computer object in active directory](screenshots/21-pc01-computer-object-in-active-directory.png) | 2026-10-11 at 14.35.51 |

<details>
<summary>Open the full screenshot walkthrough</summary>

### 01 Windows server installation ready

![Windows server installation ready](screenshots/01-windows-server-installation-ready.png)

### 02 Dc01 server manager baseline

![Dc01 server manager baseline](screenshots/02-dc01-server-manager-baseline.png)

### 03 Dc01 initial ip configuration

![Dc01 initial ip configuration](screenshots/03-dc01-initial-ip-configuration.png)

### 04 Pc01 initial ping timeout

![Pc01 initial ping timeout](screenshots/04-pc01-initial-ping-timeout.png)

### 05 Dc01 allow client icmp

![Dc01 allow client icmp](screenshots/05-dc01-allow-client-icmp.png)

### 06 Pc01 ping succeeds after firewall rule

![Pc01 ping succeeds after firewall rule](screenshots/06-pc01-ping-succeeds-after-firewall-rule.png)

### 07 Install active directory domain services

![Install active directory domain services](screenshots/07-install-active-directory-domain-services.png)

### 08 Inspect host virtual network

![Inspect host virtual network](screenshots/08-inspect-host-virtual-network.png)

### 09 Utm default host only network

![Utm default host only network](screenshots/09-utm-default-host-only-network.png)

### 10 Dc01 select isolated network

![Dc01 select isolated network](screenshots/10-dc01-select-isolated-network.png)

### 11 Pc01 select isolated network

![Pc01 select isolated network](screenshots/11-pc01-select-isolated-network.png)

### 12 Dc01 static ip configuration

![Dc01 static ip configuration](screenshots/12-dc01-static-ip-configuration.png)

### 13 Update icmp rule for lab subnet

![Update icmp rule for lab subnet](screenshots/13-update-icmp-rule-for-lab-subnet.png)

### 14 Pc01 ping domain controller

![Pc01 ping domain controller](screenshots/14-pc01-ping-domain-controller.png)

### 15 Verify lab test domain

![Verify lab test domain](screenshots/15-verify-lab-test-domain.png)

### 16 Query domain srv record and set dns

![Query domain srv record and set dns](screenshots/16-query-domain-srv-record-and-set-dns.png)

### 17 Dns lookup timeout during troubleshooting

![Dns lookup timeout during troubleshooting](screenshots/17-dns-lookup-timeout-during-troubleshooting.png)

### 18 Inspect client dns server addresses

![Inspect client dns server addresses](screenshots/18-inspect-client-dns-server-addresses.png)

### 19 Domain controller discovery succeeds

![Domain controller discovery succeeds](screenshots/19-domain-controller-discovery-succeeds.png)

### 20 Pc01 domain join confirmation

![Pc01 domain join confirmation](screenshots/20-pc01-domain-join-confirmation.png)

### 21 Pc01 computer object in active directory

![Pc01 computer object in active directory](screenshots/21-pc01-computer-object-in-active-directory.png)

</details>
