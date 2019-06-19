# Merge and split PDF files

Download and install:

- pdftk
- pdfjam

### Replace spaces to underscores in all files and directories

```bash
find input -type d | rename 's/\s+/_/g'
find input -type f | rename 's/\s+/_/g'
```

### Get a sorted list of all PDF files

```bash
find input -name "*.pdf" | sort > all.txt
```

### Resize multiple files to `A4`

```bash
for i in $(cat all.txt); do pdfjam $i --a4paper --outfile good/$i; done
for i in *.pdf; do pdfjam $i --a4paper --outfile out/$i; done
```

### Merge all PDF files listed in `all.txt` into one

```bash
pdftk $(cat all.txt) output foobar.pdf
```

### Shrink PDF

```bash
gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/ebook -dNOPAUSE -dQUIET -dBATCH -sOutputFile=output-ebook.pdf input.pdf
```
