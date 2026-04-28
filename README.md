## MountScript
# Create Windows-style directories on Linux

MountScript converts any folder on your machine from a case-sensitive
directory to a case-insensitive one at a system level by using ext4 mounts.

This will eventually be installable on bash, but for now you can run the command
from the local folder

sudo ./mountscript
sudo ./mountscript select {DIRECTORY}
sudo ./mountscript create {DIRECTORY||none} : leave empty if select was used
sudo ./mountscript list : lists all case insensitive mounts managed by this cli
sudo ./mountscript remove {DIRECTORY} : safely cleans up and removes the mount point preserving folder
sudo ./mountscript permanent {DIRECTORY} : (not implemented)
sudo ./mountscript fix : clears ghost volumes on Nautilus
