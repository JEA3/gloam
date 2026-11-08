![gif](gif.gif)

# gloam

An internet radio and music player for the terminal, with a visualiser based on the animated background of [lpx.org.uk](https://lpx.org.uk).

It plays internet radio (Icecast, SHOUTcast and HLS streams, `.pls` and `.m3u` links) and any local audio file ffmpeg can read, and draws a shader in the terminal that reacts to the sound.

## Requirements

- Python 3.8 or later
- [numpy](https://numpy.org)
- [ffmpeg](https://ffmpeg.org)
- macOS or Linux

Optional:

- [sounddevice](https://python-sounddevice.readthedocs.io) for sound, and the closest sync between picture and sound. Without it, gloam falls back to ffmpeg's macOS audio output, ffplay, paplay, pw-cat, aplay or SoX's `play`.
- [certifi](https://pypi.org/project/certifi/) to read song titles from https streams on Python builds without system certificates.

```
pip install numpy sounddevice certifi
brew install ffmpeg        # or: apt install ffmpeg
```

## Usage

```
./gloam https://ice1.somafm.com/groovesalad-128-mp3
./gloam https://somafm.com/groovesalad.pls
./gloam song.flac other.mp3          # several sources: n / b to move between them
./gloam stations.m3u                 # a playlist of stations or files
./gloam URL --palette ember --hold
./gloam URL --react wild             # off, subtle, gentle, normal, lively, strong, wild, extreme, unhinged, or 0 to 10
./gloam URL --ahead 180              # run the picture 180 ms ahead of the sound (default 130)
./gloam URL --volume 60
./gloam URL --no-sound               # the picture only
```

Display options include `--full`, `--mini [C]`, `--num` and `--chunky` (cell layouts), `--256`, `--nocolour`, `--fps`, `--speed`, `--size WxH`, `--hue`, `--brightness`, `--colour` and `--white`. Run `./gloam --help` for the full list.

## Keys

| Key | Action |
| --- | --- |
| `n` / `b` | next / previous source |
| up / down (or `0` / `9`) | louder / quieter |
| `m` | mute |
| `r` / `R` | react more / less |
| `{` / `}` | picture earlier / later against the sound, 10 ms a press |
| `p` | next palette now |
| `h` | hold the palette / let it change |
| `+` / `-` | turn the colours round the colour wheel |
| `[` / `]` | darker / brighter |
| `<` / `>` (or `,` / `.`) | colours move slower / faster |
| `i` | show where the sound is going |
| `q` | quit (Ctrl-C works too) |

## Licence

MIT. See [LICENSE](LICENSE).
