# Markdown → PDF

Setting up a command line utility for converting markdown(with custom css) to pdf.

### Requirements

Install these from the command line.

- `pandoc`

  ```bash
  sudo apt install pandoc
  ```

- `wkhtmltopdf`

  ```bash
  sudo apt install wkhtmltopdf
  ```

### Setup

Copy this into `~/.bash_aliases`

```bash
mdtopdf() {
     filename="${1%.*}"
     pandoc -t html $filename.md -o $filename.pdf
}
```

OR

Copy this instead if you want to use custom css

```bash
mdtopdf() {
     filename="${1%.*}"
     pandoc -t html --css /path/to/custom.css $filename.md -o $filename.pdf
}
```

replace `/path/to/custom.css` with the path of your css file.

### Usage

```bash
$ mdtopdf sample.md
```

```bash
[WARNING] This document format requires a nonempty <title> element.
  Please specify either 'title' or 'pagetitle' in the metadata,
  e.g. by using --metadata pagetitle="..." on the command line.
  Falling back to 'sample'
Loading page (1/2)
Printing pages (2/2)                                               
Done
```

Ignore the warning.

You'll find the output pdf in the same folder as the markdown file. 