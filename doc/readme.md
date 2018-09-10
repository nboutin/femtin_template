Generated documentation shall be put here.
One folder for html.
One folder for latex.
and so on...

# Generate Doxygen documentation outside Yocto

```sh
devtool modify <recipe>
cd workspace/sources/<recipe>/<root_project>
mkdir build
cd build
cmake ../doc
make doc
```

Open <root_project>/doc/html/index.html