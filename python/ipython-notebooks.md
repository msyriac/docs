# IPython notebooks

I've been hesitant to use notebooks for a while but I've
come around to them since they can save a lot of time for tasks
where one of the operations in your script takes a lot more time
than others. I'm now trying to generally split my code into

1. libraries in importable modules
2. deployment scripts to run integration tests (usually over MPI)
3. experimentation scripts

where the experimentation scripts are more frequently IPython
notebooks. This has the advantage that I can generate useful
tutorials with little effort.

## Running an IPython notebook over SSH

IPython can be started on a remote system without a browser.
You should specify a port of your choice.

```bash
ipython notebook --no-browser --port=8889
```

Next, on your local system, create an SSH tunnel to the remote
system but forward a chosen local port to the chosen remote port.

```bash
ssh -N -L localhost:8887:localhost:8889 msyriac@astro
```

Keep this connection alive by not closing the terminal, or use
the `-f` option to send it to the background.

Finally, in a browser on your local system, open a connection
to the chosen local port.

```
localhost:8887
```

## Auto-reload

IPython magic to auto-reload modules as you work on them

```python
%load_ext autoreload
%autoreload 2
```

## Keyboard shortcuts

|Shortcut	|Action                  |
| ------------- |:----------------------:|
|Shift-Enter	|run cell|
|Ctrl-Enter	|run cell in-place|
|Alt-Enter	|run cell, insert below|
|Ctrl-m x	|cut cell|
|Ctrl-m c	|copy cell|
|Ctrl-m v	|paste cell|
|Ctrl-m d	|delete cell|
|Ctrl-m z	|undo last cell deletion|
|Ctrl-m –	|split cell|
|Ctrl-m a	|insert cell above|
|Ctrl-m b	|insert cell below|
|Ctrl-m o	|toggle output|
|Ctrl-m O	|toggle output scroll|
|Ctrl-m l	|toggle line numbers|
|Ctrl-m s	|save notebook|
|Ctrl-m j	|move cell down|
|Ctrl-m k	|move cell up|
|Ctrl-m y	|code cell|
|Ctrl-m m	|markdown cell|
|Ctrl-m t	|raw cell|
|Ctrl-m 1-6	|heading 1-6 cell|
|Ctrl-m p	|select previous|
|Ctrl-m n	|select next|
|Ctrl-m i	|interrupt kernel|
|Ctrl-m .	|restart kernel|
|Ctrl-m h	|show keyboard shortcuts|

## Emacs

I've now stopped running notebooks in the browser since one can do it entirely within emacs using the `ein` package installable from MELPA. The steps involved are:

1. start an ipython notebook server: ``ipython notebook``
2. get the name of the port and copy the token
3. In emacs, M-x ein:notebooklist-login once with port and token
4. Then M-x ein:notebooklist-open with port to open the notebook landing page

