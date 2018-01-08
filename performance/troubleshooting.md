# Mermory
## Vitural Memory Diagnostic
### Case 1: Jvm crash because of virtural Memory
```
# Native memory allocation (mmap) failed to map 12288 bytes for committing reserved memory.
```

CheckPoint
* Check max_map_count
* Check limits
* Check vm.overcommit(default is 0)

```
sysctl -a | egrep "vm.min_free|vm.overcommit"
cat /proc/<PID>/limits
cat /proc/sys/vm/max_map_count 
cat /proc/sys/vm/min_free_kbytes

You can count number of mmap handles process is using with this command: sudo cat /proc/$PID/maps | wc -l

```
https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/performance_tuning_guide/s-memory-captun


