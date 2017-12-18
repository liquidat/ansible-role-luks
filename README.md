# Role Name

Ansible role to decrypt and mount a LUKS encrpyted device.

## Role Variables

- `luks_crypt_name` - the name of the device which will be created at `/dev/mapper/{{ luks_crypt_name }}`
- `luks_crypt_device` - actual encrypted device, `/dev/` will be assumed, LUKS mount option is `luksOpen /dev/{{ luks_crypt_device }} {{ luks_crypt_name }}`
- `luks_pwd` - the password to decrypt the device, should be provided from a vault
- `luks_mount_path` - the path to mount the decrypted device
- `luks_fstype` - a file system type can be provided to the mount option; not used if empty
- `luks_mount_opts` - additional mount options, defaults to `noauto` if not provided

## The ugly

Since there is no proper module or API for LUKS, a shell command is used to decrypt the device and pipe the password to the process.

## License

MIT
