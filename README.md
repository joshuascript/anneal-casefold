# anneal
### Native case-insensitive directories on Linux

anneal turns any Linux directory case-insensitive by backing it with a real ext4
filesystem formatted with the kernel's built-in `casefold` option. Your files
stay put. Your apps stop caring about case.

## About

- **Kernel-native** — no FUSE overlay, no userspace translation. Full ext4
  performance at every read and write.
- **Non-destructive** — anneal stashes your existing files, mounts the new
  image, and restores them automatically. Nothing is lost.
- **Conflict-aware** — before mounting, anneal scans for case-colliding files
  and lets you resolve them interactively.
- **Persistent** — mounts are written to `/etc/fstab` automatically on creation
  and survive reboots without any extra steps.

## How it works

anneal creates a sparse ext4 disk image with `-O casefold` enabled, loop-mounts
it over your target directory, and sets the casefold attribute. The result is a
real ext4 filesystem where `File.txt` and `file.txt` are the same file — resolved
at the kernel level, not through a compatibility shim.

## Requirements

- `python3`
- `e2fsprogs >= 1.45` (`mkfs.ext4`, `debugfs`)
- `losetup`, `findmnt`

## Install

```bash
./install.sh
```

To uninstall:

```bash
./install.sh --uninstall
```

> Uninstalling removes `/opt/anneal`, `/usr/local/bin/anneal`, and the udev rule.
> Your images and data in `/var/lib/anneal/` are left intact.

## Commands

| Command | Description |
|---|---|
| `select <directory>` | Set the active directory for subsequent commands |
| `create [directory]` | Create a casefold mount and add it to `/etc/fstab` |
| `remove [directory]` | Unmount and remove the image, preserving all files |
| `list` | Show all anneal mounts with status |
| `fix` | Clear ghost volumes from Nautilus |

## Example

```bash
anneal create ~/Documents/sbox-public
```

Or select first and reuse:

```bash
anneal select ~/Documents/sbox-public
anneal create
```
