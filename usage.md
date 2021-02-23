# Dependency

pip3 install scikit-build

pip3 install ninja meson

# Build & Install

./configure --target-list=aarch64-softmmu --meson=/home/michael/.local/bin/meson --ninja=/home/michael/.local/bin/ninja --enable-kvm --prefix=/usr

make

sudo make install

# Images

Disk image: Ubuntu cloud image

Cloud-init: Cloud-hypervisor modified in CI

# Usage

qemu-system-aarch64 -smp 4 -m 1024 -M virt -nographic -device virtio-blk-device,drive=image -drive if=none,id=image,file=bionic-server-cloudimg-arm64.img -device virtio-blk-device,drive=cloud -drive if=none,id=cloud,file=cloudinit.img -netdev user,id=user0 -device virtio-net-device,netdev=user0 -cpu host -enable-kvm -cpu host -drive file=/usr/share/AAVMF/AAVMF_CODE.fd,if=pflash,format=raw,unit=0,readonly=on
