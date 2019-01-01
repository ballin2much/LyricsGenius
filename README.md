# LyricsGenius: a Python client for the Genius.com API
[![Build Status](https://travis-ci.org/johnwmillr/LyricsGenius.svg?branch=master)](https://travis-ci.org/johnwmillr/LyricsGenius)
[![PyPI version](https://badge.fury.io/py/lyricsgenius.svg)](https://pypi.org/project/lyricsgenius/)
[![Python version](https://img.shields.io/badge/python-3.x-brightgreen.svg)](https://pypi.org/project/lyricsgenius/)

`lyricsgenius` provides a simple interface to the song, artist, and lyrics data stored on [Genius.com](https://www.genius.com).

## Setup
Before using this package you'll need to sign up for a (free) account that authorizes access to [the Genius API](http://genius.com/api-clients). The Genius account provides a `client_access_token` that is required by the package. See the [Usage section](https://github.com/johnwmillr/LyricsGenius#usage) below for examples.

## Installation
`lyricsgenius` requires Python 3.

Install the package via [PyPI](https://pypi.python.org/pypi/lyricsgenius) using `pip`:

```bash
pip install lyricsgenius
```

Or, install the latest version from GitHub:

```bash
pip install git+https://github.com/johnwmillr/LyricsGenius.git
```

## Usage
Import the package and search for songs by a given artist:

```python
import lyricsgenius as genius
api = genius.Genius("my_client_access_token_here")
artist = api.search_artist("Andy Shauf", max_songs=3)
print(artist.songs)
```

Search for a single song by the same artist:

```python
song = api.search_song("To You", artist.name)
print(song.lyrics)
```

Add the song to the artist object:

```python
artist.add_song(song)
```

Save the artist's songs to a JSON file:

```python
artist.save_lyrics()
```

You can also call the package from the command line:

```bash
export GENIUS_CLIENT_ACCESS_TOKEN="my_client_access_token_here"
python3 -m lyricsgenius --help
```

Search for and save lyrics to a given song:

```bash
python3 -m lyricsgenius song "Begin Again" "Andy Shauf" --save
```

Search for five songs by 'The Beatles' and save the lyrics:

```bash
python3 -m lyricsgenius artist "The Beatles" --max-songs 5 --save
```

## Example projects

  - [Trucks and Beer: A textual analysis of popular country music](http://www.johnwmillr.com/trucks-and-beer/)
  - [What makes some blink-182 songs more popular than others?](http://jdaytn.com/posts/download-blink-182-data/)
  - [Sentiment analysis on hip-hop lyrics](https://github.com/Hugo-Nattagh/2017-Hip-Hop)
  - [Does Country Music Drink More Than Other Genres?](https://towardsdatascience.com/does-country-music-drink-more-than-other-genres-a21db901940b)
  - [49 Years of Lyrics: Why So Angry?](https://towardsdatascience.com/49-years-of-lyrics-why-so-angry-1adf0a3fa2b4)

## Contributing
Please contribute! If you want to fix a bug, suggest improvements, or add new features to the project, just [open an issue](https://github.com/johnwmillr/LyricsGenius/issues) or send me a pull request.
