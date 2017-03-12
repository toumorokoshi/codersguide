# High CPU Load Average / Run Queue Length

Load average is defined as the the number of processes that are
ready to be executed, over the number of cpus available:

    load_average = processes_ready / cpus_available

In an ideal world, you would observe a load average of 1: the system
has exactly enough processing power to execute all processes on it.

A load average greater than 1 means there is work waiting to be
executed. This will result in an increase in latency: processes will
respond or execute work more slowly than if they were on a less taxed
system.

Load average can be observed using `top`

## With low CPU usage

(needs verification): load average is always greater than the total cpu utilization:

    load_average >= average_cpu_usage_percent / 100

If all cpus are utilized at all times (100%), then there is always 1 process executing
per CPU, and thus load average is 1.

If the load average is greater than the CPU utilization, there are other factors that
are keeping the processe in the run queue that waiting for CPU:

(TODO: fill in)

## Useful commands:

* processes in run queue: `ps -ef -o state,comm | grep ^R`
