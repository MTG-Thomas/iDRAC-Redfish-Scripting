# Repository guidance

This fork contains Dell PowerEdge iDRAC Redfish examples in `Redfish Python/` and PowerShell modules/scripts. Read `README.md` and the exact script or cmdlet before editing or executing it. The library spans BIOS, firmware, power, storage, credentials, virtual media, and server configuration profiles; these surfaces have different operational risks.

## Development

Keep Python and PowerShell example behavior consistent where an equivalent exists. Preserve Dell attribution and document any fork-specific changes. The README lists Python 3.x and PowerShell 5.0+ and generation-specific minimum iDRAC firmware versions. Verify the target's actual generation/firmware and endpoint support before using those examples; do not infer compatibility from a successful HTTP connection.

Inspect argument handling, Redfish requests, job polling, reboot requirements, and error paths together. Preserve quoting for credentials with special characters or domain-qualified usernames, while keeping their values out of transcripts and logs.

## Verification and live operations

No repository-wide automated CI/test gate was found in the current tree. Prefer the Redfish mockup-server approach linked in `README.md` to validate request construction and PATCH/POST behavior without affecting hardware. Record the simulation's limits; it does not prove firmware execution or storage safety.

Separate inventory reads from firmware updates, controller/disk changes, power actions, password changes, and configuration imports. For authorized mutations, bind the exact server and operation, inspect current state, use available preview paths, and verify job completion plus resulting state. Never test destructive storage, factory-reset, or power actions on an operational server as a development shortcut.
