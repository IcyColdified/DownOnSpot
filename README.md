<div align="center">

# DownOnSpot

A Spotify downloader written in Rust

<img src="assets/icon.svg" alt="drawing" width="500"/>

<br>

[![Build project](https://github.com/oSumAtrIX/DownOnSpot/actions/workflows/build.yml/badge.svg)](https://github.com/oSumAtrIX/DownOnSpot/actions/workflows/build.yml)
[![GitHub license](https://img.shields.io/github/license/oSumAtrIX/DownOnSpot)](https://github.com/oSumAtrIX/DownOnSpot/blob/main/LICENSE)
[![GitHub issues](https://img.shields.io/github/issues/oSumAtrIX/DownOnSpot)](https://github.com/oSumAtrIX/DownOnSpot/issues)
[![GitHub forks](https://img.shields.io/github/forks/oSumAtrIX/DownOnSpot)](https://github.com/oSumAtrIX/DownOnSpot/network)
[![GitHub stars](https://img.shields.io/github/stars/oSumAtrIX/DownOnSpot)](https://github.com/oSumAtrIX/DownOnSpot/stargazers)
[![Stability: Experimental](https://masterminds.github.io/stability/experimental.svg)](https://masterminds.github.io/stability/experimental.html)

</div>

## 🆘 Help needed

> [!NOTE]
Currently, I am [rewriting DownOnSpot](https://github.com/oSumAtrIX/DownOnSpot/pull/68).  
If you want to help me accelerate this process, please feel free to contact me at [osumatrix.me](https://osumatrix.me).

## ⭐ Features

- ✅ Actually downloads from Spotify, free and premium
- ✅ Chose between 96, 160, 256 and 320 kbit/s (free users can't exceed 160kbit/s)
- ✅ Download tracks, playlists, albums and artists
- ✅ Multi-threaded
- ✅ Search for tracks
- ✅ Download MP3 and original OGG files
- ✅ Metadata tagging
- ✅ Simple CLI interface

> [!NOTE]
> Free Spotify users can not exceed 160kbit/s. Change the `quality` setting in the `settings.json` file to `Q160` or lower. If you want to download 256 or 320kbit/s, you need to use a premium account.

## ⚒️ Building

1. Clone the repository using git and change to the local repository directory:

   ```bash
   git clone https://github.com/oSumAtrIX/DownOnSpot.git
   cd DownOnSpot
   ```

2. Install dependencies

   If you are on Linux, make sure you have the `libasound2-dev` package installed.  
   Additionally, you need the [libmp3lame](https://www.rarewares.org/mp3-lame-libraries.php#libmp3lame) library.  
   On Mac OS, run `brew install lame`, provided you have [Homebrew](https://brew.sh/) installed.

3. Build

   ```bash
   cargo build --release
   ```

> [!NOTE]
> You need [this private SSH key](assets/free_librespot_private_key) to clone a dependency of DownOnSpot to use it with a free Spotify account.
> Follow [this answer by DopeGhoti on stackexchange.com](https://unix.stackexchange.com/a/494485) to set up SSH with the private key.
> A sample `~/.ssh/config` file could look like this:
>
> ```text
> Host github.com
>   IdentityFile ~/.ssh/free_librespot_private_key
> ```
>
> If you do not want to use `free-librespot` (i.e. if you are using a paid Spotify account), replace `git = "ssh://git@github.com/oSumAtrIX/free-librespot.git"` with `librespot = "0.4.2"` inside the `Cargo.toml` file.

## 🕹️ Usage

1. Create a [new application](https://developer.spotify.com/dashboard/applications) on the Spotify developer dashboard
2. Run DownOnSpot

   ```bash
   $ ./down_on_spot
   Settings could not be loaded because of the following error: IO: NotFound No such file or directory. (os error 2)...
   ..but default settings have been created successfully. Edit them and run the program again.
   ```

3. Edit the `settings.json` file

   The `settings.json` file is located in the following directories:

   - Windows: `C:\Users\<user>\AppData\Roaming\down_on_spot\settings.json`
   - Unix: `~/.config/down_on_spot/settings.json`

🎉 Now you can use DownOnSpot

   ```bash
   $ ./down_on_spot
   Usage:
   down_on_spot.exe <search_term> | <track_url> | <album_url> | <playlist_url> | <artist_url>
   ```

### ⚙️ Template variables

You can use the following template variables for `path` and `filename_template` in the `settings.json` file:

- %0disc%
- %0track%
- %album%
- %albumArtist%
- %albumArtists%
- %artist%
- %disc%
- %id%
- %title%
- %track%

###   Getting sp_dc for LRC downloads

If you enabled `download_lrc`, you must set set `lrc_sp_dc` to let DownOnSpot to fetch lyrics from Spotify.

See [this page](https://github.com/akashrchandran/syrics/wiki/Finding-sp_dc) to find out how you can obtain your `sp_dc`.


## 🧭 Additional scripts

- [Userscript to download titles from YouTube](https://gist.github.com/oSumAtrIX/6abf46e2ea25d32f4e6608c3c3cf837e)

## 🐞 Known issues

- Slow MP3 downloads due to libmp3lame
- Sporadic `channel error` when downloading tracks

## 💪 Contributors

<a href="https://github.com/osumatrix/downonspot/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=osumatrix/downonspot" />
</a>

## 🔑 License

DownOnSpot is licensed under the GPLv3 licence. Please see the [licence file](LICENSE) for more information.
[tl;dr](https://www.tldrlegal.com/license/gnu-general-public-license-v3-gpl-3) you may copy, distribute and modify DownOnSpot as long as you track changes/dates in source files.
Any modifications to DownOnSpot must also be made available under the GPL, along with build & install instructions.
