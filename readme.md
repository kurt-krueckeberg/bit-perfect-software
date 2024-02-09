# Bitperfect Playback Software Options

## Linux

- [Kodi](https://kodi.tv) is an entire media (video and audio) management and server package. 

- [Emby](https://emby.media/linux-server.html) Free. Is a media server. It is a `.deb` package.
  - [Installation instructions](https://emby.media/support/articles/Installation.html)
  - [Linux tip](https://emby.media/support/articles/Linux.html)

- [Daphile](https://daphile.com/) is a headless music server + OS. It also includes other music-related packages 
  like CD burning) + OS. If you do not have a wired network connection, hit F1 during installation boot-up and enter 
  --I think--you network id and password. I found this step confusing. 
  - [Install instructions](https://daphile.com/download/DaphileInstallation.pdf) 
  - [youtube install guide](https://www.youtube.com/watch?v=iydBilo5UXI)
  - Not actively supported.

- [LibreELEC](https://libreelec.tv/) is billed as "Just enough OS for KODI." The SD creator currently only runs on Windows. 
   It is not clear if you can install it on a PC?

- [JRiver Media Center for Linux](https://yabb.jriver.com/interact/index.php/topic,134152.0.html?PHPSESSID=rhveois6o75ro6639ebqvlmp81)

- [Rune Audio](https://www.runeaudio.com/) is a version of Arch Linux.
   - free.
   - It is not designed to be installed on PCs rather on devices like Raspberry PI.

- [Universal Media Server](https://www.universalmediaserver.com/download/)

- [Open Source Media Center](https://osmc.tv)
  - Only installs on three devices--Apple TV, Vero 4K (a custom device from OSMC) and Rsspberry PI.
  - free
  - comes as AppImage. To run the AppImage, you must install the fuse package, then you can make the AppImage 
    executable.

- [Volumio OS](https://volumio.org) -- is a free OS that can be installed on Raspberry PI and PC. The PC install on the MeLe Mini PC, using a USB, did not work 
  for me. 

## Windows

- [Foobar 2000](https:///www.foobar2000.org)
  - Free
  - Windows-only.
  - bitperfect playback.

- [Audirvana](https://audirvana.com/) is Windows-only.
Others. See <https://circuitdigest.com/article/top-media-server-software-for-music-streaming-on-raspberry-pi>

## Windows

- Audirvana+ Windows

- Foobar on Windows + chord audio drivers.

- MUSIChi software suite

- XXHE. No real written docs just a forum.

## Check Bitrate and Bitdepth on Linux

## Misc

Answers

[Setting Default ALSA Sound Device](https://www.alsa-project.org/wiki/Setting_the_default_device): 

> For USB devices, all possible parameters are listed in `/proc/asound/cardX/stream0`.

Contents of [/proc/asound/card1/pcm0p/sub0/hw_params explained](https://askubuntu.com/questions/1213559/how-can-i-see-the-current-bit-depth-of-the-playing-audio-stream):

> The `hw_params` file shows the sample format in the format: line. `S24_3LE` indicates 24-bit, little-endian samples.

> The `streamX` file shows the sample format in the "Interface" section of the selected "Altset".


Example:


Output of `kurt@kurt-Airtop3:/proc/asound/card1/stream0`:

```
Creative Technology Ltd Sound Blaster X4 at usb-0000:00:14.0-4, high speed : USB Audio

Playback:
  Status: Running
    Interface = 4
    Altset = 4
    Packet Size = 168
    Momentary freq = 191976 Hz (0x17.ff3b)
    Feedback Format = 16.16
  Interface 4
    Altset 1
    Format: S16_LE
    Channels: 2
    Endpoint: 0x01 (1 OUT) (ASYNC)
    Rates: 48000, 96000, 192000
    Data packet interval: 125 us
    Bits: 16
    Channel map: FL FR
    Sync Endpoint: 0x83 (3 IN)
    Sync EP Interface: 4
    Sync EP Altset: 1
```

```
kurt@kurt-Airtop3:/proc/asound/card1/pcm0p$ cat sub0/hw_params 
access: RW_INTERLEAVED
format: S24_3LE
subformat: STD
channels: 2
rate: 192000 (192000/1)
period_size: 24000
buffer_size: 96000
```
