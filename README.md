# Sanoid Snap

Sanoid is a policy-driven snapshot management tool for ZFS filesystems.

This is an unoffical snap not developed by the Sanoid developers!

Refer to the following GitHub page for more information: https://github.com/jimsalterjrs/sanoid

## Usage

### Snap Interfaces

As Sanoid makes extensive use of system interfaces to control ZFS, there are a number of interfaces that need to be connected:

```
snap connect sanoid:hardware-observe
snap connect sanoid:load-zfs
snap connect sanoid:kernel-module-observe
snap connect sanoid:mount-observe
snap connect sanoid:removable-media
snap connect sanoid:system-observe
```

You will also need the following slot definition in your gadget snap:

```
slots:
  dev-zfs:
    interface: custom-device
    custom-device: zfs
    devices:
      - /dev/zfs
```

Then connect the interface with the following command:

```
snap connect sanoid:dev-zfs <gadget name>:dev-zfs
```

### Configuration

You will need to create a Sanoid configuration file here: `/var/snap/sanoid/common/sanoid.conf`

E.g.:

```
[path/to/volume]
    daily = 7
    weekly = 7
    monthly = 4
```

Refer to the Sanoid documentation for more information on this syntax
