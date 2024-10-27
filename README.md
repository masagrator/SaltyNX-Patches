# SaltyNX-Patches
Some useful asm64 patches for SaltyNX. They must be put to `SaltySD/patches/` folder. If you want to use it for specific game, put it into titleid folder, f.e. `SaltySD/patches/0100000000010000/`. Don't rename asm64 files, those names are important.

> Block updating clocks

[nn::oe::SetPerformanceConfiguration](BlockUpdatingClocks/_ZN2nn2oe27SetPerformanceConfigurationENS0_15PerformanceModeEi.asm64) - this function updates clocks, patch blocks it which is helpful if you are using overclocking and game too often uses this function, which results in irregular framedrops (using this patch results in handheld clocks being set to 1020/307/1331 at boot).

[nn::oe::SetCpuBoostMode](BlockUpdatingClocks/_ZN2nn2oe15SetCpuBoostModeENS0_12CpuBoostModeE.asm64) - this function enables boost mode which sets clocks to 1785 CPU and 76 GPU. It's designed to be used only in loading screens, but some games are using it when streaming assets takes too long which results in irregular framedrops. Patch blocks it which is helpful if you are using overclocking.

> Block copyright image

`All listed patches should be copied to not cause issues.`

[nn::oe::SetCopyrightVisibility](BlockCopyrightImage/_ZN2nn2oe22SetCopyrightVisibilityEb.asm64) - this function sets if copyright image should be visible or not. Blocking this only is not enough because image is set to "visible" after using nn::oe::InitializeCopyrightFrameBuffer()

[nn::oe::SetCopyrightImage](BlockCopyrightImage/_ZN2nn2oe17SetCopyrightImageEPKvmiiiiNS0_16WindowOriginModeE.asm64) - this function accepts image and where to put it.

[nn::oe::InitializeCopyrightFrameBuffer](BlockCopyrightImage/_ZN2nn2oe30InitializeCopyrightFrameBufferEPvm.asm64) - this function accepts buffer to use for storing image and other data necessary for copyright image.
