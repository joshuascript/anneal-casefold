# MountScript
### Create case-insensitive directories on Linux

MountScript converts any directory on your machine from case-sensitive to case-insensitive by backing it with an ext4 loop mount formatted with the `casefold` option.

## Usage

```bash
sudo ./mountscript <command> [directory]
```

## Commands

| Command | Description |
|---|---|
| `select <directory>` | Set the active directory for subsequent commands |
| `create [directory]` | Create a casefold mount (uses selected directory if omitted) |
| `remove [directory]` | Unmount and clean up, preserving all files (uses selected directory if omitted) |
| `list` | List all active MountScript mounts |
| `fix` | Clear ghost volumes from Nautilus |
| `permanent [directory]` | *(not yet implemented)* |
