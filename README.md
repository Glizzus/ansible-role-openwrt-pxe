# Ansible Role: OpenWRT PXE Server

An ansible role that installs and configures a PXE server for an OpenWRT DHCP server.

## Requirements

No special requirements; note that this role requires root access, so either run it in a playbook with a global become: yes, or invoke the role in your playbook like:

```yaml

- hosts: all
  roles:
    - role: openwrt-pxe
      become: true
```

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

```yaml
openwrt_pxe_usb_filesystem: ext4
```

The filesystem of the USB drive. You may need to change this to `vfat`, `exfat`, or other common filesystems.

```yaml
openwrt_pxe_mountpoint: /mnt/extstorage
```

The mountpoint of the USB drive. This is where the PXE server will store the OpenWRT images.

```yaml
openwrt_pxe_device: /dev/sda1
```

The device of the USB drive. This is where the PXE server will store the OpenWRT images.

## Dependencies

- `community.general` collection (for the `community.general.opkg` module)

## Example Playbook

```yaml
- hosts: all
  roles:
    - role: openwrt-pxe
      vars:
        openwrt_pxe_usb_filesystem: exfa4
        openwrt_pxe_mountpoint: /mnt/usb
        openwrt_pxe_device: /dev/sda2
      become: true
```

## License

MIT
