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
