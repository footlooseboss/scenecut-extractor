# Scenecut Extractor

[![PyPI version](https://img.shields.io/pypi/v/scenecut-extractor.svg)](https://pypi.org/project/scenecut-extractor)

Extract scenecuts from video files using ffmpeg.

This tool uses the [`select` filter](http://ffmpeg.org/ffmpeg-filters.html#select_002c-aselect) from ffmpeg to determine the scene cut probability of adjacent frames, and allows users to determine which frames (or at which timestamps) the scene cuts happen.

Author: Werner Robitza <werner.robitza@gmail.com>

# Requirements

- Python 3.7 or higher
- FFmpeg:
    - download a static build from [their website](http://ffmpeg.org/download.html))
    - put the `ffmpeg` executable in your `$PATH`

# Installation

```bash
pip3 install --user scenecut_extractor
```

Or clone this repository, then run the tool with `python3 -m scenecut_extractor`.

# Usage

Run:

```bash
scenecut-extractor <input-file>
```

This might take a while depending on the length of your input file, and then output a list of scene cuts in JSON format:

```json
[
  {
    "frame": 114,
    "pts": 114.0,
    "pts_time": 3.8,
    "score": 0.445904
  },
  {
    "frame": 159,
    "pts": 159.0,
    "pts_time": 5.3,
    "score": 0.440126
  }
]
```

# Extended Usage

The command supports the following arguments and options, see `scenecut-extractor -h`:

```
usage: scenecut-extractor [-h] [-t THRESHOLD] [-o {all,frames,seconds}]
                          [-of {json,csv}] [-p] [-v]
                          input

scenecut_extractor v0.3.3

positional arguments:
  input                 input file

optional arguments:
  -h, --help            show this help message and exit
  -t THRESHOLD, --threshold THRESHOLD
                        threshold (between 0 and 1) (default: 0.3)
  -o {all,frames,seconds}, --output {all,frames,seconds}
                        output what (default: all)
  -of {json,csv}, --output-format {json,csv}
                        output in which format (default: json)
  -p, --progress        Show a progress bar on stderr (default: False)
  -v, --verbose         Print verbose info to stderr (default: False)
```

You can use the `-t` parameter to set the threshold that ffmpeg internally uses (between 0 and 1) – if you set it to 0, all frames will be printed with their probabilities.

# Alternatives

For extended scene detection features such as automatic splitting or perceptual hashing, you may want to check out [PySceneDetect](https://pyscenedetect.readthedocs.io/en/latest/).

# License

scenecut_extractor, Copyright (c) 2018–2022 Werner Robitza

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
