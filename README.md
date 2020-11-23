<h1 align="center">
  <br>
  <a href="https://webtorrent.io"><img src="https://webtorrent.io/img/WebTorrent.png" alt="WebTorrent" width="200"></a>
  <br>
  WebTorrent CLI
  <br>
  <br>
</h1>

<h4 align="center">The streaming torrent client. For the command line.</h4>

<p align="center">
    <a href="https://travis-ci.org/webtorrent/webtorrent-cli"><img src="https://img.shields.io/travis/webtorrent/webtorrent-cli/master.svg" alt="travis"></a>
    <a href="https://npmjs.com/package/webtorrent-cli"><img src="https://img.shields.io/npm/v/webtorrent-cli.svg" alt="npm version"></a>
    <a href="https://npmjs.org/package/webtorrent-cli"><img src="https://img.shields.io/npm/dm/webtorrent-cli.svg" alt="npm downloads"></a>
    <a href="https://standardjs.com"><img src="https://img.shields.io/badge/code_style-standard-brightgreen.svg" alt="javascript style guide"></a>
</p>
<br>

**WebTorrent** is the first BitTorrent client that works in the **browser**, but `webtorrent-cli`,
i.e. *THIS PACKAGE*, is for using WebTorrent from the **command line**.

`webtorrent-cli` is a simple torrent client for use in node.js, as a command line app. It
uses TCP and UDP to talk to other torrent clients.

**NOTE**: To connect to "web peers" (browsers) in addition to normal BitTorrent peers, use
[`webtorrent-hybrid`](https://www.npmjs.com/package/webtorrent-hybrid) which includes WebRTC
support for node.

To use WebTorrent in the browser, see [`webtorrent`](https://www.npmjs.com/package/webtorrent).

### Features

- **Use [WebTorrent](https://webtorrent.io) from the command line!**
- **Insanely fast**
- **Pure Javascript** (no native dependencies)
- Streaming
  - Stream to **AirPlay**, **Chromecast**, **VLC player**, **IINA**, and many other devices/players
  - Fetches pieces from the network on-demand so seeking is supported (even before torrent is finished)
  - Seamlessly switches between sequential and rarest-first piece selection strategy
- Supports advanced torrent client features
  - **magnet uri** support via **[ut_metadata](https://www.npmjs.com/package/ut_metadata)**
  - **peer discovery** via **[dht](https://www.npmjs.com/package/bittorrent-dht)**,
    **[tracker](https://www.npmjs.com/package/bittorrent-tracker)**, and
    **[ut_pex](https://www.npmjs.com/package/ut_pex)**
  - **[protocol extension api](https://www.npmjs.com/package/bittorrent-protocol#extension-api)**
    for adding new extensions

### Install

To install a `webtorrent` command line program, run:

```bash
npm install webtorrent-cli -g
```

### Usage

```bash
$ webtorrent --help
               _     _                            _
 __      _____| |__ | |_ ___  _ __ _ __ ___ _ __ | |_
 \ \ /\ / / _ \ '_ \| __/ _ \| '__| '__/ _ \ '_ \| __|
  \ V  V /  __/ |_) | || (_) | |  | | |  __/ | | | |_
   \_/\_/ \___|_.__/ \__\___/|_|  |_|  \___|_| |_|\__|

Usage:
  webtorrent [command] <torrent-id> [options]

Examples:
  webtorrent download "magnet:..." --vlc
  webtorrent "magnet:..." --vlc --player-args="--video-on-top --repeat"

Specify <torrent-id> as one of:
  * magnet uri
  * http url to .torrent file
  * filesystem path to .torrent file
  * info hash (hex string)

Commands:
  webtorrent download <torrent-ids...>      Download a torrent
  webtorrent downloadmeta <torrent-ids...>  Download metadata of torrent
  webtorrent seed <inputs...>               Seed a file or a folder
  webtorrent create <input>                 Create a .torrent file
  webtorrent info <torrent-id>              Show info for .torrent file or
                                            magner uri
  webtorrent version                        Show version information
  webtorrent help                           Show help information

Options (streaming):
      --airplay     Apple TV
      --chromecast  Google Chromecast                             [default: all]
      --dlna        DNLA
      --mplayer     MPlayer
      --mpv         MPV
      --omx         OMX                                          [default: hdmi]
      --vlc         VLC
      --iina        IINA
      --xbmc        XBMC
      --stdout      Standard out (implies --quiet)

Options (simple):
  -o, --out        Set download destination         [default: current directory]
  -s, --select     Select specific file in torrent                      [number]
  -t, --subtitles  Load subtitles file                                  [string]
  -h, --help       Show help information                               [boolean]
  -v, --version    Show version information                            [boolean]

Options (advanced)
  -p, --port          Change the http server port                [default: 8000]
  -b, --blocklist     Load blocklist file/url                           [string]
  -a, --announce      Tracker URL to announce to                        [string]
  -q, --quiet         Don't show UI on stdout
      --pip           Enter Picture-in-Picture if supported by the player
      --verbose       Show torrent protocol details
      --player-args   Add player specific arguments (see example)       [string]
      --torrent-port  Change the torrent seeding port          [default: random]
      --dht-port      Change the dht port                      [default: random]
      --not-on-top    Don't set "always on top" option in player
      --keep-seeding  Don't quit when done downloading
      --no-quit       Don't quit when player exits
      --on-done       Run script after torrent download is done
      --on-exit       Run script before program exit
```

To download a torrent:

```bash
$ webtorrent magnet_uri
```

To stream a torrent to a device like **AirPlay** or **Chromecast**, just pass a flag:

```bash
$ webtorrent magnet_uri --airplay
```

In addition to magnet uris, webtorrent supports many ways to specify a torrent:

- magnet uri (string)
- torrent file (buffer)
- info hash (hex string or buffer)
- parsed torrent (from [parse-torrent](https://www.npmjs.com/package/parse-torrent))
- http/https url to a torrent file (string)
- filesystem path to a torrent file (string)

### License

MIT. Copyright (c) [Feross Aboukhadijeh](https://feross.org) and [WebTorrent, LLC](https://webtorrent.io).
