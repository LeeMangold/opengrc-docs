# GRC Foundations

## Typical Workflows
There are a lot of ways and means to implement a Governance, Risk, and Compliance program. The following workflows form the basis of most SMB GRC programs and is how OpenGRC is designed to work:

### Compliance Workflow
1. Create a new Standard that you want to adhere to.
2. Add Controls (requirements) that, when followed, meet the requirements of the Standard.
3. Create Implementations that satisfy the requirements of the Controls.
4. Perform Audits to ensure that the Implementations put in place to meet the control requirements are being followed and are effective.

### Risk Workflow
OpenGRC allows you to manage, rank, and track cybersecurity risks in your environment. This is a very simple Risk Management implementation and is likely sufficient for most small organizations. The following is a typical Risk Management workflow in OpenGRC:
1. Create a new Risk.
2. Rate the Risk based on its likelihood and impact, assuming you do NOTHING. This is your Inherent Risk.
3. Create and relate Implementations to the Risk item that reduce the likelihood or impact of the Risk.
4. Rate the Risk again, assuming you implement the Mitigations. This is your Residual Risk.

The heatmaps will show you how successful you are at managing your risks. The goal is to reduce the Residual Risk to an acceptable level (determined by you and your organizations risk appetite). This can get you started with a basic risk management program, but please note that this description is not a full tutorial on Risk Management.


## Foundational Data Objects

## Programs
Programs are the highest level of organization in OpenGRC. Programs are used to group together related Standards, Controls, Implementations, and Audits. In OpenGRC, a program is **optional** and simply a container for multiple standards. A good example for a usecase is, for example, CMMC. CMMC is a combination of the 800-171, 800-172, as well as various laws from the FAR and DFARS. Grouping them all together under one Program allows you to easily manage, audit, and report them all together.

As a reminder, using the program feature is optional. You can still create and manage Standards, Controls, Implementations, and Audits without using a Program.

## Standards
Security standards are a set of guidelines and best practices designed to safeguard systems, networks, and data from various cyber threats. They establish a baseline for implementing and measuring effective security controls within organizations. These standards cover a broad range of areas including network security, data encryption, access control, and vulnerability management. By adhering to these standards, organizations can protect themselves against unauthorized access, data breaches, and other cyber threats, thereby ensuring the confidentiality, integrity, and availability of their information assets. Common examples of security standards include ISO/IEC 27001, which provides a framework for information security management systems, and the Payment Card Industry Data Security Standard (PCI DSS), which outlines security measures for organizations handling credit card transactions.

## Controls
A security control is a safeguard or countermeasure designed to protect the confidentiality, integrity, and availability of information systems and data. These controls can be physical, technical, or administrative in nature. Physical controls include measures like locks and surveillance cameras to secure physical assets. Technical controls, often software or hardware-based, include firewalls, encryption, and antivirus programs, aimed at protecting digital assets from cyber threats. Administrative controls consist of policies, procedures, and training that govern user behavior and operational procedures. Together, these controls form a comprehensive defense against a wide range of security threats, from unauthorized access and data breaches to internal policy violations. In a world where digital threats are constantly evolving, the implementation and continuous refinement of these security controls are crucial for maintaining the overall security posture of an organization.

### Control Types (What the Control is...)
* **Administrative:** Controls managed by people or organizational processes (e.g., policies, training, incident response plans).
* **Operational:** Controls that are implemented and enforced by day-to-day processes (e.g., backups, physical security).
* **Technical:** Controls implemented through technology (e.g., firewalls, encryption, access control systems).

### Control Categories (What the Control does...)
* **Preventative:** Controls designed to prevent security incidents (e.g., firewalls, access controls, encryption).
* **Detective:** Controls aimed at identifying or detecting security incidents (e.g., intrusion detection systems, log monitoring, audit trails).
* **Corrective:** Controls that respond to and fix security issues once detected (e.g., patching systems, disaster recovery plans).
* **Deterrent:** Controls that dissuade malicious actors from attempting security breaches (e.g., warnings, legal penalties).
* **Compensating:** Controls that mitigate the risk of a vulnerability or weakness when other controls can't fully address it (e.g., encryption compensating for weak authentication).
* **Recovery:** Controls designed to restore operations after an incident (e.g., backups, business continuity planning).


### Control Enforcement Categories (How the Control is enforced...)
* **Mandatory:** The control is required and must be implemented exactly as specified by the framework. There is no flexibility in its implementation.
* **Addressable:** The control is recommended, but an organization may either implement it as specified, implement a compensating control, or justify why it is not applicable.

## Implementations
Implementations are the actual means and methods we use to implement a control. Implementations relate to one or many controls and can satisfy the requirements of a control in various ways. For example, a control that requires a password to be at least 8 characters long can be implemented by configuring a system to enforce this requirement using a specific procedure or technology.
