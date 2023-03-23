# iMac 12,x iGPU (IGD) full disable

Removes the IGD device (Bus 0 Device 2 Function 0) from the PCI bus.  
IGD device (HD 2000 or HD 3000) will not be seen by OS and will not use any hardware resources.  
Fixes Windows BSOD when loading Intel Graphics Kernel Mode driver (igdkmd64.sys)

## How it works

Patches PEI module PlatformStage1Pei to force `SaPlatformPolicyPpi->GtConfig->InternalGraphics = 0`.  
This variable is used later by bios code to initialize the iGPU. If value is 0 the iGPU is hidden from PCIe bus and left uninitialized.  
Effect is the same as selecting "Disable Integrated Graphics" or "Disable onboard video" in other vendors bios.

## How to apply patch

Patch can be applied to your previously backed up eeprom using ``UEFIPatch``:

```
UEFIPatch my_bios.img igpu-disable.txt -o new_bios.img
```

After applying it, program ``new_bios.img`` back to eeprom chip.   

## Notes

- Tested on iMac 12,x with bootrom 87.0.0.0.0. May work on other Mac models and versions. If you try it watch UEFIPatch output for clues.
- Sleep works after applying patch.
