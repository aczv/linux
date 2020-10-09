# Merge and split PDF files

## Install pdftk

```bash
sudo apt-get install pdftk
```

## File operations

```bash
# Replace spaces to underscores in all files and directories
find input -type d | rename 's/\s+/_/g'
find input -type f | rename 's/\s+/_/g'

# Get a sorted list of all PDF files
find input -name "*.pdf" | sort > all.txt
```

## pdftk

```bash

# Merge all PDF files listed in `all.txt` into one
pdftk $(cat all.txt) output foobar.pdf

# Extract certain pages
pdftk File0162.PDF cat 1-2 output out1.pdf

# Pakeiti viena lapa vidury
pdftk paraiska.PDF cat 1-2 output 12.pdf
pdftk paraiska.PDF cat 4-31 output 4.pdf
pdftk 12.pdf trecias.PDF 4.pdf output naujas.pdf

```

## pdfjam

```bash

# Resize multiple files to `A4`
for i in $(cat all.txt); do pdfjam $i --a4paper --outfile good/$i; done
for i in *.pdf; do pdfjam $i --a4paper --outfile out/$i; done

```

## gs

```bash

# Shrink PDF file
gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/ebook \
    -dNOPAUSE -dQUIET -dBATCH -sOutputFile=output-ebook.pdf input.pdf

```
