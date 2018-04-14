## Introduction
This benchmark provides a ground truth for evaluating table union search algorithms. All tables are synthesized from Open Data tables. For more details, please refer to: 

F. Nargesian, E. Zhu, K. Pu, R. J. Miller, [*Table Union Search on Open Data*](http://www.vldb.org/pvldb/vol11/p813-nargesian.pdf)

## Resources

This suite consists of two benchmarks of size 1,300 and 5,000 tables. The smaller benchmark is a subset of the one with 5,000 tables. These benchmarks are available in sqlite databases at https://www.dropbox.com/sh/3pqlk7irfusm5vu/AACFsy-u2ftvpPgV-ib0dTfaa?dl=0 in "1300/data" and "5000/data" directories. 
The "base" databases contain the base tables used in generating the benchmark and "benchmark" databases contain unionable tables. For each benchmark, we provide a ground truth database in "groundtruth" directory. This database contains three tables. Table "att_groundtruth" provides all mappings between unionable attributes. Table "alignment_groundtruth" provides the size of the max-alignment (c) between two tables. Finally, table "recall_groundtruth" provides the number of tables that are unionable with a benchmark table. 

We also include a script in the benchmark that stores benchmark tables as csv files. 
