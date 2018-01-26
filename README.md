This repository is a Binder specification that lets you use Quilt packages easily in a hosted environment.

Quilt is a data package manager. Visit us at [our homepage](http://quiltdata.com)

Click this badge to try it out! [![Binder](https://mybinder.org/badge.svg)](https://mybinder.org/v2/gh/quiltdata/data2binder/master?filepath=index.ipynb)

To use quilt.yml in your own Binder repository, follow these steps.

1. Put `quilt` in your requirements.txt

2. Use `quilt.yml` to specify the data packages your Binder depends on.

3. Add
``` bash
#!/bin/bash
quilt install
```
to your postBuild script. (Make sure it's executable, `chmod +x postBuild` on UNIX-like systems, `git update-index --chmod=+x postBuild` for Windows.)
