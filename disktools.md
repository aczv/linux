
## ncdu

```bash

sudo apt install ncdu

# Should give a clean read on biggest dirs/files ONLY on root area drive. (-r =
# read-only, -x = stay on same filesystem (meaning: do not traverse other
# filesystem mounts))
sudo ncdu -rx

```

## du

```bash

du -xhst10M *|sort -h

```
