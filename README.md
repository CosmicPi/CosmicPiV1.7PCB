# CosmicPiV1.6
Version 1.6 of the Cosmic Pi, learning the lessons from V2 and going back to something simpler. All the components are now on a single PCB with a snap-off for the SiPM elements. We have also moved to KiCad!

The SiPM's in this design are from Ketek, and we're very happy with the performance. You can find the SiPM datasheet here: https://www.ketek.net/wp-content/uploads/2018/12/KETEK-PM3325-WB-D0-Datasheet.pdf
The SiPM's are also available to purchase retail from their shop (!) - a significant advance over our previous models:
https://www.ketek.net/store/products/pm3325-wb/

The design uses scintillators from Amcrys http://www.amcrys.com/ which are not yet available via a retail outlet, however any BC-408 equivalent scintillator that has diamond polished finish surfaces and dimensions of 200x100x10mm can be mated to the SiPMs with suitable mounting holes.

# What do the signals do?


Shapeout 1 & 2 - Shaped (i.e. amplified and stretched signal from the SiPMs - muon detection waveforms). Not used in current software.

Biasfb 1 & 2 - Feedback on the Vbias supply (i.e. to check that it's the right voltage). Not used in current software.

Inj led 1 & 2 - Light injector LEDs, allowing the operation of the SiPM to be checked (and calibrated) post-assembly. 

Accint 1, 2 - Interrupts from the accelerometer, not really used for anything yet.

Magint 3 - Interrupt from magnetometer, also not used.

Flag, boot0 - Signals to the Raspberry Pi, flag can be set by the STM32 to indicate a particular condition. Boot0 is used to set the boot mode of the STM32, for example when flashing. This doesn't function correctly in this version, it will be updated for V1.7, due to some issues with the STM32 bootloader.

Vbusm otg dm otg dp - Vbus is the USB bus voltage detection line to the STM32 (i.e. in OTG mode, sense incoming voltage), DM and DP are the differential lines for USB communication. Not functional in the current software; note that the USB doesn't power the device.

Swclk, swdio - These are the programming commands for the STM32, based on the ST-Link system. These work fine, used for programming.
