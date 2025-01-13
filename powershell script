# PowerShell Script to Secure Windows Group Policy Settings

# Run the script as an administrator
if (-not [System.Security.Principal.WindowsIdentity]::GetCurrent().IsSystem) {
    Write-Host "Please run the script as an administrator!" -ForegroundColor Red
    exit
}

# Set Windows Update Policies to Automatically download and install updates
Write-Host "Configuring Windows Update Settings..."
Set-GPRegistryValue -Name "Windows Update" -Key "HKLM\Software\Policies\Microsoft\Windows\WindowsUpdate" -ValueName "AUOptions" -Type DWord -Value 4
Set-GPRegistryValue -Name "Windows Update" -Key "HKLM\Software\Policies\Microsoft\Windows\WindowsUpdate" -ValueName "ScheduledInstallDay" -Type DWord -Value 0
Set-GPRegistryValue -Name "Windows Update" -Key "HKLM\Software\Policies\Microsoft\Windows\WindowsUpdate" -ValueName "ScheduledInstallTime" -Type DWord -Value 3

# Configure password policy settings (strong password requirement)
Write-Host "Configuring Password Policy Settings..."
Set-GPRegistryValue -Name "Password Policy" -Key "HKLM\Software\Microsoft\Windows\CurrentVersion\Policies\System" -ValueName "MinimumPasswordLength" -Type DWord -Value 12
Set-GPRegistryValue -Name "Password Policy" -Key "HKLM\Software\Microsoft\Windows\CurrentVersion\Policies\System" -ValueName "MaximumPasswordAge" -Type DWord -Value 30
Set-GPRegistryValue -Name "Password Policy" -Key "HKLM\Software\Microsoft\Windows\CurrentVersion\Policies\System" -ValueName "MinimumPasswordAge" -Type DWord -Value 1
Set-GPRegistryValue -Name "Password Policy" -Key "HKLM\Software\Microsoft\Windows\CurrentVersion\Policies\System" -ValueName "PasswordComplexity" -Type DWord -Value 1

# Configure lockout policy settings
Write-Host "Configuring Account Lockout Policy Settings..."
Set-GPRegistryValue -Name "Account Lockout Policy" -Key "HKLM\Software\Microsoft\Windows\CurrentVersion\Policies\System" -ValueName "LockoutBadCount" -Type DWord -Value 5
Set-GPRegistryValue -Name "Account Lockout Policy" -Key "HKLM\Software\Microsoft\Windows\CurrentVersion\Policies\System" -ValueName "ResetCount" -Type DWord -Value 15
Set-GPRegistryValue -Name "Account Lockout Policy" -Key "HKLM\Software\Microsoft\Windows\CurrentVersion\Policies\System" -ValueName "LockoutDuration" -Type DWord -Value 15

# Enforce UAC (User Account Control) for elevated processes
Write-Host "Enforcing User Account Control (UAC)..."
Set-GPRegistryValue -Name "User Account Control" -Key "HKLM\Software\Microsoft\Windows\CurrentVersion\Policies\System" -ValueName "EnableLUA" -Type DWord -Value 1
Set-GPRegistryValue -Name "User Account Control" -Key "HKLM\Software\Microsoft\Windows\CurrentVersion\Policies\System" -ValueName "ConsentPromptBehaviorAdmin" -Type DWord -Value 2
Set-GPRegistryValue -Name "User Account Control" -Key "HKLM\Software\Microsoft\Windows\CurrentVersion\Policies\System" -ValueName "PromptOnSecureDesktop" -Type DWord -Value 1

# Disable SMBv1 to protect against vulnerabilities
Write-Host "Disabling SMBv1 Protocol..."
Set-GPRegistryValue -Name "SMB Settings" -Key "HKLM\System\CurrentControlSet\Services\LanmanServer\Parameters" -ValueName "SMB1" -Type DWord -Value 0

# Enable Windows Defender Antivirus
Write-Host "Enabling Windows Defender Antivirus..."
Set-GPRegistryValue -Name "Windows Defender" -Key "HKLM\Software\Policies\Microsoft\Windows Defender" -ValueName "DisableAntiSpyware" -Type DWord -Value 0

# Configure audit policy for account logon and logoff
Write-Host "Configuring Audit Policy Settings..."
Set-GPRegistryValue -Name "Audit Policy" -Key "HKLM\Software\Microsoft\Windows\CurrentVersion\Policies\Audit" -ValueName "AuditLogon" -Type DWord -Value 1
Set-GPRegistryValue -Name "Audit Policy" -Key "HKLM\Software\Microsoft\Windows\CurrentVersion\Policies\Audit" -ValueName "AuditLogoff" -Type DWord -Value 1

# Enforce BitLocker drive encryption for data protection
Write-Host "Enabling BitLocker Drive Encryption..."
Enable-BitLocker -MountPoint "C:" -EncryptionMethod Aes256 -UsedSpaceOnly -TpmProtector

# Enforce Windows Defender Firewall
Write-Host "Enforcing Windows Defender Firewall..."
Set-NetFirewallProfile -Profile Domain,Public,Private -Enabled True

Write-Host "Security configurations applied successfully!"

# Exit script
exit
