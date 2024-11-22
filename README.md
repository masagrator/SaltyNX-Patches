# SaltyNX-Patches
Some useful asm64/asm32 patches for SaltyNX. They must be put to `SaltySD/patches/` folder. If you want to use it for specific game, put it into titleid folder, f.e. `SaltySD/patches/0100000000010000/`. Don't rename asm64 files, those names are important.

> Block updating clocks

**nn::oe::SetPerformanceConfiguration**:[asm64](BlockUpdatingClocks/_ZN2nn2oe27SetPerformanceConfigurationENS0_15PerformanceModeEi.asm64)/[asm32](BlockUpdatingClocks/_ZN2nn2oe27SetPerformanceConfigurationENS0_15PerformanceModeEi.asm32) - this function updates clocks, patch blocks it which is helpful if you are using overclocking and game too often uses this function, which results in irregular framedrops (using this patch results in handheld clocks being set to 1020/307/1331 at boot).

**nn::oe::SetCpuBoostMode**:[asm64](BlockUpdatingClocks/_ZN2nn2oe15SetCpuBoostModeENS0_12CpuBoostModeE.asm64)/[asm32](BlockUpdatingClocks/_ZN2nn2oe15SetCpuBoostModeENS0_12CpuBoostModeE.asm32) - this function enables boost mode which sets clocks to 1785 CPU and 76 GPU. It's designed to be used only in loading screens, but some games are using it when streaming assets takes too long which results in irregular framedrops. Patch blocks it which is helpful if you are using overclocking.

> Block copyright image

`All listed patches should be copied to not cause issues.`

**nn::oe::SetCopyrightVisibility**:[asm64](BlockCopyrightImage/_ZN2nn2oe22SetCopyrightVisibilityEb.asm64)/[asm32](BlockCopyrightImage/_ZN2nn2oe22SetCopyrightVisibilityEb.asm32) - this function sets if copyright image should be visible or not. Blocking this only is not enough because image is set to "visible" after using nn::oe::InitializeCopyrightFrameBuffer()

**nn::oe::SetCopyrightImage**:[asm64](BlockCopyrightImage/_ZN2nn2oe17SetCopyrightImageEPKvmiiiiNS0_16WindowOriginModeE.asm64)/[asm32](BlockCopyrightImage/_ZN2nn2oe17SetCopyrightImageEPKvmiiiiNS0_16WindowOriginModeE.asm32) - this function accepts image and where to put it.

**nn::oe::InitializeCopyrightFrameBuffer**:[asm64](BlockCopyrightImage/_ZN2nn2oe30InitializeCopyrightFrameBufferEPvm.asm64)/[asm32](BlockCopyrightImage/_ZN2nn2oe30InitializeCopyrightFrameBufferEPvm.asm32) - this function accepts buffer to use for storing image and other data necessary for copyright image.

> Block internet access

**nn::nifm::IsNetworkAvailable**:[asm64](BlockUpdatingClocks/_ZN2nn4nifm18IsNetworkAvailableEv.asm64)/[asm32](BlockUpdatingClocks/_ZN2nn4nifm18IsNetworkAvailableEv.asm32) - If game is using this function to check if you are connected to internet, patch returns information that you are not.
