# "sshclictl"
## Overview
- This is a script for easily managing authorized public keys for SSH public key authentication.
- It operates on the `$HOME/.ssh/authorized_keys` file.
## Usage
### Only for the first execution
1. Generate your private and public key pair in advance using `ssh-keygen`.
2. Place this script in any directory included in your PATH.
3. Run `sshclictl help`.
### Subsequent usage
#### When you want to scan `authorized_keys`
- Simply running `sshclictl` will automatically scan the keys, so no special command is required.
- During the scan, public keys not present in the `known_keys.d` directory will be added to it. Each file will be named using the `username@hostname` part of the public key, where `@` is replaced with `-` and `.pub` is appended.
#### List of scanned public keys
- `sshclictl list`
#### Check whether a public key is enabled or disabled
- `sshclictl status <key_name>`
- To view the status of all keys, run the command without specifying a key name.
#### Disable a public key
- `sshclictl disable <key_name>`
#### Enable a public key
- `sshclictl enable <key_name>`
## Notes
- Disabled public keys are only removed from the `authorized_keys` file but remain in the `known_keys.d` directory (use the `delete` subcommand to completely remove them).

