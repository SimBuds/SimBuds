# Workstation

The machines behind [the lab](README.md#the-lab): a Ryzen 9 5900X / RTX 3080 desktop that dual-boots Windows 11 and Arch Linux and serves the [Local-LLM](https://github.com/SimBuds/Local-LLM) router, plus an always-on ZBOX mini PC.

## Hardware

| Component | Detail |
|---|---|
| CPU | AMD Ryzen 9 5900X (12C/24T, 105 W TDP) |
| CPU tuning | PBO on Motherboard limits, Curve Optimizer on Auto (no offsets). Set in BIOS, so it applies to both OSes. |
| CPU cooling | AIO liquid cooler |
| Motherboard | ASUS TUF GAMING X570-PRO (WI-FI), BIOS 5044 |
| Memory | 32 GB (2 x 16 GB) G.Skill F4-3600C16-16GTZN, Samsung B-die, DDR4-3600 16-16-16-36 at 1.35 V, 1T, GDM on, dual channel |
| GPU | GIGABYTE RTX 3080 GAMING OC 10G 2.0 (LHR), 10 GB GDDR6X, 370 W power limit |
| PSU | Corsair HX850 (850 W). Estimated worst-case draw 605 to 630 W. |
| Drive 1 | Micron 2200V 512 GB NVMe (PCIe 3.0 x4), Windows |
| Drive 2 | Samsung 980 PRO 1 TB NVMe (PCIe 4.0 x4), Arch Linux |
| Network | Intel I225-V 2.5 GbE, Intel Wi-Fi/Bluetooth |
| Displays | Gigabyte M27Q P (165 Hz), ASUS VG279QM (240 Hz) |

### Drive health (smartctl, 2026-11-18)

| Drive | Health | Host writes | Power-on hours | Media errors |
|---|---|---|---|---|
| Drive 1 (Micron 2200V) | 76% | 27.51 TiB | 2,868 | 0 |
| Drive 2 (Samsung 980 PRO) | 88% | 98.08 TiB | 7,521 | 0 |

### Memory timings (XMP)

| Group | Values |
|---|---|
| Primary | 16-16-16-36, tRC 85, 1T, GDM on |
| Secondary | tRRDS 7, tRRDL 10, tFAW 38, tWTRS 5, tWTRL 14, tWR 26, tRTP 14, tCWL 16 |
| Refresh | tRFC 630 (350 ns), tREFI 14029 |
| Turnaround | tRDWR 18, tWRRD 7, tRDRDSCL 5, tWRWRSCL 5 |
| Voltages | VSOC 1.08 V, VDDG CCD 0.947 V, VDDG IOD 1.048 V, CLDO VDDP 0.900 V |
| Termination | ProcODT 43.6 Ω, RttNom off, RttWr RZQ/3, RttPark RZQ/1, drive strengths 24 Ω |

---

## Windows 11 (Drive 1)

### System and apps

| Item | Detail |
|---|---|
| OS | Windows 11 Pro x64 (26H2), UEFI, TPM on, Secure Boot off |
| GPU driver | GeForce 621.01 |
| Memory mode | XMP, FCLK = UCLK = 1800 MHz (1:1) |
| Resizable BAR | Enabled (16 GB) |
| GPU tuning | MSI Afterburner undervolt: flat 1920 MHz at 875 mV, memory +0, power limit 100%, temp limit 83 °C |
| Apps | MSI Afterburner, HWiNFO64 |

### Benchmarks

| Test | Conditions | Result (mean of 3 runs where listed) |
|---|---|---|
| Superposition 1080p Extreme, OpenGL | Stock voltage, 3 runs | 9811 (9801 to 9824). FPS 73.38 avg, 57.98 min, 94.49 max |
| Superposition 1080p Extreme, DirectX | Undervolt | 11,060 |
| Cyberpunk 2077 built-in, 1440p RT Ultra, DLSS Auto | Stock voltage, game 2.5, DLSS Transformer Model 2, 3 runs | 73.48 FPS avg (73.25 to 73.74). 65.31 min, 82.36 max |
| Cyberpunk 2077 built-in, same settings | Undervolt, game 2.31, DLSS CNN model, 3 runs | 73.89 FPS avg (73.74 to 74.16). 66.82 min, 81.18 max |
| Cyberpunk 2077 gameplay, 40 min | Undervolt, same settings | 70.9 FPS median, 54.7 to 81.5 (5th to 95th percentile), 56.9 1% low |
| Cinebench 2026 Multi-core | Old Curve Optimizer offsets (since removed) | 4,995 (stock 5900X reference 4,783) |
| Cinebench 2026 Single Core | Old Curve Optimizer offsets (since removed) | 485 |
| Cinebench 2026 GPU | Undervolt | 54,081 |
| 3DMark (all demo tests), 32 min | Undervolt, stress test only | No score recorded |

### Temps and power (avg / max)

GPU rows are filtered to >90% GPU load, except the gameplay column, which covers the whole session.

| Sensor | 3DMark (undervolt) | Superposition (stock) | Cyberpunk benchmark (stock) | Cyberpunk gameplay (undervolt) |
|---|---|---|---|---|
| GPU core temp (°C) | 63 / 69 | 69 / 71.7 | 64.5 / 67.4 | 60 / 65.8 |
| GPU hot spot (°C) | 74 / 81 | 80 / 83.9 | 76.8 / 80.6 | 72 / 78 |
| GPU memory junction (°C) | 71 / 78 | 75 / 78 | n/a | 70 / 76 |
| GPU power (W) | 300 / 356 | 346 / 349 | 338 / 344 | 237 / 323 |
| GPU clock (MHz) | 1932 / 1935 | 1866 / 1905 | 1888 / 1935 | 1887 / 1935 |
| GPU core voltage (V) | 0.87 / 0.88 | 0.97 / 0.99 | 0.98 / 1.06 | about 0.88 |
| GPU fan | 70% / 76% | 77% / 80% | 71% / 75% | 70% / 73% |
| Peak VRAM (GB) | 6.3 | 4.2 | 9.7 | 9.9 |
| CPU temp, Tctl (°C) | 60 / 80.5 | 61 / 68.5 | 63.3 / 67.4 | 65 / 71.4 |
| CPU package power (W) | 88 / 145 | 91 / 114 | 129 / 139 | 124 / 142 |
| Drive 1 temp (°C) | 56 / 71 | 55 / 64 | n/a | 55 / 59 |
| Drive 2 temp (°C) | 41 / 42 | 42 / 42 | n/a | 41 / 42 |

Other readings from the 3DMark run: coolant 34 / 36 °C, chipset 69 / 70 °C, DIMMs 43 / 45 °C, +12 V rail 11.88 to 12.08 V.

**Stability:** no CPU or GPU thermal throttling and zero PCIe errors in any run. At stock voltage the GPU sits on its power limit. With the undervolt it hit the limit in 26 of 994 3DMark samples.

---

## Arch Linux (Drive 2)

### System and apps

| Item | Detail |
|---|---|
| OS | Arch Linux, linux-zen kernel, installed 2026-04-27 with archinstall |
| Boot | systemd-boot, with Windows as a menu entry. Windows boot files live on the Drive 2 ESP, so Windows needs Drive 2 to boot. |
| Filesystem | btrfs (`compress=zstd:3`), subvolumes `@`, `@home`, `@log`, `@pkg`. Swap is 15.6 GB zram. |
| Desktop | KDE Plasma 6 on Wayland |
| GPU driver | nvidia-open-dkms 620.70.06. The benchmarks below ran on 615.78.08. |
| Resizable BAR | Enabled (16 GB) |
| GPU tuning | Stock |
| Apps | Steam (Proton), lm_sensors, nvtop, snapper, fwupd |
| Snapshots | snapper takes a daily snapshot of `/home` and keeps 3 daily and 2 weekly. `~/VMs`, `~/models` and the Steam library are separate subvolumes, so snapshots skip them. |

### Benchmarks

| Test | Conditions | Result (mean of 3 runs where listed) |
|---|---|---|
| Superposition 1080p Extreme, OpenGL | Stock voltage, 3 runs | 9653 (9607 to 9676). FPS 72.20 avg, 57.91 min, 89.06 max |
| Cyberpunk 2077 built-in, 1440p RT Ultra, DLSS Auto | Stock voltage, game 2.5, DLSS Transformer Model 2, Proton 11.0-2e, 3 runs | 73.17 FPS avg (73.10 to 73.30). 63.77 min, 83.74 max |
| Cyberpunk 2077 built-in, same settings | LACT undervolt (since removed), 3 runs | 72.54 FPS avg (71.82 to 73.40). 62.25 min, 83.97 max |
| memtest_vulkan (VRAM), 14 min | Stock | 0 errors in 41,321 iterations. 607.7 GB/s write, 666.1 GB/s check (avg) |

### Temps and power (Superposition, stock, >90% GPU load)

| Sensor | Avg | Max |
|---|---|---|
| GPU core temp | 69 °C | 72 °C |
| GPU hot spot | n/a | n/a (not exposed on Linux) |
| GPU power | 343 W | 348 W |
| GPU clock | 1866 MHz | 1965 MHz |
| GPU fan | 76% | 80% |
| Peak VRAM | n/a | 5.1 GB |
| CPU temp (Tctl) | 61 °C | 71.2 °C |
| Drive 2 temp | 43 °C | 45 °C |

**Stability:** power limited for the whole run, with no thermal slowdown and no kernel or driver errors.

---

## Windows vs Arch

Both at stock GPU voltage. Sensor rows come from Superposition at >90% GPU load. Windows reads from HWiNFO and Arch from `nvidia-smi` and `lm_sensors`, so a degree or a few watts can come from the tools alone.

| Metric | Windows 11 | Arch Linux | Difference |
|---|---|---|---|
| Superposition score (mean) | 9811 (73.38 FPS avg) | 9653 (72.20 FPS avg) | Windows +1.6%, larger than the run-to-run spread |
| Superposition FPS min / max (mean) | 57.98 / 94.49 | 57.91 / 89.06 | Same on min, Windows +6.1% on max |
| Cyberpunk built-in FPS avg (mean) | 73.48 | 73.17 | Windows +0.4%, inside the run-to-run spread |
| Cyberpunk built-in FPS min / max (mean) | 65.31 / 82.36 | 63.77 / 83.74 | Windows +2.4% on min, Arch +1.7% on max |
| GPU temp avg / max | 69 / 71.7 °C | 69 / 72 °C | Same |
| GPU power under load | 346 W | 343 W | Same |
| GPU clock under load | 1866 MHz | 1866 MHz | Same |
| CPU max temp under load | 68.5 °C | 71.2 °C | Arch 2.7 °C warmer |

Performance is effectively the same on both. Windows stays the choice for Cyberpunk with ray tracing, which hangs the GPU under Proton.

---

## ZBOX (always-on mini PC)

A fanless ZOTAC ZBOX CI321 nano that runs a Hermes Agent Discord bot for friends all the time. The model stays on the desktop's llama.cpp router, reached through a reverse SSH tunnel that the desktop opens, so the desktop needs no SSH server. When the desktop is asleep or off, the bot gives a fixed offline reply from code, with no model call. It is a separate box, not a service on the desktop, so the bot stays up while the desktop sleeps and friends' messages, which are untrusted input, never share a machine with the personal agent, its memory, or its tokens.

| Component | Detail |
|---|---|
| CPU | Intel Celeron 2961Y (2 cores) |
| Memory | 2 GB DDR3L at 1,333 MT/s, 1.35 V (one slot). About 390 MB used at idle, about 900 MB spare with the bot answering. An 8 GB stick is the upgrade if it starts swapping. |
| Drive | Toshiba MQ01ABD032 320 GB 2.5" HDD. SMART passed, 0 bad sectors, about 5,500 hours, lifetime max 76 °C, so it needs airflow. |
| Network | Intel Wireless 3160 (in use, power save off), 2x Realtek RTL8111/8168 gigabit (unused) |
| OS | Debian 13, no desktop, UEFI with GRUB on the removable path |
| Apps | Hermes Agent (Discord gateway with a custom sports-odds plugin), SSH server |
| Access | The bot runs as an unprivileged user without sudo. The tunnel account has no shell and can open only the one router forward. |
