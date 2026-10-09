# vm-bootstrap.sh

Sets up a fresh Debian/Ubuntu VM for coding agents. Run as root: `bash vm-bootstrap.sh` (see `--help`).

## Important: KVM with CPU type `host`

On generic CPU models (`kvm64`/`qemu64`), Claude Code **hangs forever** at step `[5/10] Claude Code`, because the VM doesn't see CPU features like SSE4.2 and POPCNT.
Set the CPU type to `host` (Proxmox: Hardware → Processors → Type), then power the VM off and on again.

The script detects this, skips Claude Code and tells you. After fixing it: `bash ~/vm-bootstrap.sh --only claude`
