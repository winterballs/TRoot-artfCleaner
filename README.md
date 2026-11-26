# Temp Root Artifact Cleaner

A lightweight KernelSU / Magisk module that automatically removes leftover temporary root and CVE exploit artifacts from `/data/local/tmp` upon root startup.

## Why is this needed?
When escalating privileges via temporary root exploits (such as CVE-2026-43499), helper binaries and payloads remain in `/data/local/tmp`. Modern root detectors scan this directory for known signatures and flag the device even after KernelSU has finished loading.

## Cleaned Artifacts
On every boot (`late_start service` stage), the module safely deletes the following files from `/data/local/tmp` without touching any system partitions or unrelated user binaries:
- `ksu-helper`
- `ksu-payload`
- `ksud`
- `temp_su`
- `libcve43499root.so`

## Installation
1. Download the latest release ZIP (or pack the repository files into a `.zip` archive).
2. Open **KernelSU** / **KernelSU-Next** -> **Modules**.
3. Tap **Install** and select the ZIP file.
4. On subsequent root startups, cleanup runs automatically in the background.

note:
its only for temp root
