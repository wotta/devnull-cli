# devnull

A tiny CLI for posting to [/dev/null](https://dev-null.sh) without typing the `curl | bash` incantation every time. Drag images straight into your terminal, and HEIC photos and oversized screenshots get fixed up for you.

Unofficial; not affiliated with dev-null.sh. It wraps their own [`commit`](https://dev-null.sh/commit) script, so signing and uploading work exactly as they document.

## Install

```sh
curl -fsSL https://raw.githubusercontent.com/wotta/devnull-cli/main/devnull -o ~/.local/bin/devnull
chmod +x ~/.local/bin/devnull
```

Any directory on your `PATH` works instead of `~/.local/bin`.

Requires bash (the 3.2 that ships with macOS is fine). Image conversion and resizing use `sips`, which ships with macOS.

## Usage

```sh
devnull It was DNS.                     # plain commit (quotes optional)
devnull -r 0be0130 Agreed!              # reply to a commit
devnull ~/Desktop/shipped.png Shipped!  # attach images (up to 3)
devnull                                 # interactive: drop images, then type the message
```

- **Images:** any argument that is an existing `.png`, `.jpg`, `.jpeg`, `.webp`, `.heic` or `.heif` file is attached; everything else becomes the message. Type `devnull `, drag files into the terminal, then type your message.
- **Interactive mode:** run `devnull` on its own. It asks you to drop images (Enter to skip), then for the message.
- **HEIC/HEIF** is converted to JPEG.
- **Large images** are scaled down to 1600px on the longest side, since /dev/null rejects bigger ones. PNGs stay PNG; everything else becomes JPEG. Your original files are never touched.
- **Options:** `-r`/`--reply <hash or link>`, `-i`/`--image <path>`. Use `--` before a message that starts with `-`.

Quote messages that contain `?`, `*` or `!` followed by text, so your shell doesn't expand them.

## License

MIT
