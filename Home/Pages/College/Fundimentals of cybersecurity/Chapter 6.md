[[Fundimentals of cybersecurity]]
Here’s a **clean, concise Obsidian-ready summary** of **Lecture 6: Operating System Security**, structured for notes, linking, and review.

---

# Lecture 6 – Operating System Security

**Professor:** Hossein Saiedian

---

## OS Security Layers

* Operating systems are built in **layers**
* Each layer depends on the security of the layers below it
* If lower layers (e.g., BIOS, hardware) are compromised, higher layers cannot be trusted

**BIOS (Basic Input/Output System)**

* Initializes hardware and boots the OS
* Vulnerable if not secured early

---

## System Security Planning

**Goal:** Maximize security while minimizing cost

### Why Planning Matters

* Systems can be compromised **during installation**
* Security must be designed **before deployment**

### Planning Objectives

* Assess risks and define security requirements
* Secure OS first, then applications and data
* Ensure proper network protection
* Define ongoing security processes

### Planning Considerations

* Purpose of the system and stored data
* Applications and services provided
* User categories and privilege levels
* Authentication methods
* Administrative access (local vs remote)
* Access to external systems (file/database servers)
* Additional controls (firewalls, antivirus, logging)

---

## Operating System Hardening

**First critical step** in securing a system

### Core Hardening Steps

* Install and patch the OS
* Configure OS to meet security requirements
* Install security tools:

  * Anti-virus
  * Host-based firewall
  * IDS/IPS
* Perform security testing

### Key Statistics

* Over **70% of cyber intrusions** could have been prevented by:

  * Application whitelisting
  * OS & third-party patching
  * Restricting admin privileges
  * Defense-in-depth

---

## Removing Unnecessary Services

* Fewer running services = smaller attack surface
* Default installations prioritize usability, not security
* Only install what is required
* Add packages later **only when needed**

---

## Users, Privileges, and Resource Controls

### User & Privilege Configuration

* Not all users need the same access
* Elevated privileges:

  * Granted only when required
  * Used only for specific tasks
* Default accounts:

  * Remove or disable if unused
  * Secure authentication policies

### Resource Controls

* Set permissions on files and directories
* Follow hardening guides for secure defaults
* Enhance with:

  * Anti-virus
  * Firewalls
  * IDS/IPS
  * Application whitelisting

---

## System Security Testing

* Final step in OS hardening
* Ensures configurations are correct
* Uses:

  * Security checklists
  * Vulnerability scanners
  * Configuration auditing tools

---

## Application Security

### Application Configuration

* Secure default settings
* Remove default data, scripts, and accounts
* Restrict write permissions (especially for web/file services)

### Encryption Technology

* Protects data **in transit and at rest**
* Includes:

  * Encrypted file systems
  * TLS/IPsec for network services
  * SSH keys for secure access
* Requires proper key creation and management

---

## Security Maintenance

Security is **continuous**

### Includes

* Log monitoring and analysis
* Regular backups
* Incident recovery
* Periodic security testing
* Patch management and configuration reviews

---

## Data Backup & Archiving

* Essential for integrity and recovery
* Defined during system planning

### Backup Decisions

* Online vs offline
* Local vs remote storage
* Trade-offs:

  * Cost vs security
  * Ease vs robustness

---

## Linux / Unix Security

### Patch & Configuration Management

* Keep OS and applications patched
* Configuration files:

  * System-wide: `/etc`
  * User-specific: hidden “dot” files
* Disable unnecessary services

### Users, Groups, and Permissions

* Permissions: read, write, execute
* Applied to owner, group, others
* Protect critical files and directories

### Exploits

* **Local exploit:** gain elevated privileges locally
* **Remote exploit:** attack via network services

### Chroot Jail

* Restricts process view of filesystem
* Improves isolation
* Adds complexity

---

## Windows Security

### Patch Management

* Windows Update / WSUS
* Third-party auto-update tools

### Access Control

* Discretionary Access Control (DAC)
* Mandatory Integrity Control (Vista+)

  * Integrity levels: low, medium, high, system
  * Based on Biba Integrity Model

### Registry

* Centralized configuration database
* Modified via Registry Editor
* Useful for bulk changes

### Security Tools

* Anti-virus, anti-spyware, firewall
* Built-in Windows protections
* Cryptography support:

  * EFS (file encryption)
  * BitLocker (full disk encryption)
* Microsoft Baseline Security Analyzer (MBSA)

---

## Virtualization

### Overview

* Abstraction of hardware into virtual machines
* Improves efficiency
* Supports multiple OSs on one system
* Introduces new security risks

### Virtualization Alternatives

* Application virtualization (e.g., JVM)
* Full virtualization (multiple guest OSs)
* Hypervisor / VMM manages hardware access

### Full Virtualization Types

* **Native (bare-metal)**

  * Hypervisor runs directly on hardware
  * Fewer layers → more secure
* **Hosted**

  * Runs on top of a host OS
  * More layers → increased risk

---

## Virtualization Security Issues

* Guest OS isolation
* Hypervisor trustworthiness
* VM image and snapshot security

### Hypervisor Security Best Practices

* Harden like an OS
* Isolate environment
* Auto-update and monitor
* Restrict admin access
* Secure remote administration
* Integrate with firewalls and IDS

---

## Summary

* System security planning
* OS hardening and testing
* Application security and encryption
* Continuous maintenance and backups
* Linux/Unix and Windows security practices
* Virtualization risks and controls

---

## Tags

```
#operating-systems #os-security #cybersecurity #system-hardening
#linux-security #windows-security #patch-management
#access-control #encryption #virtualization
#backup #logging #ids #firewalls
```

If you want, I can also:

* Break this into **linked atomic notes** (Zettelkasten style)
* Add **exam-focused highlights**
* Convert it into a **one-page cheat sheet**