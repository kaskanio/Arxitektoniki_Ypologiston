## Ερώτημα 1.
Τα περισσότερα στοιχεία τα παίρνω μέσα από την main.

* CPU Type:  Υπάρχουν 3 τύποι CPU, οι atomic, minor και hpi. Ο default είναι ο atomic.
 * parser.add_argument("--cpu", type=str, choices=cpu_types.keys(),
                        default="atomic",
* CPU Frequency: Η default συνχότητα λειτουργίας είναι στα 4GHz.
  * parser.add_argument("--cpu-freq", type=str, default="4GHz")
* CPU Cores: Default είναι 1.
 * parser.add_argument("--num-cores", type=int, default=1,
                        help="Number of CPU cores")
* Memory Type: Default είναι DDR3_1600_8x8
  * parser.add_argument("--mem-type", default="DDR3_1600_8x8",
                        choices=ObjectList.mem_list.get_names(),
                        help = "type of memory to use")
* Memory Channels: Default είναι 2.
  * parser.add_argument("--mem-channels", type=int, default=2,
                        help = "number of memory channels")
* Memory Ranks: Default είναι 2.
  * parser.add_argument("--mem-ranks", type=int, default=None,
                        help = "number of memory ranks per channel")
* Memory Size: Default είναι 2GB.
  * parser.add_argument("--mem-size", action="store", type=str,
                        default="2GB",
                        help="Specify the physical memory size")
* Cache: cache_line_size = 64.

## Ερώτημα 2.
* 
