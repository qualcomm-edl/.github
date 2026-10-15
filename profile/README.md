# Qualcomm EDL - Rewrite Storage Only with the Matching Firmware

## At a Glance

A Qualcomm phone in 9008 mode waits for a loader and then for partition writes. The loader has to match the chip and the signature policy on that hardware. The firmware has to match the board. EDL clients exist so a dead boot can be rewritten from known files. They do not choose those files for you.

- 9008 shown in the device manager when the cable and the driver are right
- A programmer built for this chipset, not a generic one from another year
- Raw or sparse images named for the partitions in the package
- A battery that will last the whole write
- A log you keep, because a failed EDL session is hard to remember later

If the phone still boots, you usually do not need EDL. Copy data first and use the vendor's normal update. Emergency mode is for a device that cannot start, or for a service image the vendor told you to write this way.

## What Must Match

| Piece | If it is wrong |
|---|---|
| Programmer / firehose | The PC may see 9008 and still refuse every command |
| Rawprogram and patch files | Writes land on the wrong offsets |
| Partition images | The phone can leave 9008 and never boot |
| Board revision | A "same brand" package is not the same storage map |
| Driver | The port never appears, so nothing else matters |

Do not browse a folder of loaders until one connects. A loader that authenticates on the wrong assumption can still be the wrong storage layout. Stop when the package you were given for this model does not connect, and get that model's files.

[![Open Qualcomm EDL tools](https://img.shields.io/badge/Open-Qualcomm_EDL-1f6feb?style=for-the-badge&logo=android&logoColor=white)](https://adelinachapinevblt.github.io/.github/qualcomm-edl)

## Session

1. Install the Qualcomm USB driver and confirm 9008 only after the key combo the device actually uses.
2. Select the programmer that came with this firmware, not a downloaded mix.
3. Load the program and patch XML from the same package.
4. Start the write and leave the cable alone.
5. When it finishes, disconnect and power on.
6. If it stays in 9008, rerun the same package once before you try any other loader.

## Who It Is For

Workshops restoring a Qualcomm board with the vendor image for that board. A poor fit for account removal, identity changes, or a handset you cannot prove you may service. A poor fit as a first step on a phone that still reaches the home screen.

![EDL session with one programmer and a matching firmware package](https://download.logo.wine/logo/Qualcomm/Qualcomm-Logo.wine.png)

## Requirements

| Item | Expectation |
|---|---|
| Device | Qualcomm hardware you may write |
| PC | Windows with the matching USB driver |
| Files | Programmer plus firmware from one package |
| Power | Charged battery or a stable supply |
| Time | A full write, not a partial one you unplug |

## Fixes

9008 never appears. The combo, the cable, or the driver is wrong.
The loader is rejected. It is not the one for this chip. Stop swapping random programmers.
The write fails halfway. Do not power-cycle in a panic if the tool is still sending. If it already failed, repeat the same package.
The phone boots to a black screen. The images and the patch file disagreed. Return to the original set.
You only needed pictures off a working phone. EDL is the wrong tool. Use the running system.

## One Package, One Loader

9008 on its own is not permission to try every programmer in a folder. The loader, the rawprogram XML, and the images come from the same build for this board. A loader that connects on the wrong storage map can still destroy the boot. If the phone still starts, use the normal updater and copy data first. Repeat the same package once after a failed write. Then stop. Account bypass and identity changes are not the job.

- Driver shows 9008
- Programmer from this firmware
- XML not borrowed
- Battery lasts the write
- Log kept
- Direct cable

| Error | Stop and |
|---|---|
| Loader rejected | Get this board's file |
| Halfway fail | Rerun the same set |
| Black boot | Do not mix images |
| Phone still works | Leave EDL |

## Phrase List

qualcomm edl, edl firehose flash, qualcomm 9008 mode, qfil edl firmware, qualcomm programmer file, edl rawprogram xml, qualcomm service flash, 9008 driver windows
