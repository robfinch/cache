# Cache
## Overview
This repository contains code for instruction and data caches that may be used in a CPU core. The components are written in System Verilog.
The caches are single-cycle access for cache hits. They are only single level. How long the cache takes to update depends on the speed of the system bus. In a system-on-chip there is typically a system cache which may act somewhat like a second level cache.
The caches interface to a 256-bit wide bus using FTA bus which is an asynchronous bus. Cache lines are 512-bits wide, although this could be changed in the cache_pkg.sv in the inc repository.

## Instruction Cache Code
The instruction cache outputs odd/even pairs of cache lines to allow instructions to span a cache line.
The cache is 32kB organized as four ways of 8kB.
* icache.sv - top level for the instruction cache
* icache_ctrl.sv - control logic for the instruction cache
* icache_req_generator.sv	-generates bus requests to fill the cache
* icache_ack_processor.sv - processes bus responses
* cache_hit - used to detect cache hits
* cache_tag - used to store cache tags

## Data Cache Code
The data cache return a single cache line. Unaligned data that spans cache-lines will require two accesses to the data cache.
The data cache is 64kB organized as four ways of 16kB.
* icache.sv - top level for the data cache
* icache_ctrl.sv - control logic for the data cache

## Support RAMs
* sram_1r1w.sv - single independent read/write port RAM
* sram_1r1w_bw.sv - single independent read/write port RAM with byte write enables
* sram_512x256_1rw1r.sv - dual port block RAM with a read/write port and a second read port.

## Status
These cores have been used in several projects so they should be close to working.

## ToDo
Develop independent test benches for the caches. Currently they have been tested as part of a larger CPU project.


