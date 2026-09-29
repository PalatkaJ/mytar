# Mytar

A small C implementation of a subset of the `tar` archive format. The project focuses on reading tar archives, listing their contents, and extracting regular files without external dependencies.

## What it does

This implementation understands the basic ustar-style tar header format and supports:

- listing archive members with `-t`
- extracting files with `-x`
- optional verbose output with `-v`
- handling regular files inside the archive
- basic validation for malformed or truncated archives

The entire program is contained in a single source file: `mytar.c`.

## Project structure

- `mytar.c` — core tar parser and archive logic
- `README.md` — project documentation

## Build

Compile the program with a standard C toolchain:

```bash
gcc -std=c11 -Wall -Wextra -O2 -o mytar mytar.c
```

## Usage

List the contents of an archive:

```bash
./mytar -t -f archive.tar
```

Extract an archive:

```bash
./mytar -x -f archive.tar
```

Extract with verbose output:

```bash
./mytar -x -v -f archive.tar
```

List only specific files from an archive:

```bash
./mytar -t -f archive.tar file1.txt file2.txt
```

## Notes

- The implementation is intentionally minimal and focused on the core tar behavior needed for archive listing and extraction.
- It validates a few common archive problems, including unexpected end-of-file conditions and unsupported header types.
- This project is designed to be simple to compile and easy to inspect in a single file.

## Example workflow

```bash
gcc -std=c11 -Wall -Wextra -O2 -o mytar mytar.c
tar -cf archive.tar file1.txt file2.txt
./mytar -t -f archive.tar
./mytar -x -f archive.tar
```

The first command creates the archive (using the official tar utility), the second lists files inside it, and the third extracts them back to the working directory.
