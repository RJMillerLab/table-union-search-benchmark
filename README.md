# BENCHMARK FOR TABLE UNION SEARCH

BENCHMARK CREATION

Since there is no available ground truth for table union search on Open Data, we synthesized a benchmark using tables from Canadian and UK Open Data. The ground truth provided by the benchmark allows us to evaluate the precision, recall and MAP of table union search.

First, we find base original tables from Open Data. We choose the base tables by looking at all tables in descending order of row counts and pick tables that have at least 5 text columns. This is to ensure both natural language and ontology measures are treated equally. In order to avoid using near-duplicate tables, every pair of selected tables must have at least 5 different column names. Then, we perform keyword search on a repository of consisting of the meta data of Open Data tables using the meta data (table name and publisher) available for each base table. For each base table, we select one of the highest ranking tables and manually align it with the corresponding table. This gives us an extended set of base tables.  The added tables are about similar topics as the original base tables but are not necessarily unionable on all attributes. For example, we align a table containing transportation information of Manchester with a table containing information about bus stops statistics in Chicago. 

Next, we create groups of benchmark tables by first issuing a projection on a random c-subset of text columns of an original table, and then a selection with some limit and offset on the projected table. For instance, on an original table T, we issue "CREATE TABLE T_3 AS SELECT distinct c1, c2, c5 FROM T" to create a projection of 3-subset of columns.
Then, we issue "SELECT * FROM T\_3 LIMIT 100 OFFSET 0" to generate a table with 100 rows, and additional unionable tables are generated similarly by choosing appropriate offsets so the tables do not overlap. For every original table with n text column, we generate two random $c$-subset projections for c = 1, 2, ..., n. 

For every pair of benchmark tables, the ground truth alignment can be derived from matching columns that came from the same original table or the tables coming from the base table that has been found unionable by keyword search. A correct alignment only happens when all matching columns are aligned correctly.

FOLDER ORGANIZATION

To compare table union search with existing frameworks and evaluate the effectiveness of different unionability measures, we generated two benchmark of size 1,300 and 5,000 tables. The smaller benchmark is a subset of the one with 5,000 tables. These benchmarks are available in sqlite databases in "1300/data" and "5000/data" directories. 
"base" databases contain the base tables used in generating the benchmark and "benchmark" databases contain unionable tables. For each benchmark, we provide a ground truth database in "groundtruth" directory. This database contains three tables. Table "att_groundtruth" provides all mappings between unionable attributes. Table "alignment_groundtruth" provides the size of the max-alignment (c) between two tables. Finally, table "recall_groundtruth" provides the number of tables that are unionable with a benchmark table. 

We also include a script in the benchmark that stores benchmark tables as csv files. 

