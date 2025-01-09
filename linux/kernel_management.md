---
layout: post
---

# Kernel Management

- See what CMD a system was booted with:
```
root@mariadb:~# cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-6.8.0-50-generic root=UUID=19c5ce25-a085-434c-8ae2-bbb8be11756d ro quiet splash
```

## Configure kernel parameters
### Persistent change:
Use the command: 
```
sysctl -w <TUNABLE_CLASS>.<PARAMETER>=<TARGET_VALUE> >> /etc/sysctl.conf
sysctl -p
```

### Non-persistent change: 
Use the command:
```
sysctl <TUNABLE_CLASS>.<PARAMETER>=<TARGET_VALUE>
```

## Kernel modules:
- Located at **/lib/modules/$(uname -r)**
- Modules utilities: 
    - **lsmod**: List loaded modules.
    - **modprobe**: Load or unload modules, using a pre-built module database with dependency and location information.
    - **depmod**: Rebuild the module dependency database.
    - **modinfo**: Display information about a module.
