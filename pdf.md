

```bash
for i in *.pdf; do pdfjam $i --a4paper --outfile out/$i; done
pdftk a04*.pdf output ../final/all_04.pdf
```

