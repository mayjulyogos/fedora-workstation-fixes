## Purpose

Download YouTube videos and audio using yt-dlp.

## Features

- Video download
- Audio extraction
- Browser cookie support
- AV1 video support




## Commands

```bash
sudo dnf install yt-dlp -y
sudo dnf install nodejs -y
curl -fsSL https://deno.land/install.sh | sh
echo 'export DENO_INSTALL="$HOME/.deno"' >> ~/.bashrc
echo 'export PATH="$DENO_INSTALL/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
deno --version

yt-dlp --remote-components ejs:github --no-playlist --cookies-from-browser firefox -f "bv[vcodec^=av01]+ba/b" "https://www.youtube.com/watch?v=UvV74ex-02M" #video and audio

yt-dlp --remote-components ejs:github --no-playlist --cookies-from-browser firefox -f ba -x --audio-format wav "https://www.youtube.com/watch?v=UvV74ex-02M" #audio only
```




## Verification

```bash
yt-dlp --version
```

Expected:

```text
2025.x.x
```

or newer.

## Notes

Browser cookies allow downloading content that requires login.
