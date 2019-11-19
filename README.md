## Ερώτημα 1.
Τα περισσότερα στοιχεία τα παίρνω μέσα από την main.

* CPU Type:  Υπάρχουν 3 τύποι CPU, οι atomic, minor και hpi. Ο default είναι ο atomic.  
`parser.add_argument("--cpu", type=str, choices=cpu_types.keys(), default="atomic", help="CPU model to use")`
                        
* CPU Frequency: Η default συνχότητα του CPU είναι στα 4GHz.  
`parser.add_argument("--cpu-freq", type=str, default="4GHz")`
  
* CPU Cores: Default είναι 1.  
`parser.add_argument("--num-cores", type=int, default=1, help="Number of CPU cores")`
                        
* Memory Type: Default είναι DDR3_1600_8x8  
`parser.add_argument("--mem-type", default="DDR3_1600_8x8", choices=ObjectList.mem_list.get_names(), help = "type of memory to use")`
                        
* Memory Channels: Default είναι 2.  
`parser.add_argument("--mem-channels", type=int, default=2, help = "number of memory channels")`  
                        
* Memory Ranks: Default είναι none.  
`parser.add_argument("--mem-ranks", type=int, default=None, help = "number of memory ranks per channel")`
                        
* Memory Size: Default είναι 2GB.  
`parser.add_argument("--mem-size", action="store", type=str,
                        default="2GB",
                        help="Specify the physical memory size")`
                        
* Clock domain: 1GHz  
`self.clk_domain = SrcClockDomain(clock="1GHz",voltage_domain=self.voltage_domain)`
 
* Voltage domain: 3.3V  
`self.voltage_domain = VoltageDomain(voltage="3.3V")`

* Cache: `cache_line_size = 64`.  


## Ερώτημα 2.
Από το config.ini μπορώ να βρω τα εξής:
* Τύπος CPU Minor (αφού τρέχουμε την εντολή με τον minor):  
Line 67: `type=MinorCPU`
* Αριθμός threads 1:  
Line 117: `numThreads=1.`
* Μέγεθος μνήμης από 0~2GB.  
Line 25: `mem_ranges=0:2147483647`
* Memory Ranks 2:  
Line 1296: `ranks_per_channel=2`
* Clock Domain 1000:  
Line 46: `clock=1000`
* Cache line size 64:  
Line 15: `cache_line_size=64`    

#Ερώτημα 2α
Από το stats.txt για την εκτέλεση με τον minorCPU παίρνω τα εξής:
<pre>
final_tick                                   44310000                       # Number of ticks from beginning of simulation (restored from checkpoints and never reset)
host_inst_rate                                 689636                       # Simulator instruction rate (inst/s)
host_mem_usage                                 707276                       # Number of bytes of host memory used
host_op_rate                                   787408                       # Simulator op (including micro ops) rate (op/s)
host_seconds                                     0.02                       # Real time elapsed on the host
host_tick_rate                             2354650922                       # Simulator tick rate (ticks/s)
sim_freq                                 1000000000000                       # Frequency of simulated ticks
sim_insts                                       12887                       # Number of instructions simulated
sim_ops                                         14803                       # Number of ops (including micro ops) simulated
sim_seconds                                  0.000044                       # Number of seconds simulated
sim_ticks                                    44310000                       # Number of ticks simulated
</pre>
