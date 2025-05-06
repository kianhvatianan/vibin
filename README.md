# vibin

`vibin` is a simple and lightweight command-line music player built using the D programming language. It supports playing individual music files or full playlists (folders of music files) in the background. Additional commands allow users to check playback status and stop the music anytime.

## Features

* Play a single music file in the background
* Play all music files from a folder as a playlist in the background
* Check the current playback status (mode and file)
* Stop playback and terminate all background processes

## Usage

### Play a Single Song

Plays a single `.mp3` file in the background.

```bash
vibin only music_name.mp3
```

### Play All Songs in a Folder

Plays all `.mp3` files inside a folder in order, in the background.

```bash
vibin all playlist_folder/
```

### Check Playback Status

Displays the current playback mode (`only` or `all`) and the name of the song currently playing. Also indicates whether playback is active.

```bash
vibin status
```

### Stop Playback

Stops all music playback and terminates any background player process. Also clears the current status.

```bash
vibin stop
```

## How It Works

* The player runs in the background using system processes.
* Playback information (mode, file name, and PID) is stored in a runtime status file: `~/.vibin_status`.
* The `status` command reads this file to display playback information.
* The `stop` command reads the process ID from the status file and terminates the player.

## Dependencies

* `ffmpeg`, `mpg123`, or another terminal-based audio player must be installed on the system.
* Compatible with Linux systems (tested on Ubuntu).

## Status File Format (`~/.vibin_status`)

This file stores the current player state:

```json
{
  "mode": "only",
  "file": "music_name.mp3",
  "pid": 12345
}
```

Enjoy.

