---
title: "Microsoft Is Killing Third-Party Encryption. Your Keys Are Already in the Cloud."
date: 2026-04-09
categories: [Analysis]
tags: [microsoft, bitlocker, veracrypt, encryption, privacy, windows]
excerpt: "Microsoft terminated the accounts used to sign VeraCrypt and WireGuard drivers. Windows 11 silently encrypts drives with BitLocker and uploads recovery keys to the cloud. Every decision moves the ecosystem in the same direction: toward encryption you do not control."
---

## The account termination

On March 30, 2026, Mounir Idrassi posted to SourceForge to explain where he had been.

Microsoft had terminated the account he used for years to sign Windows drivers and the VeraCrypt bootloader. He received no notification, no explanation, and no appeal path.

VeraCrypt is free open-source full-disk encryption software and the most widely used independent alternative to BitLocker on Windows. Its latest installer had been downloaded close to a million times since May 2025.

Without a valid signed certificate, Idrassi cannot release new Windows versions of VeraCrypt. Users who enabled system encryption may face boot issues after July 2026 because Microsoft will revoke the certificate authority used to sign the bootloader.

After Idrassi's post circulated on Hacker News, WireGuard creator Jason Donenfeld said the same thing had happened to him. His account was suspended after he released an update. He entered a 60-day recovery process and still cannot publish. Donenfeld noted that if a critical remote code execution vulnerability were discovered, he would be unable to deploy a fix to Windows users.

Idrassi's attempts to reach support produced only AI-generated responses. He was unable to reach a human being.

---

## Why signing matters

VeraCrypt operates at the kernel level. To encrypt a drive it must load a driver into the Windows kernel. Microsoft's Driver Signing requirements mean the OS checks each driver against a revoked certificate list. For users with Hypervisor-Protected Code Integrity enabled the block is absolute. The system refuses to load the driver, leaving users unable to mount their encrypted volumes.

The available workaround is to disable Driver Signature Enforcement via the Windows Recovery Environment, or run Windows in Test Mode using `bcdedit /set testsigning on`. Doing so disables the protections that prevent malware from installing kernel-mode drivers. To recover access to encrypted data, users must instruct the OS to stop verifying who is allowed to touch the hardware.

---

## The pattern

The VeraCrypt account termination is one event in a longer sequence.

Rufus is a utility used to create bootable Windows install media. It is also the primary tool users rely on to install Windows without a Microsoft account, which is the condition that prevents BitLocker keys from being automatically uploaded to the cloud. In February 2026, Rufus developer Pete Batard reported that Microsoft was intentionally breaking the application's download scripts, preventing Rufus from downloading the latest Windows 11 Insider Preview builds. Batard noted that breaking the script requires active involvement. He stated in a GitHub thread: "I'm pretty sure Microsoft paid one of their employees to figure out a way to break the Fido downloads explicitly, and then implemented that."

Microsoft has not confirmed this. Downloads were eventually restored after Rufus patched around the block.

On the local account front, the record is clearer. Starting with builds 26220.6772 and 26120.6772 in October 2025, commands like `bypassnro` and `ms-cxh:localonly` no longer work, forcing users to connect to the internet and sign in during setup. Microsoft has been systematically removing or disabling those shortcuts, a process that accelerated through 2024 and 2025.

Features such as BitLocker key escrow, Windows Hello recovery, and settings sync depend on an online identity. Microsoft's explicit release-note language signals product intent: they are closing consumer-facing setup shortcuts and favoring supported provisioning paths.

A local account during setup is the only default-path option that prevents BitLocker keys from being automatically uploaded to Microsoft's servers. Each removed bypass is one fewer way to avoid that.

On the encryption side, Windows 11 24H2 automatically enables BitLocker encryption on most modern hardware when installing Windows with a Microsoft account during setup. Encryption starts seamlessly and silently in the background, covering even Home editions and desktop computers that historically escaped full-disk encryption defaults. Not only is the C: drive encrypted, but all other drives connected to the machine are encrypted as well during reinstallation.

Opting out requires editing the registry before installation completes.

BitLocker automatic device encryption starts during the out-of-box experience. Protection is enabled only after users sign in with a Microsoft account or Azure Active Directory account. BitLocker automatic device encryption is not enabled with local accounts. The conditions for cloud key upload and for silent full-disk encryption are identical: a Microsoft account at setup. Microsoft has spent two years making that account harder to avoid.

---

## What BitLocker does with your keys

Windows 11 defaults to requiring a Microsoft account during setup. The OS automatically ties the BitLocker recovery key to that account.

In early 2025, the FBI seized three laptops encrypted with BitLocker in a fraud investigation in Guam. Investigators could not access them. They obtained a search warrant directing Microsoft to provide the recovery keys. Microsoft complied in February 2025. The keys had been automatically uploaded to Microsoft's cloud when the devices were configured with Microsoft accounts.

A 2025 court document from an ICE forensic expert stated the agency "does not possess the forensic tools to break into devices encrypted with Microsoft BitLocker." The encryption is sound. The key storage is the issue.

Microsoft confirmed it receives approximately 20 such requests annually and complies with valid legal orders.

---

## The architectural choice

Cryptography researcher Matthew Green at Johns Hopkins wrote: "This is private data on a private computer and they made the architectural choice to hold access to that data."

Microsoft spokesperson Charles Chamberlayne said the company "believes customers are in the best position to decide how to manage their keys." The default makes the decision before most users know the choice exists.

Choosing local-only storage requires knowing the option exists and understanding that losing a password could mean losing the data permanently. The default is cloud storage and requires no deliberate action.

ACLU surveillance counsel Jennifer Granick noted that once a precedent exists for US law enforcement, foreign governments can point to it and make the same demand.

Senator Ron Wyden said it was "simply irresponsible for tech companies to ship products in a way that allows them to secretly turn over users' encryption keys."

---

## What this looks like from the outside

Each of these events has an innocent explanation. Account re-verification programs generate false positives. Local account requirements exist to enable cloud features. Default encryption protects users who would not otherwise enable it. ISO download blocks are fraud prevention.

The issue is that every individual decision moves the ecosystem in the same direction: toward BitLocker, toward Microsoft accounts, toward cloud key storage, and away from tools that do not give Microsoft access to keys.

When your security depends on a third-party tool, but that tool's ability to function depends on a single corporate account's standing with a trillion-dollar vendor, you are not in control of your data. You are renting permission to encrypt it.

---

## What to do

Check the Microsoft account website. It lists which devices have BitLocker recovery keys in the cloud and lets you delete them.

If you use VeraCrypt on Windows, monitor the SourceForge forum. Do not install builds from unofficial sources.

Using a local Windows account prevents BitLocker keys from being automatically uploaded. Creating one at setup currently requires editing the registry or using Rufus to build the install media. Both of those paths have been narrowed once already. There is no reason to expect the narrowing has stopped.
