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

yt-dlp --remote-components ejs:github --no-playlist --cookies-from-browser firefox --extractor-args "youtube:player_client=android_vr,web_embedded" -f "bestvideo+bestaudio/best" --merge-output-format mkv --postprocessor-args "ffmpeg:-c:v copy -c:a flac" "https://www.youtube.com/watch?v=UvV74ex-02M" # video and audio
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
