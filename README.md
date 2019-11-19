# _Ερώτημα 1_
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


# _Ερώτημα 2_
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


# _Ερώτημα 3_
**Minor** is an _in-order processor_ model with a fixed pipeline but configurable data structures and execute behaviour. It is intended to be used to model processors with strict in-order execution behaviour and allows visualisation of an instruction's position in the pipeline through the MinorTrace/minorview.py format/tool. The intention is to provide a framework for micro-architecturally correlating the model with a particular, chosen processor with similar capabilities.  

The model **isn't** currently capable of multithreading but there are THREAD comments in key places where stage data needs to be arrayed to support multithreading.

## _Ερώτημα 3a_  
Από το stats.txt για την εκτέλεση με τον minorCPU παίρνω τα εξής:
<pre>
final_tick                                   36381000                       # Number of ticks from beginning of simulation (restored from checkpoints and never reset)
host_inst_rate                                 231814                       # Simulator instruction rate (inst/s)
host_mem_usage                                 711628                       # Number of bytes of host memory used
host_op_rate                                   266784                       # Simulator op (including micro ops) rate (op/s)
host_seconds                                     0.06                       # Real time elapsed on the host
host_tick_rate                              648402559                       # Simulator tick rate (ticks/s)
sim_freq                                 1000000000000                       # Frequency of simulated ticks
sim_insts                                       12972                       # Number of instructions simulated
sim_ops                                         14964                       # Number of ops (including micro ops) simulated
sim_seconds                                  0.000036                       # Number of seconds simulated
sim_ticks                                    36381000                       # Number of ticks simulated
</pre>  
Από το stats.txt για την εκτέλεση με τον TimingSimpleCPU παίρνω τα εξής:
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

> **Με τα παραπάνω αποτελέσματα παρατηρώ ότι το πρόγραμμα εκτελέστηκε γρηγορότερα με τον TimingSimpleCPU από ότι με τον MinorCPU.

## _Ερώτημα 3c_  
Αλλάζοντας την συχνότητα σε 10KHz, έχω τα εξής αποτελέσματα σε χρόνους για τον minorCPU:
<pre>
final_tick                               2160100000000                       # Number of ticks from beginning of simulation (restored from checkpoints and never reset)
host_inst_rate                                   4035                       # Simulator instruction rate (inst/s)
host_mem_usage                                 711628                       # Number of bytes of host memory used
host_op_rate                                     4655                       # Simulator op (including micro ops) rate (op/s)
host_seconds                                     3.21                       # Real time elapsed on the host
host_tick_rate                           671964561234                       # Simulator tick rate (ticks/s)
sim_freq                                 1000000000000                       # Frequency of simulated ticks
sim_insts                                       12972                       # Number of instructions simulated
sim_ops                                         14964                       # Number of ops (including micro ops) simulated
sim_seconds                                  2.160100                       # Number of seconds simulated
sim_ticks                                2160100000000                       # Number of ticks simulated
</pre>  

Αλλάζοντας την συχνότητα σε 10KHz, έχω τα εξής αποτελέσματα σε χρόνους για τον TimingSimpleCPU:
<pre>
final_tick                               3965900000000                       # Number of ticks from beginning of simulation (restored from checkpoints and never reset)
host_inst_rate                                   2242                       # Simulator instruction rate (inst/s)
host_mem_usage                                 707276                       # Number of bytes of host memory used
host_op_rate                                     2575                       # Simulator op (including micro ops) rate (op/s)
host_seconds                                     5.75                       # Real time elapsed on the host
host_tick_rate                           689928409045                       # Simulator tick rate (ticks/s)
sim_freq                                 1000000000000                       # Frequency of simulated ticks
sim_insts                                       12887                       # Number of instructions simulated
sim_ops                                         14803                       # Number of ops (including micro ops) simulated
sim_seconds                                  3.965900                       # Number of seconds simulated
sim_ticks                                3965900000000                       # Number of ticks simulated
</pre>  

> **Αλλάζοντας σημαντικά τη συχνότητα σε 10KHz από 1GHz που είχαμε στο προηγούμενο ερώτημα, βλέπω πως τώρα ο minorCPU εκτελεί το πρόγραμμα γρηγορότερα από ότι τον TimingSimpleCPU.

Τώρα, χρησιμοποιόντας πάλι τη default συχνότητα του CPU και αλλάζοντας το τύπο της μνήμης και τις συχνότητες της σε LPDDR2_S4_1066_1x32 έχω για τον minorCPU τα εξής αποτελέσματα:  
<pre>
final_tick                                   45776000                       # Number of ticks from beginning of simulation (restored from checkpoints and never reset)
host_inst_rate                                 232010                       # Simulator instruction rate (inst/s)
host_mem_usage                                 711628                       # Number of bytes of host memory used
host_op_rate                                   267179                       # Simulator op (including micro ops) rate (op/s)
host_seconds                                     0.06                       # Real time elapsed on the host
host_tick_rate                              817053267                       # Simulator tick rate (ticks/s)
sim_freq                                 1000000000000                       # Frequency of simulated ticks
sim_insts                                       12972                       # Number of instructions simulated
sim_ops                                         14964                       # Number of ops (including micro ops) simulated
sim_seconds                                  0.000046                       # Number of seconds simulated
sim_ticks                                    45776000                       # Number of ticks simulated
</pre>  

Βάζοντας την ίδια μνήμη LPDDR2_S4_1066_1x32 στον TimingSimpleCPU τα αποτελέσματα μου είναι:  
<pre>
final_tick                                   52009000                       # Number of ticks from beginning of simulation (restored from checkpoints and never reset)
host_inst_rate                                 647657                       # Simulator instruction rate (inst/s)
host_mem_usage                                 707276                       # Number of bytes of host memory used
host_op_rate                                   740337                       # Simulator op (including micro ops) rate (op/s)
host_seconds                                     0.02                       # Real time elapsed on the host
host_tick_rate                             2598754962                       # Simulator tick rate (ticks/s)
sim_freq                                 1000000000000                       # Frequency of simulated ticks
sim_insts                                       12887                       # Number of instructions simulated
sim_ops                                         14803                       # Number of ops (including micro ops) simulated
sim_seconds                                  0.000052                       # Number of seconds simulated
sim_ticks                                    52009000                       # Number of ticks simulated
</pre>

> **Παρατηρώ όπως και με τις Default τιμές, ο TimingSimpleCPU είναι γρηγορότερος από τον minorCPU.**
