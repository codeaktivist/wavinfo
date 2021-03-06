# wavinfo - analyse audio files
**A ultra fast and simple command line tool to analyse WAVE audio files written in C.**

## Scope of the program
This command line tool performs an in depth analysis for a provided audio wav file. The information in the file header (metadata) is presented to the user and interpreted.

## Usage

### Compilation
Just compile from source, no additional resources (other than standard header files) required:
'clang wavinfo.c -o wavinfo'

### Execution
To use the compiled executable binary, following command line prompt must be used:
'./wav-audio-worker youraudiofile.wav'

### Suported Files
Only uncompressed wave files are supported, meaning linear PCM files in a wav-container:
- yourfile.wav
- yourfile.wave
- yourfile.bwf (**b**roadcast **w**ave **f**ile)

## Background

What's under the hood and what specs are used:

[WAVE Header Reference](http://www-mmsp.ece.mcgill.ca/Documents/AudioFormats/WAVE/Docs/riffmci.pdf)

[Broadcast WAVE Header Reference](https://tech.ebu.ch/docs/tech/tech3285.pdf)

[Information on Chunks](https://www2.ak.tu-berlin.de/~fhein/Alias/Studio/ProTools/audio-formate/wav/overview.html)

### Analyzing the header info and metadata

To make sense of the 0s and 1s in audio data, you need to know how many channels there are and what the bit depth and sample rate are. This information is provided in the file header.

## Supported chunks

### Mandatory chunks

- ftm - Format Chunk
- data - Audio Data Chunk
... chunks must appear in this order

### ProTools specific chunks

- minf
- elmo
- (data)
- regn
- ovwf
- umid
... files created by ProTools will follow this order

### Optional chunks

PAD - PAD chunk, fill with NUL (legacy)
CUE - CUE chunk, defining markers and loops
PLST - Playlist chunk
ADTL - Associated Data List Chunk, contains text for cue points
