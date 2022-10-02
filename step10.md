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
 <a href='command:katapod.loadPage?[{"step":"step9"}]'
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 10 of 10</span>
 <a href='command:katapod.loadPage?[{"step":"finish"}]'
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">Secondary index limitations</div>

To understand secondary index limitations, let's take a closer look at how they work in comparison to Cassandra tables and 
materialized views.

Tables and materialized views are examples of *distributed indexing*. A table or view data structure is distributed across all nodes 
in a cluster based on a partition key. When retrieving data using a partition key, Cassandra knows exactly which replica nodes may contain the result. 
For example, given a `100`-node cluster with the replication factor of `5`, at most `5` replica nodes and `1` coordinator node need to participate 
in a query.

In contrast, secondary indexes are examples of *local indexing*. A secondary index is represented by many independent data structures that index data 
stored on each node. When retrieving data using only an indexed column, Cassandra has no way to determine which nodes may have necessary data and 
has to query all nodes in a cluster. For example, given a `100`-node cluster with any replication factor, all `100` nodes have to search 
their local index data structures. This does not scale well.

Therefore, for real-time transactional queries, you should only use a secondary index when a partition key is also known, 
such that your query retrieves rows from a known partition based on an indexed column. In this case, Cassandra takes advantage 
of both distributed and local indexing.

Secondary indexes can also be beneficial to distribute processing across all nodes in a cluster 
for expensive analytical queries that retrieve a large subset of table rows based on a low-cardinality column. Such queries are generally run via *Spark-Cassandra Connector*, where 
retrieved data is further processed using *Apache Spark™*. Note, however, that *Apache Solr™*-based search indexes can do substantially better 
than secondary indexes in this use case.

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"step9"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
 <a href='command:katapod.loadPage?[{"step":"finish"}]'
    class="btn btn-dark navigation-bottom-right">Next ➡️
  </a>
</div>

