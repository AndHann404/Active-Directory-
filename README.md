# Active-Directory-HomeLab
## Table of Contents
- [Overview](#overview)
- [Active Directory](#what-is-active-directory)
- [Lab Setup](#lab-setup)
- [Active Directory Setup](#active-directory-setup)

---
## Overview
This Homelab demonstrates the setup of a virtual Active Directory environment using VMware. This homelab also provides a detailed process, with screenshots, for building and configuring an AD setup, including creating organizational units, users, groups and more. Showcasing my understanding on of Active Directory, necessary for helpdesk/support roles in IT.

The goal of this project is to create a fully functional AD environment, simulating a real-world IT environment where users, groups, and policies can be managed. 

---
## What is Active Directory

Active Directory (AD) is Microsoft's directory service used to centrally manage users, computers, groups, security policies, and other network resources within a Windows domain environment. It provides administrators with a single location to authenticate users, control access to resources, enforce security policies, and simplify the management of enterprise networks.

#### Key Features:

- Centralized User Management – Create, modify, disable, and delete user accounts from one location.
- Authentication & Authorization – Verifies user identities and determines what resources they can access.
- Group Policy Management – Applies security settings and system configurations across computers and users automatically.
- Organizational Units (OUs) – Organizes users, computers, and groups into logical containers for easier administration.
- Domain Services – Allows devices within a domain to communicate securely while sharing resources.
- Security Groups – Simplifies permission management by assigning access rights to groups instead of individual users.


## Lab Setup

VMware Fusion: Installed and Configured
Windows Server 2025 Build 26404 ARM64: For setting up the Domain Controller

#### Setting up my VM

<img width="638" height="524" alt="Install Method (Screenshot)" src="https://github.com/user-attachments/assets/b3227eef-3bcc-4804-a39b-b2bc975313da" />
<img width="640" height="532" alt="Screenshot 2026-07-05 at 5 40 59 PM" src="https://github.com/user-attachments/assets/e031a37d-81dd-4203-abd8-bab573886997" />

<img width="641" height="530" alt="Screenshot 2026-07-07 at 3 20 15 PM" src="https://github.com/user-attachments/assets/67802c33-a541-4330-9d89-edd4d2251aea" />

<img width="643" height="530" alt="Screenshot 2026-07-07 at 3 21 23 PM" src="https://github.com/user-attachments/assets/b03b27bf-3328-414b-951a-a0d20a582a07" />


---

Troubleshooting:

I Had issue when booting up the VM: When it started to boot, it ended up failing due to not find an "Operating System" 

The Fix: fix I needed to select the ISO image I was using in VMware setting 

---

#### Active Directory Setup

Adding Roles and Features 

<img width="977" height="710" alt="Server Manager" src="https://github.com/user-attachments/assets/7203f9fb-8634-4e26-8568-050954ede7fb" />

<img width="1017" height="803" alt="Add roles and features wizard" src="https://github.com/user-attachments/assets/9a80a287-d45e-4990-a5c3-d5971dabe4f6" />

<img width="787" height="562" alt="Selected Services " src="https://github.com/user-attachments/assets/a82fb544-9328-4ada-8551-d6b3a3617367" />

Choosing the roles and features needed for my Active Directory Environment (i.e Active Directory Domain Services, DNS server, Group Policy Management, etc)

* Note: Not all are Necessary for AD to function, some roles/functioins are optional

---

Issue I ran into:

* When choosing the role & functions, there was an issue when I chose "DNS Server". This is due to not having set up an "Static IP" address, and if I didn't set it up any IP address change could make my AD server break.

The fix for this:

* Set up an static IP address for the role to function (I had to block it out for privacy)

<img width="787" height="591" alt="Static IP address creation" src="https://github.com/user-attachments/assets/94f9b6c4-6b20-4f1e-acae-f6264850e675" />

---

Once completed, my computer restarted and installed all of the roles and functions I chose.

<img width="786" height="558" alt="Active Directory Domain Services" src="https://github.com/user-attachments/assets/a15182ec-2df0-4ada-9143-85bec04526c4" />

<img width="974" height="699" alt="Active Directory Icons" src="https://github.com/user-attachments/assets/402d0011-64b6-4b75-8cf7-184a3000c96c" />

















