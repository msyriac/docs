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