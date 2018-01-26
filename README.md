[![Binder](https://mybinder.org/badge.svg)](https://mybinder.org/v2/gh/quiltdata/data2binder/master?filepath=index.ipynb)

# Pull data into Binder notebooks
This example uses [Quilt](http://quiltdata.com) to inject versioned data packages into a Jupyter notebook.

# How to specify data dependencies in your own Binder

1. Add `quilt` to `requirements.txt`
2. Specify data package dependencies in [`quilt.yml`](https://docs.quiltdata.com/cli.html)
3. Include the following in `postBuild`:
``` bash
#!/bin/bash
quilt install
```
4. Ensure that `postBuild` is executable:
    * `chmod +x postBuild` on UNIX-like systems
    * `git update-index --chmod=+x postBuild` for Windows.
    
# Developer
* [Quilt repository](https://github.com/quiltdata/quilt)
* [Quilt docs](https://docs.quiltdata.com)
