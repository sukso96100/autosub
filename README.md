# Autosub <a href="https://pypi.python.org/pypi/autosub"><img src="https://img.shields.io/pypi/v/autosub.svg"></img></a>
  
### Auto-generated subtitles for any video

Autosub is a utility for automatic speech recognition and subtitle generation. It takes a video or an audio file as input, performs voice activity detection to find speech regions, makes parallel requests to Google Web Speech API to generate transcriptions for those regions, (optionally) translates them to a different language, and finally saves the resulting subtitles to disk. It supports a variety of input and output languages (to see which, run the utility with the argument `--list-languages`) and can currently produce subtitles in either the [SRT format](https://en.wikipedia.org/wiki/SubRip) or simple [JSON](https://en.wikipedia.org/wiki/JSON).

### Installation

1. Install [ffmpeg](https://www.ffmpeg.org/).
2. Run `pip install git+https://github.com/sukso96100/autosub`.

### Usage
Set `GOOGLE_APPLICATION_CREDENTIAL` environment variable
```
export GOOGLE_APPLICATION_CREDENTIAL=./credential.json
```

```
$ autosub -h
usage: autosub [-h] [-C CONCURRENCY] [-o OUTPUT] [-F FORMAT] [-S SRC_LANGUAGE] [-D DST_LANGUAGE] [-P PROJECT_ID]
               [-L LOCATION] [-M MODEL] [--list-formats] [--list-languages]
               [source_path]

positional arguments:
  source_path           Path to the video or audio file to subtitle

optional arguments:
  -h, --help            show this help message and exit
  -C CONCURRENCY, --concurrency CONCURRENCY
                        Number of concurrent API requests to make
  -o OUTPUT, --output OUTPUT
                        Output path for subtitles (by default, subtitles are saved in the same directory and name as
                        the source path)
  -F FORMAT, --format FORMAT
                        Destination subtitle format
  -S SRC_LANGUAGE, --src-language SRC_LANGUAGE
                        Language spoken in source file
  -D DST_LANGUAGE, --dst-language DST_LANGUAGE
                        Desired language for the subtitles
  -P PROJECT_ID, --project-id PROJECT_ID
                        Your Google Cloud Project ID
  -L LOCATION, --location LOCATION
                        Google Cloud region id(e.g. us-central1)
  -M MODEL, --model MODEL
                        Speech regocnition model(default, video, phone_call, command_and_search
  --list-formats        List all available subtitle formats
  --list-languages      List all available source/destination languages
```
Command example
```
autosub -F srt -S en -D ko -P my-gcp-project -L us-central1 -M default video.mp4
```

### License

MIT
