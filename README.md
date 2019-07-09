# Run this example
[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/quiltdata/data2binder/master?filepath=index.ipynb)

# Pull data into Binder notebooks
This example uses [Quilt](http://quiltdata.com) to inject data packages into a Jupyter notebook.

Data packages are versioned, immutable snapshots of data. Data packages may contain data of any size. Here is an example of data package: [uciml/iris](https://quiltdata.com/package/uciml/iris).

# How to specify data dependencies in your own Binder

1. Add `quilt` to `requirements.txt`

2. Specify data package dependencies in `quilt.yml` ([docs](https://docs.quiltdata.com/api/api-cli)). For example:

```
packages:
  - vgauthier/DynamicPopEstimate   # get the latest version
  - danWebster/sgRNAs:a972d92      # get a specific hash (short hash)
  - akarve/sales:tag:latest        # get a specific tag
  - asah/snli:v:1.0                # get a specific version
```

3. Include the following lines at the top of `postBuild`. (`postBuild` should be executable: `chmod +x postBuild` on UNIX, `git update-index --chmod=+x postBuild` for Windows).
``` bash
#!/bin/bash
quilt install
```
If you are adopting the `binder` folder pattern for your `repo2docker` configuration files, and including `quilt.yml`, your `postBuild` file should look like this:

```bash
#!/bin/bash
quilt install @./binder/quilt.yml
```

    
Now you can access the package data in your Jupyter notebooks:
```
In [1]: from quilt.data.akarve import sales
In [2]: sales.transactions()
Out[2]: 
      Row ID  Order ID Order Date Order Priority  Order Quantity       Sales  \
0          1         3 2010-10-13            Low               6    261.5400   
1         49       293 2012-10-01           High              49  10123.0200   
2         50       293 2012-10-01           High              27    244.5700   
...
```
    
# Developer
* [Quilt repository](https://github.com/quiltdata/quilt)
* [Quilt docs](https://docs.quiltdata.com)
