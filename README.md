# WAV Audio Volume Adjuster

This project is a command-line C program that adjusts the volume of a WAV audio file. It reads an input WAV file, multiplies each audio sample by a user-specified factor to increase or decrease the volume, and writes the result to a new output WAV file. The program preserves the original file's header to maintain the correct WAV format.

## Features

- Reads and writes standard 16-bit PCM WAV files.
- Copies the WAV file header to ensure the output file is valid.
- Multiplies each audio sample by a floating-point factor to adjust volume.
- Handles command-line arguments for input file, output file, and volume factor.
- Performs error checking for file operations and argument validity.

## How It Works

1. **Header Copying:**  
   The program reads the first 44 bytes (the standard WAV header) from the input file and writes them unchanged to the output file.

2. **Sample Processing:**  
   Each audio sample (16-bit signed integer) is read, multiplied by the specified factor, and written to the output file. This increases or decreases the volume accordingly.

3. **Command-Line Usage:**  
   The program is run from the command line with three arguments: the input WAV file, the output WAV file, and the volume adjustment factor.

## Usage

```sh
gcc -o volume volume.c
./volume input.wav output.wav 1.5
```

- `input.wav`: Path to the original WAV file.
- `output.wav`: Path where the adjusted WAV file will be saved.
- `1.5`: Volume factor (greater than 1.0 increases volume, between 0 and 1.0 decreases volume).

## Example

To double the volume:
```sh
./volume input.wav output.wav 2.0
```

To halve the volume:
```sh
./volume input.wav output.wav 0.5
```

## File Structure

- `volume.c` — Main C source file containing all logic for reading, processing, and writing WAV files.

## Notes

- Only works with 16-bit PCM WAV files.
- The program does not perform clipping, so very large factors may cause audio distortion if samples exceed the 16-bit range.
- Ensure the input file exists and is a valid WAV file before running the program.

---

This project is a practical introduction to file I/O, binary data manipulation, and audio
