# Building Images

* Setup

```bash
sudo apt update
sudo apt upgrade -y
sudo apt install qemu-user-static -y
sudo update-binfmts --enable qemu-aarch64
mkdir -p ./sd-images
```

```bash
docker build -t sd-images https://github.com/johang/sd-card-images.git
```

#

### raspberry Pi 2

* build boot image

```bash
docker run --rm -v ./sd-images:/artifacts sd-images build-boot raspberrypi_2b bcm2836 rpi_2_defconfig arm-linux-gnueabihf
```

* build ubuntu jammy

```bash
docker run --rm -v ./sd-images:/artifacts sd-images build-debian ubuntu armhf jammy
```

#

### Raspberry Pi 3b+

* build boot image

```bash
docker run --rm -v ./sd-images:/artifacts sd-images build-boot raspberrypi_3b_plus bcm2837 rpi_3_defconfig aarch64-linux-gnu
```

* build ubuntu jammy

```bash
docker run --rm -v ./sd-images:/artifacts sd-images build-debian ubuntu arm64 jammy
```
