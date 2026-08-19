# Connectivity Tests

These tests were performed to verify routing, firewall policies, ACLs, and NAT in the lab.

## 1. Internal → DMZ Web Server

**Test:** HR PC → DMZ Web Server  
**Destination:** `192.168.50.10`  
**Protocol:** HTTP  
**Expected:** Allowed  
**Result:** PASS

The HR network was able to access the web server hosted in the DMZ.

---

## 2. Outside → DMZ Web Server

**Test:** Outside PC → ASA Outside IP  
**Destination:** `192.168.100.2`  
**Protocol:** HTTP  
**Expected:** Allowed through static NAT  
**Result:** PASS

The outside PC successfully accessed the DMZ web server through the ASA's outside address.

---

## 3. Outside → Internal Network

**Test:** Outside PC → Internal networks  
**Destination:** `192.168.10.0/24`, `192.168.20.0/24`, `192.168.30.0/24`  
**Expected:** Blocked  
**Result:** PASS

The ASA ACL prevented direct access from the outside network to the internal departments.

---

## 4. DMZ → Internal Network

**Test:** DMZ Web Server → Internal networks  
**Expected:** Restricted  
**Result:** PASS

Traffic from the DMZ toward the internal networks was restricted according to the firewall policy.

---

## 5. NAT Verification

Static NAT was verified on the ASA using:

```text
show nat
show xlate
