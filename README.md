## How to compile Android 6.0 for Pine A64

1. Checkout http://source.android.com/source/downloading.html
1. Create a new directory:
  ```
  mkdir android
  cd android
  ```

2. Initialize manifests:
  ```
  repo init -u https://android.googlesource.com/platform/manifest -b android-6.0.1_r74 --depth=1
  git clone https://github.com/Callahan633/local_manifests -b marshmallow .repo/local_manifests
  ```

3. Checkout sources:
  ```
  repo sync -c
  ```

4. Compile sources:
  ```
  source build/envsetup.sh
  # tulip_chihpd-eng: use for normal Android build with Launcher
  # tulip_chiphd_atv-eng: use for Android TV build with Leanback Launcher
  lunch tulip_chiphd-eng
  make
  ```

5. Create SD card image:
  ```
  sdcard_image pine64_android_6.img.gz
  ```

6. Write image to SD card with Rasplex Installer (this is multiplatform tool):
  https://github.com/RasPlex/rasplex-installer/releases or use `DD`.

## Changes

I did backport minimal amount of Allwinner changes to make it run.
You can see a commit history.

Callahan633: I had changed remote for kernel sources with fixes for WM8904 external codec on I2S Euler Bus (based on: https://github.com/looperlative/linux-pine64-armbian/commits/ramstadt) and added to manifest Gapps from their new remote on gitlab

## Author

Kamil Trzciński (ayufan@ayufan.eu)
