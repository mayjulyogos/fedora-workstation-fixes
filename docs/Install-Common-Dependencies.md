# Updates and Install dependencies
```bash
sudo dnf install -y --skip-unavailable \
  https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm \
  https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm \
  @development-tools \
  cmake make automake autoconf libtool binutils \
  gcc gcc-c++ \
  kernel-devel kernel-headers dkms \
  acpid fuse-libs libxcrypt-compat systemd-devel \
  libglvnd-glx libglvnd-opengl libglvnd-devel \
  mesa-libGLU \
  vulkan-tools vulkan-loader-devel \
  libevdev-devel \
  libcurl-devel curl aria2 \
  python3-pip python3-devel \
  python3.11 python3.11-libs \
  git pkgconfig \
  @virtualization \
  libva-nvidia-driver \
  libavcodec-freeworld \
  libva-utils \
  lm_sensors \
  kmodtool \
  akmods \
  mokutil \
  openssl \
  firewall-config \
  android-tools
  
sudo systemctl enable --now libvirtd
sudo usermod -aG libvirt $USER
```
