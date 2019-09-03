

```bash
# Resize photos
for file in IMG_201907*.jpg; do convert $file -resize "1280>" 1280/$file; done
```
