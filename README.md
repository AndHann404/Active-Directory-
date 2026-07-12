# Active-Directory-HomeLab
## Table of Contents
- [Overview](#overview)
- [Active Directory](#what-is-active-directory)
- [Lab Setup](#lab-setup)
- [Active Directory Setup](#active-directory-setup)
- [Organizational Units](#creating-organizational-units)
- [Created Users](#creating-users)
- [Group Policies](#creating-group-policies)

---
## Overview
This Homelab demonstrates the setup of a virtual Active Directory environment using VMware. This homelab also provides a detailed process, with screenshots, for building and configuring an AD setup, including creating organizational units, users, groups and more. Showcasing my understanding on of Active Directory, necessary for helpdesk/support roles in IT.

The goal of this project is to create a fully functional AD environment, simulating a real-world IT environment where users, groups, and policies can be managed. 

---
## Project Synopsis

This Active Directory homelab simulates a regional healthcare network consisting of three hospitals: Manhattan General Hospital, Brooklyn Medical Center, and Queens Children's Hospital. Each hospital contains its own Organizational Units for departments, users, computers, and servers to replicate a real-world enterprise Active Directory environment. The project is designed to practice common IT support and system administration tasks, including user management, Group Policy administration, domain management, and access control.

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

---
#### Creating Organizational Units

Organizational Units (OUs) are container objects in Active Directory that allow you to organize different resources, including users, computers, and groups. This makes it easier to manage resources by allowing administrators to apply Group Policy Objects (GPOs) to specific sets of users or devices.

<img width="715" height="528" alt="Creating OUs" src="https://github.com/user-attachments/assets/c1b1f525-8190-42a1-b087-131d1ebf2af7" />

*Note: In this screenshot, I checked the box "protect container from accidental deletion" to give each container an added layer of protection.

---
#### Creating Groups

Groups in Active Directory is a collection of users or computer accounts managed as a single object. 

They are catorgized by two types:

* Security Groups: Used to assign permissions to shared resources (e.g., printers, files, folders).
* Distribution Groups: Used exclusively for email distribution lists in Microsoft Exchange.

<img width="749" height="527" alt="Group creation 1" src="https://github.com/user-attachments/assets/391b3d39-8874-4d74-8583-058810cba76c" />

<img width="741" height="525" alt="Group Creation 2" src="https://github.com/user-attachments/assets/b95633d5-9684-40a4-a81b-90a32d4ee7eb" />


---
#### Creating Users

<img width="435" height="381" alt="Creating Users" src="https://github.com/user-attachments/assets/68519b42-73fa-4f6e-a46d-fde5be54d8c6" />


<img width="446" height="386" alt="Creating User (PW)" src="https://github.com/user-attachments/assets/07068ef2-6da7-4bf1-ac06-0450e1b4ae7a" />


<img width="748" height="526" alt="created users list" src="https://github.com/user-attachments/assets/fda2bfbb-ae8e-4ccf-bf4c-8e0f45fcd70e" />

---

#### Creating Group Policies

Group Policies are a centralized management feature in Active Directory that allows IT administrators to define, manage, and enforce security settings, desktop configurations, and software policies across users and computers within a domain. 

This allows administrators to apply policies from a central location, ensuring consistency, improving security and reducing time to manage large environements.

## There are two types fo Group Policy Configurations, Computer configutation and User configuration: 

* Computer Configuration: A set of rules that apply ONLY to the computer, regardless of the user who logs in.

* User Configuraton: A set of rules that applies to the user, meaning that any time they log in; the system will push those set rules.



## There is also two types of Group Policy Settings, Policies and Preferences:

* Policies: Settings that are enforced by Active Directroy and cannot be changed by the user (ex: Password policies).

* Preferences: Settings that can be set by default but can be changed by users (Ex: Mapped Network Drives).


<img width="750" height="522" alt="Creating GPO" src="https://github.com/user-attachments/assets/bf0d048e-4aec-48b6-8703-f9ab2e70de93" />

* In this screenshot I am creating a Password Policy


<img width="773" height="558" alt="Editing GPO" src="https://github.com/user-attachments/assets/2972c086-2bd2-4828-b14c-5dd9ccd5f377" />

Since this is gonna be a Password Policy, this rule had to be unchangable by the user (Policy) and had to be applied for the computer (computer configuration).

* This screenshot showcases the details of my password policies.

---

### Connecting To the Domain



