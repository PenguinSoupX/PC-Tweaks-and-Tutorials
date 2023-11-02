## Guide to Brother HL-L2321D Printer Setup with Brlaser Driver for Duplex Printing and File Compatibility in Linux

**Brother HL-L2321D Printer:**

- [x] The 'D' in the name stands for duplex printing.

- [x] The HL-L2321D version is the Indian version, and the international version is HL-L2320D, but they are essentially the same.

- [x] There are two drivers for this printer: the official driver and the brlaser driver from pdewacht.

**brlaser v6 driver:**

- [x] Can do duplex printing.

- [x] Cannot print some JPG and PDF files, which might be related to the resolution of the files.

- [x] To resolve issues with some files, reducing the lines per block to 16 in the source code may help.

**Brother-hll2320d official driver:**

- [ ] The official driver can be downloaded from the Brother support website: [Official Brother Driver Download](https://support.brother.com/g/b/downloadtop.aspx?c=in&lang=en&prod=hll2321d_as)

- [x] .Can print every page.

- [ ] Can't seem to print duplex

**Steps to Make brlaser Work:**

- [x] Install brlaser from [https://github.com/pdewacht/brlaser](https://github.com/pdewacht/brlaser).

- [x] The tested version is version 6, released on September 6th, 2019.

- [x] A solution was found on [https://github.com/pdewacht/brlaser/issues/52](https://github.com/pdewacht/brlaser/issues/52).

- [x] User "0xAl3xH" suggested reducing the lines per block to 32 in "src/block.h" in the source code.

- [x] The suggested change should be inserted under the line "static const unsigned max_block_size_ = 16350;". However, you reduced it to 16 lines per block.

- [ ] More research is warranted to confirm if reducing the block lines is necessary.

- [x] After installing the modified brlaser driver, using the **Brother HL-L2340D series** driver in settings, it allowed printing for every file without any issues. It's unclear if the successful printing was due to changing the block lines or using another model printer in settings. More testing may be needed to confirm the cause of improved compatibility.

- [x] There is also a new repository for brlaser at https://github.com/Owl-Maintain/brlaser because the old one is not being maintained. Please check the new repository for the latest updates and fixes.

- [x] If all else fails, consider using a Windows virtual machine with USB passthrough for printing.

These steps have allowed you to print every file you know of along with duplex printing, which was not available with the official driver.
