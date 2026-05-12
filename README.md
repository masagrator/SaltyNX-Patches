# SaltyNX-Patches
Some useful asm64/asm32 patches for SaltyNX. They must be put to `SaltySD/patches/` folder. If you want to use it for specific game, put it into titleid folder, f.e. `SaltySD/patches/0100000000010000/`. Don't rename files, those names are important.

> Block updating clocks

**nn::oe::SetPerformanceConfiguration**:[asm64](BlockUpdatingClocks/_ZN2nn2oe27SetPerformanceConfigurationENS0_15PerformanceModeEi.asm64)/[asm32](BlockUpdatingClocks/_ZN2nn2oe27SetPerformanceConfigurationENS0_15PerformanceModeEi.asm32) - this function updates clocks, patch blocks it which is helpful if you are using overclocking and game too often uses this function, which results in irregular framedrops (using this patch results in handheld clocks being set to 1020/307/1331 at boot).

**nn::oe::SetCpuBoostMode**:[asm64](BlockUpdatingClocks/_ZN2nn2oe15SetCpuBoostModeENS0_12CpuBoostModeE.asm64)/[asm32](BlockUpdatingClocks/_ZN2nn2oe15SetCpuBoostModeENS0_12CpuBoostModeE.asm32) - this function enables boost mode which sets clocks to 1785 CPU and 76 GPU. It's designed to be used only in loading screens, but some games are using it when streaming assets takes too long which results in irregular framedrops. Patch blocks it which is helpful if you are using overclocking.

> Block copyright image

`All listed patches should be copied to not cause issues.`

**nn::oe::SetCopyrightVisibility**:[asm64](BlockCopyrightImage/_ZN2nn2oe22SetCopyrightVisibilityEb.asm64)/[asm32](BlockCopyrightImage/_ZN2nn2oe22SetCopyrightVisibilityEb.asm32) - this function sets if copyright image should be visible or not. Blocking this only is not enough because image is set to "visible" after using nn::oe::InitializeCopyrightFrameBuffer()

**nn::oe::SetCopyrightImage**:[asm64](BlockCopyrightImage/_ZN2nn2oe17SetCopyrightImageEPKvmiiiiNS0_16WindowOriginModeE.asm64)/[asm32](BlockCopyrightImage/_ZN2nn2oe17SetCopyrightImageEPKvmiiiiNS0_16WindowOriginModeE.asm32) - this function accepts image and where to put it.

**nn::oe::InitializeCopyrightFrameBuffer**:[asm64](BlockUpdatingClocks/_ZN2nn2oe30InitializeCopyrightFrameBufferEPvm.asm64)/[asm32](BlockUpdatingClocks/_ZN2nn2oe30InitializeCopyrightFrameBufferEPvm.asm32) - this function accepts buffer to use for storing image and other data necessary for copyright image.

> Block internet access

**nn::nifm::IsNetworkAvailable**:[asm64](BlockInternetAccess/_ZN2nn4nifm18IsNetworkAvailableEv.asm64)/[asm32](BlockInternetAccess/_ZN2nn4nifm18IsNetworkAvailableEv.asm32) - If game is using this function to check if you are connected to internet, patch returns information that you are not.

> Block suspending game

**nn::oe::SetFocusHandlingMode**:[asm64](BlockSuspending/_ZN2nn2oe20SetFocusHandlingModeENS0_17FocusHandlingModeE.asm64)/[asm32](BlockSuspending/_ZN2nn2oe20SetFocusHandlingModeENS0_17FocusHandlingModeE.asm32) - Block game from changing Focus Handling Mode to something else than "Never pause game in home menu". Helpful in games that disconnect you from server if you go to Home Menu.

> Block calling network error applet

**nn::nifm::PrepareHandlingNetworkRequestResult**:[asm64](BlockNetworkErrorHandling/_ZN2nn4nifm35PrepareHandlingNetworkRequestResultENS0_13RequestHandleEPNS_6applet19LibraryAppletHandleE.asm64)/[asm32](BlockNetworkErrorHandling/_ZN2nn4nifm35PrepareHandlingNetworkRequestResultENS0_13RequestHandleEPNS_6applet19LibraryAppletHandleE.asm32) - This function is used to generate an applet handle that is later used to call an applet that shows what network error game/nnSDK found. By returning error for this function we block creating handle and force anything that called it to immediately return. This way we don't get any network error popup, no memory leak and no handle exhaustion.

> Block calling error applet

**nn::err::ShowError(nn::Result)**:[asm64](BlockErrorApplet/_ZN2nn3err9ShowErrorENS_6ResultE.asm64)/[asm32](BlockErrorApplet/_ZN2nn3err9ShowErrorENS_6ResultE.asm32) - This specific variant of ShowError function is called by some network functions in nnSDK to show an error, f.e. 2155-8007. This patch blocks showing it.
