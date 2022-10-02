<!-- TOP -->
<div class="top">
  <img src="https://datastax-academy.github.io/katapod-shared-assets/images/ds-academy-logo.svg" />
  <div class="scenario-title-section">
    <span class="scenario-title">Secondary Indexes in Apache Cassandra®</span>
    <span class="scenario-subtitle">ℹ️ For technical support, please contact us via <a href="mailto:aleksandr.volochnev@datastax.com">email</a> or <a href="https://dtsx.io/aleks">LinkedIn</a>.</span> 
  </div>
</div>

<!-- NAVIGATION -->
<div id="navigation-top" class="navigation-top">
 <a href='command:katapod.loadPage?[{"step":"intro"}]'
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 1 of 10</span>
 <a href='command:katapod.loadPage?[{"step":"step2"}]' 
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">Secondary indexes</div>

Each table only supports a limited set of queries based on its primary key definition. 
Additional queries can be supported by creating new tables with different primary keys, 
materialized views or *secondary indexes*. A *secondary index* can be created on a table column to enable 
querying data based on values stored in this column. Internally, a secondary index is represented by 
additional data structures that are created and automatically maintained on each cluster node. There are two types of secondary indexes:
- *Regular secondary index* (*2i*): a secondary index that uses hash tables to index data and supports equality (`=`) predicates.
- *SSTable-attached secondary index* (*SASI*): an experimental and more efficient secondary index that uses B+ trees to index data and can support equality (`=`), 
inequality (`<`, `<=`, `>`, `>=`) and even text pattern matching (`LIKE`).

While secondary indexes may seem very convenient, they have serious performance limitations and their use in production 
should be limited to the following two rather specific cases: 
- *Real-time transactional query*: retrieving rows from a large multi-row partition, 
when both a partition key and an indexed column are used in a query.
- *Expensive analytical query*: retrieving a large number of rows from potentially all partitions, when 
only an indexed *low-cardinality* column is used in a query. A low-cardinality column is characterized by 
a large number of duplicates stored in it and a limited data range for its possible values. 

For all other use cases, which usually involve *high-cardinality columns*, 
you should always prefer tables and materialized views to secondary indexes.

The general recommendation is to have at most one secondary index per table. And most tables do not need any. We 
provide more details about the secondary index limitations later in this presentation.

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"intro"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
 <a href='command:katapod.loadPage?[{"step":"step2"}]'
    class="btn btn-dark navigation-bottom-right">Next ➡️
  </a>
</div>
