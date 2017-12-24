# Plotting


## Speed up saved plots

When saving plots to disk, you will want to make sure that the backend used is `Agg`. Otherwise, the plots can take a lot of time to be saved. To set the backend globally, first find your `matplotlibrc` file by doing the following:


```
python
import matplotlib
matplotlib.matplotlib_fname()
```

This will display the location of your currently used matplotlibrc file. Copy this file to `$HOME/.config/matplotlib/matplotlibrc` (matplotlibrc being a file not a directory) and ensure that `backend` is set as follows there:

```
backend    :   Agg
```