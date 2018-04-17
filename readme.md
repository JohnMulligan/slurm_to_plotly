Pipeline for monitoring resource usage and speed on mpi4py jobs.

Memory: This function is multipurpose: to clean up old memory blocks (to the extent that this is possible inside mpi4py) and, optionally, to give you feedback on that process's memory usage.

```python
def checkmem(id,verbose=0):
	proc = psutil.Process(os.getpid())
	mem = proc.memory_info()
	gc.collect()
	if verbose==1:
		print "proc: %s time: %s mem: %s" %(str(id),str(time.time()), mem)
		return mem.rss
```

Speed: The below is just to give you the right format for your step time in a format readable by slurm_to_plotly.py

```python
t=time.time()
while True:
	print rank, time.time()-t, time.time()
	t=time.time()
```