# Telnet Service Exposure on Adorcam Indoor IP Camera

## Summary
The **Adorcam Indoor IP Camera** exposes a BusyBox telnet service on the local network.
The device listens on TCP port **23** and allows cleartext authentication attempts,
which unnecessarily increases the device’s attack surface.

This repository documents the exposed telnet service as evidence for a security
vulnerability report.

---

## Affected Product
- **Vendor:** Adorcam  
- **Product:** Adorcam Indoor Camera  
- **Amazon Listing:** https://www.amazon.com/dp/B0FHFQRSY7  
- **Firmware:** 1.00.11 (Factory firmware)  
- **Category:** Consumer IP Camera / IoT Device  

---

## Technical Details
- **Open Port:** TCP 23  
- **Service:** BusyBox `telnetd`  
- **Protocol:** Telnet (cleartext)  
- **Operating System:** Embedded Linux (kernel 2.6.x–3.x range observed via fingerprinting)  
- **Authentication:** Required, transmitted in cleartext  
- **User Mitigation:** No documented method to disable the telnet service  

The telnet service is unnecessary for normal consumer operation and is not documented
in user-facing product materials.

---

## Proof of Exposure
A network service scan confirms that the device exposes a telnet service on the local network.

To reproduce:
```bash
nmap -sV -p 23 <device_ip>
