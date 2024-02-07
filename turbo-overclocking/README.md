# iMac 12,x Turbo Overclocking Enable

WIP

## How it works


## How to apply patch

Patch can be applied to your previously backed up eeprom using ``UEFIPatch``:

```
UEFIPatch my_bios.img turbo-OC-40.txt -o new_bios.img
```

After applying it, program ``new_bios.img`` back to eeprom chip.   

## Notes

- Tested on iMac 12,x with bootrom 87.0.0.0.0. 
