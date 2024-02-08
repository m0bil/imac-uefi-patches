# iMac 12,x Turbo Overclocking Enable

This firmware patch enables CPU Turbo Overclocking and allows setting the Max Turbo Multipliers of the CPU.

## How it works

Turbo Overclocking allows the CPU to reach core multipliers above its rated Processor Base Frequency.

The number of Turbo Bins (Intel terminology for a 100MHz multiplier) is fused at manufacture time and the CPU will not run above its fused value.

For Sandy Bridge non-K cpus Turbo Overclocking is limited to 4 Bins above the Processor Base Frequency. 

For -K CPUs the number of Bins is unlimited. For Xeon CPUs the number of Bins is 0.

Also, on standard setup the Turbo Bins depend on the number of active physical cores: 4 Bins are used when only one core is used, 3 Bins when 2 cores are used, 2 Bins when 3 cores are used and 1 Bin when all 4 cores are used.

As an example, an i7-2600 CPU with Processor Base Frequency rated at 3400 MHz will Turbo run at 3500 MHz when 4 cores are used and at 3800 MHz when just one core is used.

This patch allow independently setting the Max Core multipliers depending on the number of physical cores used. You will mostly always set the four max core multipliers to the same value.

For ease of use I have provided two version of the patch, one sets the 4 max multipliers to x40, and another that sets them to x44, otherwise they are identical. You can also look inside the patch and set your own max multiplier values.

This patch also works for non-K cpus. Setting the max multiplier to the same value on a non-K cpu will allow all four cores to run 4 Bins above the Processor Base Frequency (instead of just one Bin). This means an i7-2600 can run 4 cores at 3800 MHz instead of 3500 MHz without the patch, a nice ~8% speed increase in multi-core use.

For non-K cpus you can safely set the max multiplier higher than the cpu supports, but it will not run faster than the fused value, so you can use the x40 patch for non-K cpus.

## How to apply patch

Patch can be applied to your previously backed up eeprom using ``UEFIPatch``:

```
UEFIPatch my_bios.img turbo-OC-40.txt -o new_bios.img
```

After applying it, program ``new_bios.img`` back to eeprom chip.   

## Notes

- Tested on iMac 12,x with bootrom 87.0.0.0.0.
- May work on other macs with Sandy Bridge CPUs, pending to be tested.
