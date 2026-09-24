# Privacy Policy for AiroSpeedMonitor

**Last Updated / Effective Date:** September 24, 2026  
**Application Name:** AiroSpeedMonitor  
**Developer / Publisher:** Asep Sayyad  
**Contact Email:** feedback@asepsayyad007.in  
**Website & Support:** https://asepsayyad007.in  
**Public Releases:** https://github.com/asepsayyad007/AiroSpeedMonitor-Release  

---

## 1. Overview and Core Privacy Principle

AiroSpeedMonitor is an open-source, local-first network bandwidth monitoring and system telemetry utility for Windows 10 and Windows 11.

**Our Core Privacy Principle:**  
AiroSpeedMonitor does **not** collect, store, profile, sell, or transmit your personal data, browsing history, packet contents, device serial numbers, or online identity. All network bandwidth calculations and hardware performance counters run strictly on your local computer.

---

## 2. Information Accessed on Your Device

To provide real-time network speed metrics and hardware widgets, AiroSpeedMonitor accesses the following system information locally:

1. **Network Adapter Throughput**: Measures the total number of bytes sent and received via your active network interfaces (Wi-Fi, Ethernet) using standard Windows `System.Net.NetworkInformation` APIs.
2. **Process Network Connections**: Reads active TCP/UDP connection endpoints and socket counts via standard, non-elevated Windows IP Helper APIs (`GetExtendedTcpTable`, `GetExtendedUdpTable`) to display per-process bandwidth consumption. Process network traffic analysis is performed entirely in memory (RAM).
3. **Hardware Telemetry**: Reads overall CPU utilization, memory (RAM) usage, and GPU utilization via standard Windows Performance Data Helper (PDH) and Win32 `GlobalMemoryStatusEx` APIs.
4. **Network Interface Details**: Reads adapter name, MAC address, gateway IP, and subnet mask locally to display connection status.
5. **Local Network Devices (LAN Scanner)**: When you explicitly run the LAN Scanner tool, link-layer ARP queries (`SendARP`) and local reverse DNS requests are performed on your local subnet (`192.168.x.x` or `10.x.x.x`) to list connected local devices. This scan data never leaves your local network.

---

## 3. Local Data Storage

AiroSpeedMonitor stores minimal configuration and traffic statistics exclusively on your local hard drive:

- **Local Database (`traffic.db`)**: Located at `%AppData%\AiroSpeedMonitor\traffic.db`. Contains aggregated daily/monthly upload and download byte totals (used for data quota alerts and history graphs) and past Speed Test benchmark scores.
- **Application Settings (`settings.json`)**: Located at `%AppData%\AiroSpeedMonitor\settings.json`. Stores your UI preferences (themes, widget position, auto-hide options, alert thresholds).
- **User Control & Deletion**: You can reset or delete this data at any time directly within the application via **Settings > Reset All Settings** or by deleting the `%AppData%\AiroSpeedMonitor` folder. Uninstalling the application removes all application files.

---

## 4. Network Communications & External Endpoints

AiroSpeedMonitor operates fully offline for its core monitoring features. The application initiates external network connections **only** when you explicitly launch specific diagnostic features:

### A. Network Speed Benchmark (User-Initiated)
When you click **Run Speed Test**, the application measures network latency, download speed, and upload speed by communicating with public Anycast Content Delivery Networks:
- **Endpoints**:
  - `speed.cloudflare.com` (Cloudflare Anycast CDN)
  - `ash-speed.hetzner.com` (Hetzner Speedtest Mirror)
  - `proof.ovh.net` (OVH Speedtest Mirror)
- **Data Transmitted**: Random synthetic byte streams generated dynamically in memory. No user files, identifiable headers, or personal information are included in the test payload.

### B. Public IP Lookup (User-Initiated)
When you open the **Network Info** or **Network Tools** view, the application can determine your external WAN IP address by querying:
- `speed.cloudflare.com/cdn-cgi/trace`
- `api.ipify.org` (fallback)
The returned public IP address is displayed on your screen and is never transmitted to the publisher or any third party.

---

## 5. Third-Party Analytics, Advertising, and Tracking

- **Analytics SDKs**: None.
- **Crash Reporting Services**: None.
- **Advertising Networks**: None.
- **Tracking Cookies / Beacons**: None.
- **Data Sales or Brokering**: We do not sell, rent, monetize, or share any user data.

---

## 6. External Links

The application contains user-facing links to external websites (such as GitHub project pages, documentation, and a voluntary Buy Me a Coffee donation link). Clicking these links opens your default web browser, which is governed by the respective privacy policies of those external sites.

---

## 7. Children's Privacy

AiroSpeedMonitor does not collect any personal information from any user, including children under the age of 13.

---

## 8. Compliance and Contact Information

If you have questions regarding this Privacy Policy or the application's data practices, please contact:

- **Developer / Publisher**: Asep Sayyad
- **Support & Privacy Email**: feedback@asepsayyad007.in
- **Feedback Form**: https://forms.gle/8qRg4bGxPKurk7N6A
- **Public Issues**: https://github.com/asepsayyad007/AiroSpeedMonitor-Release/issues
