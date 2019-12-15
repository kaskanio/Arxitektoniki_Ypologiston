#### _Ομάδα 21: Κασκανιώτης Διονύσιος-Παναγιώτης 8702 , Τσίκας Δημήτριος-Ελευθέριος 8749_

# Bήμα 1
## Ερώτημα 1
Τα ζητούμενα δεδομένα τα παίρνω από το αρχείο config.ini του κάθε benchmark.

<pre>
              icache  assoc   dcache  assoc   L2cache  assoc    cache.line
specbzip2      32768   2       65536   2       2097152  8        64
spechmmer     32768   2       65536   2       2097152  8        64
speclibm      32768   2       65536   2       2097152  8        64
specmfc       32768   2       65536   2       2097152  8        64 
specjjeng     32768   2       65536   2       2097152  8        64
</pre>

## Ερώτημα 2
Τα ζητούμενα δεδομένα τα παίρνω από το αρχείο stats.txt του κάθε benchmark.

<pre>
              sim_seconds   cpi         l2cache_miss_rate   icache_miss_rate    dcache_miss_rate
specbzip2      0.084159      1.683172    0.281708            0.000074            0.014840
spechmmer     0.059368      1.187362    0.082246            0.000205            0.001645
speclibm      0.174681      3.493611    0.999927            0.000099            0.060971
specmfc       0.055477      1.109538    0.724040            0.000037            0.002051
specjjeng     0.513541      10.270810   0.999979            0.000020            0.121829
</pre>

## Ερώτημα 3
Τα ζητούμενα δεδομένα τα παίρνω από το αρχείο stats.txt του κάθε benchmark. Παρατηρώ τις τιμές των `system.clk_domain.clock` και `system.cpu_clk_domain.clock`. Οι τιμές για το 1ο ερώτημα είναι 1000 και 500 μαζί, ενώ στα benchmarks με το 1GHz οι τιμές και των 2 παραμένουν 1000.

* Default:
<pre>
specbzip2    system.clk_domain.clock                          1000
            system.cpu_clk_domain.clock                      500
spechmmer   system.clk_domain.clock                          1000
            system.cpu_clk_domain.clock                      500
speclibm    system.clk_domain.clock                          1000
            system.cpu_clk_domain.clock                      500
specmfc     system.clk_domain.clock                          1000
            system.cpu_clk_domain.clock                      500
specjjeng   system.clk_domain.clock                          1000
            system.cpu_clk_domain.clock                      500
</pre>

* 1GHz:
<pre>
specbzip2    system.clk_domain.clock                          1000
            system.cpu_clk_domain.clock                      1000
spechmmer   system.clk_domain.clock                          1000
            system.cpu_clk_domain.clock                      1000
speclibm    system.clk_domain.clock                          1000
            system.cpu_clk_domain.clock                      1000
specmfc     system.clk_domain.clock                          1000
            system.cpu_clk_domain.clock                      1000
specjjeng   system.clk_domain.clock                          1000
            system.cpu_clk_domain.clock                      1000
</pre>

# Bήμα 2
## Ερώτημα 1

* Για το **bzip2** benchmark παρατηρήσαμε ότι το cpi επηρεάζεται κυρίως με τις αλλαγές των cacheline και του l2_cache_size. Όπως φαίνεται και στο διάγραμμα, καθώς αυξάνεται η μνήμη L2 Cache, το CPI μειώνεται άρα έχουμε καλύτερη απόδοση. Εξαίρεση αποτελεί η περίπτωση στην οποία το cacheline είναι 16, στην οποία αρχικά παρατηρούμε μια αύξηση, ενώ για τιμές L2 Cache μεγαλύτερες από 512 έχουμε πτώση του CPI. Φυσικά να τονίσουμε πως το καλύτερο αποτέλεσμα το πετυχαίνουμε το υψηλότερο cacheline, το οποίο στις δοκιμές μας ήταν 128.
