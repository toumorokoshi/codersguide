# High Memory Usage

## Cache and Buffer are mostly unimportant

memory used for cache and buffer are sometimes folded into the same
field as used memory. Cache and buffer refer to memory that is used to
improve the performance of reads and writes to disk: If your
application does not perform heavy reads and writes to disk, it
is probably irrelevant.

Cache and buffer take as much available memory as necessary, and does
not impede memory consumption from the processes that need them.

## Look at Resident Set Size, not Virtual Memory.

Some operating systems allow the allocation of memory beyond what is
available. Linux is one example, and distinguishes between what the process
believes it has allocated (virtual memory) versus what it is actually using.

RSS is a real indicator of how much your application consumes.

## Look at swap as well

If your operating system has any swap partitions, those can show how
much memory is being used as well.  The operating system moves
seldom-used objects in memory to swap, as the impact of reading rarely
used data from disk vs ram is negligible.

However, when the operating system is forced to use swap more
frequently (such as when the processes are actively using more memory
than exists on the host), the Linux kernel attempts to alleviate that
with swap, causing very high read and write rate to and from disk.

This has a significant performance impact on applications, as the data
it was used to reading quickly now takes an order of magnitune or more
time.

### Quick Linux Commands

Find memory used by a process type

    ps -e -o comm,rss | grep $MY_PROCESS | tr -s ' ' | cut -d ' ' -f 2 | paste -sd+ | bc
