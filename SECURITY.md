# Security policy

This policy covers Logicly and its installers and release assets. Logicly sits between an AI agent,
a project and a controller that runs a machine. Report anything that weakens the checks between them.

## Report a vulnerability

[Report a vulnerability privately](https://github.com/zanotra/logicly-releases/security/advisories/new)
through GitHub. Do not open a public issue, discussion or pull request for a security problem.

Include:

- The Logicly version and your operating system.
- The steps to reproduce the problem, with a minimal example that contains no customer data.
- The expected result, the actual result and what an attacker gains.

If the problem can make a machine move or change state without a person's approval, say so in the first line.
We read those reports first. Use an emulator or an isolated test environment for a reproduction.

We acknowledge reports within one week. Fixes ship in a new release.
We publish the advisory after the fixed release is available. There is no bug bounty.

Only the latest release receives security fixes. Check whether a newer release already fixes the problem.
You can still report a suspected vulnerability in an older release or a prerelease.

## In scope

- A write reaching a hardware-class target without a live arm or a bench flag.
- A target classified as an emulator when it is not one.
- A download, test run or implode that proceeds while validation has findings.
- Access to the daemon's routes without its token when it binds beyond loopback.
- Access to the daemon's routes as an engine agent without a valid agent token.
- An engine agent or client that trusts a certificate other than the daemon CA it pinned.
- A daemon request that reads or deletes a file outside its workspaces.
- An installer that accepts an archive that does not match the release's `checksums.txt`.
- Suspected tampering with a published installer or release asset.

## Out of scope

- **Anything an agent can already do as you.** The arming gate prevents accidents.
  It is not a sandbox for a hostile agent. An agent with your account can read your config and token,
  and run any command you can. Run untrusted agents in a separate account or VM.
- **Other users on a loopback daemon's machine.** A daemon bound to loopback does not require its
  token unless started with `--require-auth`. Use that flag on a machine with other users.
- **A bench flag that works as designed.** It keeps a target armed, and only a person can set it.
- **What validation does not check.** Validation is a static check. Each report lists what it does not check.
  A program that passes validation and misbehaves is not, by itself, a vulnerability in Logicly.
- **Studio 5000, Logix Echo, the Logix Designer SDK or controller firmware.** Report those problems
  to Rockwell Automation.
- **Scanner or AI-generated reports with no working reproduction.** Include evidence of a specific problem.
