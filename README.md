# SaltyNX-Patches
Some useful asm64 patches for SaltyNX. They must be put to `SaltySD/patches/` folder. If you want to use it for specific game, put it into titleid folder, f.e. `SaltySD/patches/0100000000010000/`.

> Block updating clocks

[nn::oe::SetPerformanceConfiguration](https://github.com/masagrator/SaltyNX-Patches/blob/main/BlockUpdatingClocks/_ZN2nn2oe27SetPerformanceConfigurationENS0_15PerformanceModeEi.asm64) - this function updates clocks, patch blocks it which is helpful if you are using overclocking and game too often uses this function, which results in irregular framedrops (using this patch results in handheld clocks being set to 1020/307/1331 at boot).
[nn::oe::SetCpuBoostMode](https://github.com/masagrator/SaltyNX-Patches/blob/main/BlockUpdatingClocks/_ZN2nn2oe15SetCpuBoostModeENS0_12CpuBoostModeE.asm64) - this function enables boost mode which sets clocks to 1785 CPU and 76 GPU. It's designed yo use only in loading screens, but some games are using it when streaming assets takes too long which results in irregular framedrops. Patch blocks it which is helpful if you are using overclocking.
