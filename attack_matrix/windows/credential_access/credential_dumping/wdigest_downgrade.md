# WDigest Downgrade
## Technique ID
T1003_wdigest


## Description
Windows 8.1 introduced a registry setting that allows for disabling the storage of the user’s logon credential in clear text for the WDigest provider.

(HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\WDigest\UseLogonCredential)


## Hypothesis
Adversaries are updating the registry value of \WDigest\UseLogonCredential to 1 in order to grab clear text passwords from memory contents of lsass in my environment.


## Events

| Source | EventID | EventField | Details | Reference | 
|--------|---------|-------|--------|-----------| 
| Sysmon | 13 | TargetObject | HKLM\System\CurrentControlSet\Control\SecurityProviders\WDigest\UseLogonCredential | [Cyb3rWard0g](https://twitter.com/Cyb3rWard0g) |
| Sysmon | 13 | Details | 1 | [Cyb3rWard0g](https://twitter.com/Cyb3rWard0g) |


# Atomic Sysmon Configuration
[T1003_wdigest.xml](https://github.com/Cyb3rWard0g/ThreatHunter-Playbook/blob/master/attack_matrix/windows/sysmon_configs/T1003_wdigest.xml)


## Hunter Notes
 * Monitor for any changes to the registry key


## Hunting Techniques Recommended

- [ ] Grouping
- [x] Searching
- [ ] Clustering
- [ ] Stack Counting
- [ ] Scatter Plots
- [ ] Box Plots
- [ ] Isolation Forests