## Install
1. [install perf](https://askubuntu.com/questions/50145/how-to-install-perf-monitoring-tool)  
   > apt-get install linux-tools-common linux-tools-generic linux-tools-\`uname -r`
2. install FlameGraph
   > git clone https://github.com/brendangregg/FlameGraph

## Use
```bash
sudo time perf record -g -o perf_with_stack.data YOUR-APP
# or
perf record -F 99 -p 181 -g -- sleep 60
perf record -p ID1,ID2 sleep seconds

sudo perf script -f -i perf_with_stack.data | FlameGraph/stackcollapse-perf.pl | FlameGraph/flamegraph.pl > flamegraph.svg
# or
$ gunzip -c example-perf-stacks.txt.gz | ./stackcollapse-perf.pl --all | ./flamegraph.pl --color=java --hash > example-perf.svg
```

## Others
### Common perf commands
- `perf stat`
This command provides overall statistics for common performance events, including instructions executed and clock cycles consumed. Options allow for selection of events other than the default measurement events.
- `perf record`
This command records performance data into a file, perf.data, which can be later analyzed using the perf report command.
- `perf report`
This command reads and displays the performance data from the perf.data file created by perf record.
- `perf list`
This command lists the events available on a particular machine. These events will vary based on performance monitoring hardware and software configuration of the system.
- `perf top`
This command performs a similar function to the top utility. It generates and displays a performance counter profile in realtime.
- `perf trace`
This command performs a similar function to the strace tool. It monitors the system calls used by a specified thread or process and all signals received by that application.
- `perf help`
This command displays a complete list of perf commands.

### websites
[offical website](https://www.brendangregg.com/flamegraphs.html)  
[flamegraphs usage](https://gitlab.com/gitlab-com/runbooks/-/blob/v2.220.2/docs/tutorials/how_to_use_flamegraphs_for_perf_profiling.md)