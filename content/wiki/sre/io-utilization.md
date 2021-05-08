---
title: Find out what's the IO utilization
categories:
- til
---

# Find out what's the IO utilization

```sh
iostat -xyz 1 100
```

This will give an output like that:

```
Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await r_await w_await  svctm  %util
sda               0.00     0.00    0.00  373.00     0.00 38416.00   205.98   150.96  236.06    0.00  236.06   2.68 100.00
dm-1              0.00     0.00    0.00  523.00     0.00 67416.00   257.80   152.00  169.23    0.00  169.23   1.91 100.10
```


You want to look into `%util` for utilization.

You can the follow up with one of the below to identify the offending processes:
```sh
iotop
```
or
```sh
while true; do date; ps aux | awk '{if($8=="D") print $0;}'; sleep 1; done
```
