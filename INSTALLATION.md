# Installing a Linux system

At the time of writing, after having escaped from the very poorly documented [declarative hellscape of `NixOS`](https://nixos.org/), I have decided to use `Ubuntu 24.04 LTS` as my main operating system. Here follows my notes on the installation process.

## Downloading the ISO image

I downloaded the ISO image from the [official Ubuntu website](https://ubuntu.com/download/desktop). I chose the 64-bit version for desktops. You can quickly check the integrity of the downloaded file by running the following command in the terminal:

```bash
sha256sum ubuntu-24.04-desktop-amd64.iso
```

At the time of writing, the correct hash is `c2e6f4dc37ac944e2ed507f87c6188dd4d3179bf4a3f9e110d3c88d1f3294bdc`.

## Creating a bootable USB stick

The suggested method for creating a bootable USB stick is to use the [`Balena Etcher`](https://etcher.balena.io/). It is rather straightforward to use. Just select the downloaded ISO image, the USB stick, and click `Flash!`.

This step took about 10 minutes on my machine. Gently take out the USB stick after the process is complete - here somehow I managed to split one of my USB sticks in half, so try not to do that.

## Booting from the USB stick

After creating the bootable USB stick, you can boot from it by restarting your computer and pressing the appropriate key to enter the BIOS settings. This key is different for different computers, but it is usually one of the following: `F2`, `F10`, `F12`, or `DEL`. On recent windows machines, you may need to [enable the access to BIOS from the operative system configuration](https://www.asus.com/support/faq/1008829/).

One rather unintuitive step that I found necessary for the installation to work was to enable the [`Input–output memory management unit, or IOMMU,`](https://en.wikipedia.org/wiki/Input%E2%80%93output_memory_management_unit) in the BIOS. This has different names and locations in different BIOS versions, depending on the associated CPU. Specifically, in Intel-based systems you will find it called [`Intel® Virtualization Technology`](https://www.intel.com/content/www/us/en/content-details/774206/intel-virtualization-technology-for-directed-i-o-architecture-specification.html), while on AMD-based systems it is called [`IOV`](https://www.amd.com/content/dam/amd/en/documents/processor-tech-docs/specifications/48882_IOMMU.pdf).

I am unsure why a virtualization technology is necessary for booting from a USB stick, but it is seemingly necessary for the installation to work.

While updating the BIOS settings, you also want to make sure that the boot order is set to boot from the USB stick first.

If you have not enabled the IOMMU, you might encounter `error '/boot' not found` followed by a seemingly okay set of boot options, which inevitably lead to `Unable to find a medium containing a live file system`.

## Installing Ubuntu

After booting from the USB stick, you will be presented with the usual Ubuntu setup installation process. Pay special attention to the disk selection step, as the default option I had wanted to install ubuntu on my 18TB data disk instead of the NVME, which would have been a disaster.

Furthermore, during the installation process, you will be asked whether to proceed connecting to a Wi-Fi network. After I inserted the Wi-Fi password, the installation process hanged for several minutes, after which I decided to try again without connecting to the Wi-Fi. Unexpectedly, the installation process then proceeded **connecting to the wifi**, so I am unsure what the initial hang was about. Maybe it was just a coincidence and it had resumed the installation process for some other reason.

And that's it! After the installation process is complete, you can remove the USB stick and restart your computer. You should now have a fresh Ubuntu installation ready to be configured to your liking.
