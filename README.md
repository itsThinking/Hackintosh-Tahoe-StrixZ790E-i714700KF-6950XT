# :apple: Strix Z790-E + i7-14700KF + 6950 XT
<br>
**macOS**: Tahoe (26.0.1)<br>
**OpenCore**: 1.0.6 (release 2025-09-11)
<br>
Farewell to Hackintosh and thank you for all the work [Acidanthera](https://github.com/acidanthera)!
I assembled this build with the notion of running macOS Tahoe with the best hardware for at least the next 1-2 years, as Intel support has now dropped. These years of experimentation with Hackintoshes was also what made Apple so great, as the founders started out the same way. Despite the eventual proprietary ways of Apple, I know Steve Jobs and Woz would have been Hackintoshers themselves.
<br>
:white_check_mark: iMessage<br>
:white_check_mark: Continuity<br>
:ballot_box_with_check: AirDrop (Hackintosh-to-Device [one-way], "Allow me to be discovered by: Everyone" isn't letting me select it)<br>
:no_entry: Bluetooth (Turns on but drops connections)<br>
:white_check_mark: Wi-Fi (HeliPort)<br>
:white_check_mark: FileVault<br>
:white_check_mark: Sleep<br>
:white_check_mark: Power Management<br>
:white_check_mark: DRM Playback<br>
:white_check_mark: SSD TRIM<br>
:white_check_mark: CFG Lock Removed<br>
:white_check_mark: Audio (via built-in monitor speaker for now)<br>
:x: Boot Chime (Files/Settings are there, but finish when I have speakers)<br>
<br>
| Hardware |                                                              |
| -------- | ------------------------------------------------------------ |
| Mobo     | **ASUS ROG STRIX Z790-E Gaming WiFi** (note: *not* version II)<br />Chipset: Z790, Ethernet: Intel I226-V, Wi-Fi: AX210, Audio: ALC4080 |
| CPU      | **Intel Core i7-14700KF** (Raptor Lake Refresh)              |
| GPU      | **PowerColor Red Devil AMD Radeon RX 6950 XT**               |
| RAM      | **32GB Corsair Vengeance DDR5 6000MHz** (2 x 16GB)           |
| SSD      | **2TB WD_BLACK SN850X NVMe**                                 |
| BT/Wi-Fi | **BCM94360CD** (*<u>Optional</u>*: I have this card in case there is a way to support Bluetooth again. Wi-Fi is handled by the motherboard) |


**<u>Benchmarks</u>**

Scores are comparing this Hackintosh vs. Mac Studio M4 Max 14-Core CPU/32-Core GPU:

| Cinebench       | Strix Z790-E | M4 Max |
| --------------- | ------------ | ------ |
| GPU**           | 7,943        | 16,574 |
| CPU Multi-Core  | **2,009**    | 1,811  |
| CPU Single-Core | 129          | 186    |

**Cinebench GPU test seems to be far more optimized for Apple Silicon GPUs, see Geekbench scores below + Shadow of the Tomb Raider tests

| Geekbench       | Strix Z790-E | M4 Max  |
| --------------- | ------------ | ------- |
| CPU Single-Core | 2,922        | 4,038   |
| CPU Multi-Core  | 17,499       | 23,509  |
| GPU OpenCL      | **116,903**  | 100,867 |
| GPU Metal       | **236,274**  | 159,479 |

| Shadow of the Tomb Raider @ 1440p/Highest/No AA | Strix Z790-E | M4 Max |
| ----------------------------------------------- | ------------ | ------ |
| Low FPS                                         | **90**       | 66     |
| Avg FPS                                         | **116**      | 90     |

| Amorphous Disk Mark | Strix Z790-E (Read) | M4 Max (Read) | Strix Z790-E (Write) | M4 Max (Write) |
| ------------------- | ------------------- | ------------- | -------------------- | -------------- |
| SEQ1M QD8           | ***6,851.77***      | 6,461.81      | 6,111.67             | 7,285.36       |
| SEQ1M QD1           | ***4,670.55***      | 3,342.05      | 4,934.23             | 7,322.58       |
| RND4K QD64          | 507.17              | 1,241.28      | ***382.09***         | 173.10         |
| RND4K QD1           | ***80.47***         | 59.30         | ***461.29***         | 32.37          |



**<u>ASUS BIOS Settings</u>**

Advanced<br>
	CPU Configuration<br>
		CPU - Power Management Control<br>
			CPU C-States = **Enabled**<br>
	Platform Misc Configuration<br>
		Native ASPM = **Enabled**<br>
		DMI ASPM = **Auto**<br>
		DMI Gen3 ASPM = **Auto**<br>
		PEG - ASPM = **L0sL1**<br>
	PCH-FW Configuration<br>
		PTT = **Enabled**<br>
	Trusted Computing<br>
		Security Device Support = **Disabled** (this is TPM)<br>
	UEFI Variables Protection<br>
		Password protection of Runtime Variables = **Disabled**<br>
Boot<br>
	Fast Boot = **Disabled**<br>
	Setup Mode = **Advanced Mode** (optional)<br>



**<u>Important Notes</u>**

- BIOS version ***must*** be 1801, anything beyond breaks the setup when ACPIs are trying to load

- CFG Lock command for `Modified GRUB Shell`:
  ```setup_var_cv CpuSetup 0x44 0x01 0x00```

- I originally had the Samsung 990 Pro NVMe, but faced issues dealing with mass files (even with `NVMeFix`), so I got the recommended WD_BLACK series

- If dual booting, select macOS as the startup disk via `System Settings` -> `General` -> `Startup Disk`

- Of course, HeliPort must be installed later for Wi-Fi

  

**<u>TODO</u>**

- Bluetooth via BCM94360CD card, if possible ([Possible Broadcom Fix for Tahoe](https://www.tonymacx86.com/threads/success-with-broadcom-bcm943602cdp-wifi-under-tahoe.332619/))

- Speakers + Boot Chime

- Make AirDrop two-way

  
