tgtop
=====

Task group per-CPU top.

This tool helps monitor CFS behavior for task groups on SMP systems.

## Example

```
L GROUP           %CPU   CPU0   CPU1   CPU2   CPU3
0-/                209    5/2    4/2 100/48 100/48
1-docker           200    0/0    0/0 100/50 100/50
2-f6e9479dc0ca     200    0/0    0/0 100/50 100/50

05:55:00 | Ntasks: 3/719 | Load avg: 0.86 0.54 0.72 | View: 1-%CPU | Frozen
```

## Requirements

- Control group `cpu` and `cpuacct` must have the same groups.

- Kernel must be compiled with `CONFIG_SCHED_DEBUG=y`.

## Views

Each view shows group name, group stats, and per-CPU stats.  3 views
are available:

### 1-%CPU:

    - group stats: total CPU usage of the group
    - per-CPU stats x/y:
        - x: group usage on this CPU
        - y: percent of this CPU usage to total group usage

### 2-SHARES:

    - group stats: "cpu.shares" of the group
    - per-CPU stats x/y:
        - x: percent of entity weight to cfs_rq weight on this CPU
        - y: percent of entity weight to total group weight

### 3-NTASKS:

    - group stats: number of tasks directly belong to this group
    - per-CPU stats x/y:
        - x: number of group running tasks on this CPU
        - y: number of group tasks on this CPU
