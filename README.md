# scout-seeker

![Banner with large array and scout-seeker title](https://raw.githubusercontent.com/ewilan-riviere/scout-seeker/main/docs/banner.jpg)

[![rust][rust-version-src]][rust-version-href]
[![tests][tests-src]][tests-href]

<!-- [![codecov][codecov-src]][codecov-href] -->

scout-seeker is a simple [Rust](https://www.rust-lang.org/) CLI to scan a directory to list files, recursively.

## Installation

You can install `scout-seeker` with [Cargo](https://doc.rust-lang.org/cargo/).

```bash
cargo install scout-seeker
```

## Usage

You have to pass the directory to scan as an argument.

Optional arguments:

- `-o` or `--output`: to specify the output file, by default it will be `./output.json`.
- `-v` or `--verbose`: to display more information in the terminal.
- `-p` or `--print`: to print the output in the terminal (this will disable the output file and verbose).

```bash
scout-seeker /path/to/directory -o=/path/to/output.json -v
```

You will have an output, like this:

```bash
Directory: /path/to/directory
Date: "2024-04-28 10:07:12.081879 +02:00"
Time in seconds: 3.123456
Total files: 1234
Output file: /path/to/output.json
```

And an output file, like this:

```json
{
  "path": "/path/to/directory",
  "date": "2024-04-28 10:07:12.081879 +02:00",
  "time_seconds": "3.123456",
  "total_files": 1234,
  "files": ["/path/to/directory/file1.txt", "/path/to/directory/file2.txt"]
}
```

#### Print

If you want to print the output in the terminal, you can use the `-p` or `--print` argument.

```bash
scout-seeker /path/to/directory -p
```

You will have an output, like this:

```bash
tests/data/file-3.md
tests/data/file-2.md
tests/data/file.jpg
tests/data/file.mkv
tests/data/file-1.md
tests/data/nested/file-nested-2.md
tests/data/nested/file-nested-1.md
```

### Files excluded

- Files with dots at the beginning of their names, like `.gitignore`.
- Files into directories with dots at the beginning of their names, like `.git/HEAD`.

## Build

Clone repository:

```bash
git clone https://github.com/ewilan-riviere/scout-seeker.git
cd scout-seeker
```

To build, you have to install [Rust](https://www.rust-lang.org/), you can follow [this guide](https://gist.github.com/ewilan-riviere/6a0b8aab2e347164e73feab83c862e99).

```bash
cargo build
```

```bash
cargo run /path/to/directory
```

## Release

Build the release version:

```bash
cargo build --release
```

Put the binary in your path:

```bash
cp target/release/scout-seeker /usr/local/bin
```

## Tests

To run the tests.

```bash
cargo test
```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

[rust-version-src]: https://img.shields.io/badge/Rust-v1.77.2-000000?colorA=18181B&logo=Rust&logoColor=ffffff
[rust-version-href]: https://www.rust-lang.org/
[tests-src]: https://img.shields.io/github/actions/workflow/status/ewilan-riviere/scout-seeker/run-tests.yml?branch=main&label=tests&style=flat&colorA=18181B
[tests-href]: https://github.com/ewilan-riviere/scout-seeker/actions
[codecov-src]: https://img.shields.io/codecov/c/gh/ewilan-riviere/scout-seeker/main?style=flat&colorA=18181B&colorB=777BB4
[codecov-href]: https://codecov.io/gh/ewilan-riviere/scout-seeker
