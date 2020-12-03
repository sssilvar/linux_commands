# Useful commands in Linux

## List all the processes runing on your machine
```bash
ps -ejH
```

Your output will look like:
```
    PID    PGID     SID TTY          TIME CMD
      2       0       0 ?        00:00:00 kthreadd
      3       0       0 ?        00:00:00   rcu_gp
      4       0       0 ?        00:00:00   rcu_par_gp
      6       0       0 ?        00:00:00   kworker/0:0H-kblockd
```

## Kill a group of processes under the same name
Let's say you want to kill all the python processes. To do so, just execute:

```bash
ps -ejH | grep python | awk '{print $1}' | xargs kill
```
replace `python` for the name of the process you want to kill.
