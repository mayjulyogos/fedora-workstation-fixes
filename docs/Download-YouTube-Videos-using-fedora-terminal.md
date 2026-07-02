## Purpose

Download YouTube videos and audio using yt-dlp.

<br>

## Features

- Video download
- Audio extraction
- Browser cookie support
- AV1 video support

<br>

## Commands

```bash
sudo dnf install yt-dlp -y
sudo dnf install nodejs -y
curl -fsSL https://deno.land/install.sh | sh
echo 'export DENO_INSTALL="$HOME/.deno"' >> ~/.bashrc
echo 'export PATH="$DENO_INSTALL/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
deno --version

sudo dnf install https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
sudo dnf swap ffmpeg-free ffmpeg --allowerasing
sudo dnf install gstreamer1-plugins-libav gstreamer1-plugins-bad-free-extras gstreamer1-plugins-bad-nonfree gstreamer1-plugins-ugly lame-libs --allowerasing

yt-dlp --remote-components ejs:github --no-playlist --cookies-from-browser firefox --extractor-args "youtube:player_client=android_vr,web_embedded" -f "bestvideo+bestaudio/best" --merge-output-format mkv --postprocessor-args "ffmpeg:-c:v copy -c:a flac" "https://www.youtube.com/watch?v=UvV74ex-02M" # video and audio
yt-dlp --remote-components ejs:github --no-playlist --cookies-from-browser firefox --extractor-args "youtube:player_client=android_vr,web_embedded" -f "bestaudio" -x --audio-format flac "https://www.youtube.com/watch?v=xZ3-_Tx0Kfg" # audio only
```

<br>

## Verification

```bash
yt-dlp --version
```

Expected:

```text
2025.x.x
```

or newer.

<br>

## Notes

Browser cookies allow downloading content that requires login.
Added instructions for installing FFmpeg and GStreamer plugins for video processing.
