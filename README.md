

---

# Secure Windows Group Policy Script

This PowerShell script helps secure Windows environments by automating the configuration of key Group Policy settings. It applies various security measures including Windows update settings, password policies, account lockout policies, user account control, and more.

## Table of Contents
- [Description](#description)
- [Key Areas of the Script](#key-areas-of-the-script)
- [Running the Script](#running-the-script)
- [Important Considerations](#important-considerations)
- [License](#license)

## Description

The **Secure Windows Group Policy Script** automates the configuration of several important security policies in Windows operating systems. These configurations aim to improve the security posture of a machine by enforcing best practices such as:

- Automatic Windows updates
- Strong password policies
- Account lockout policies
- Enforcing User Account Control (UAC)
- Disabling deprecated protocols like SMBv1
- Enabling Windows Defender Antivirus and Firewall
- Configuring BitLocker drive encryption
- Enabling security auditing for logon/logoff activities

## Key Areas of the Script

The script configures the following security settings:

1. **Windows Update Settings**: Configures automatic updates for the operating system.
2. **Password Policy**: Enforces strong password requirements (minimum length, complexity, expiration).
3. **Account Lockout Policy**: Configures account lockout after a set number of failed login attempts.
4. **User Account Control (UAC)**: Ensures UAC prompts for elevated privileges, improving security.
5. **SMBv1**: Disables the outdated SMBv1 protocol, mitigating the risk of attacks.
6. **Windows Defender Antivirus**: Ensures that Windows Defender Antivirus is enabled for protection.
7. **Audit Policy**: Configures auditing for logon and logoff activities to monitor user access.
8. **BitLocker**: Enables BitLocker encryption for system drive to protect sensitive data.
9. **Windows Defender Firewall**: Ensures that the Windows firewall is enabled for all profiles (Domain, Public, Private).

## Running the Script

1. Open **PowerShell** as **Administrator**.
2. Download the script or copy it directly from the repository.
3. Paste the script into the PowerShell window or run the script from a saved `.ps1` file.
4. Press **Enter** to execute the script.

## Important Considerations

- **Backup Group Policies**: Before making any changes, ensure that the current policies are backed up. This will allow you to restore settings if needed.
- **Test Environment**: It's highly recommended to test the script in a non-production environment first. This will ensure the script does not interfere with existing configurations or applications in your production environment.
- **Administrator Privileges**: The script requires administrative privileges to make changes to system policies.

---
