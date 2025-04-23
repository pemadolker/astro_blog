---
title: Enumeration Methodology notes
publishDate: "2025-04-23T13:00:00Z"
updateDate: "2025-04-23T14:32:00Z"
---

# Enumeration Methodology

When we're dealing with complex processes, it’s really important to follow a proper methodology. Without one, it’s super easy to get lost or miss out on something important during our testing. Target systems can vary a lot, so there’s never a one-size-fits-all approach. That’s why most penetration testers tend to follow their own habits or routines they’ve developed over time. But those routines aren’t necessarily standardized—they’re just based on personal experience.

Since both penetration testing and enumeration are very dynamic, we still need some sort of structured plan to guide us. That’s where a static enumeration methodology helps. It gives us a layered system for both external and internal penetration tests while still being flexible enough to adapt to different environments. 

## Three Main Levels of Enumeration

1. **Infrastructure-based Enumeration**
2. **Host-based Enumeration**
3. **OS-based Enumeration**

Imagine these levels like walls or barriers. We’re basically looking for holes, gaps, or weak spots in each wall to try and move deeper inside the target. Sometimes we might even force our way through, but that might not always work out because there could be nothing useful on the other side. So instead of wasting time and energy, we focus on where the real entry points are.

## The 6 Enumeration Layers

Below is a breakdown of the six layers we usually follow during enumeration. Think of each layer as a stage that brings us closer to the core of the system:

| **Layer** | **Description** | **Information Categories** |
|----------|-----------------|-----------------------------|
| **1. Internet Presence** | Identifying external infrastructure that's publicly visible. | Domains, Subdomains, vHosts, ASN, Netblocks, IPs, Cloud Instances, Security Measures |
| **2. Gateway** | Understanding external/internal protection measures. | Firewalls, DMZ, IDS/IPS, EDR, Proxies, VPN, NAC, Network Segmentation |
| **3. Accessible Services** | Identifying and analyzing reachable services/interfaces. | Service Types, Functionality, Ports, Versions, Configurations |
| **4. Processes** | Digging into internal processing flows of these services. | PIDs, Data Processing Tasks, Source & Destination |
| **5. Privileges** | Looking into user roles and permissions. | Users, Groups, Permissions, Environment Restrictions |
| **6. OS Setup** | Getting insights into the OS configuration and environment. | OS Type, Patch Levels, Config Files, Sensitive Data |

> ⚠️ Note: The first two layers (Internet Presence and Gateway) aren’t always applicable in internal environments like Active Directory. Internal enumeration is usually handled differently.

## How to Think About Enumeration

Let’s picture a penetration test like going through a big maze. Every wall has a few gaps or cracks, and our job is to find the right one that leads us further in. But not every gap will be useful. Just because we spent hours trying to break in at one point doesn’t mean it’s the right way. So we need to use our time wisely and keep in mind: there is *almost always* a way in—we just have to find it.

For example, even a four-week pen test might not uncover every single vulnerability. An attacker who watches a company for months could easily discover things we might miss. The SolarWinds attack is a great example of this—slow, careful observation led to a massive breach.

> A quick note: For simplicity, OSINT data from employees has been left out of Layer 1 (Internet Presence), but in real life, it can be super useful.

## Practical Example: External Black Box Test

Let’s say we’ve been hired to do an external black box penetration test. Once the contract is signed and we’re good to go, we’ll begin with:

### Layer 1: Internet Presence

We look for everything related to the company’s presence on the internet. That means domains, subdomains, netblocks, IPs, etc. If the contract lets us scan for more targets outside of what’s been given, this becomes even more critical.

**Goal:** Find all potential targets and interfaces.

---

### Layer 2: Gateway

Now we try to figure out what security measures are in place for the reachable targets. This can include firewalls, VPNs, proxies, and so on. It’s all about learning how the target is protected and where it sits in the network.

**Goal:** Understand the protections and limitations.

---

### Layer 3: Accessible Services

At this point, we start identifying all the services the target hosts. Each service has a reason it’s running—maybe it’s a mail server, maybe a web app. We need to understand these services, how they work, and how we can interact with them.

**Goal:** Learn how the services work and how to use them to our advantage.

> This is the part of enumeration we focus on the most in this module.

---

### Layer 4: Processes

Whenever a service runs, it triggers processes—these handle data and tasks. Each process has a source (where data comes from) and a destination (where it’s going).

**Goal:** Understand the relationships and flow of data.

---

### Layer 5: Privileges

Every service is run by a user with specific privileges. Often, misconfigured privileges can give us unexpected access. This happens a lot in Active Directory or when sysadmins don’t segment roles properly.

**Goal:** Identify what users and groups can do.

---

### Layer 6: OS Setup

Finally, we look at the actual OS setup. This is where we can find configuration files, patch info, and even sensitive data. It shows us how the admins are managing their systems and what their security posture is like.

**Goal:** Assess internal system security and misconfigurations.

---

##  Concluding: What Is a Methodology?

A methodology is basically a structured approach to gather information for a certain goal. It's not a step-by-step guide, but more of a collection of logical steps we adapt depending on the situation. 

In our case, enumeration methodology helps us consistently explore a system from the outside in. Tools and commands will always change based on context, but the overall strategy—this layered approach—stays the same.

> Tools are useful, but they're not the methodology. They're just part of our toolkit or a cheat sheet we can use when needed.

---

