<!-- TOP -->
<div class="top">
  <img src="https://datastax-academy.github.io/katapod-shared-assets/images/ds-academy-logo.svg" />
  <div class="scenario-title-section">
    <span class="scenario-title">Materialized Views in Apache Cassandra®</span>
    <span class="scenario-subtitle">ℹ️ For technical support, please contact us via <a href="mailto:aleksandr.volochnev@datastax.com">email</a> or <a href="https://dtsx.io/aleks">LinkedIn</a>.</span> 
  </div>
</div>

<!-- NAVIGATION -->
<div id="navigation-top" class="navigation-top">
 <a href='command:katapod.loadPage?[{"step":"step1"}]'
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 2 of 8</span>
 <a href='command:katapod.loadPage?[{"step":"step3"}]' 
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">Syntax</div>

To create a materialized view, Cassandra Query Language provides the `CREATE MATERIALIZED VIEW` statement with the following simplified syntax:

<pre class="non-executable-code">
CREATE MATERIALIZED VIEW [ IF NOT EXISTS ] 
[keyspace_name.] view_name AS 
  SELECT * | column_name [ , ... ]
  FROM [keyspace_name.] base_table_name
  WHERE primary_key_column_name IS NOT NULL [ AND ... ] 
PRIMARY KEY ( 
  ( partition_key_column_name  [ , ... ] )
  [ clustering_key_column_name [ , ... ] ]
)  
[ WITH CLUSTERING ORDER BY 
  ( clustering_key_column_name ASC|DESC [ , ... ] )
];
</pre>

First, notice that a view is created within an existing keyspace. If a keyspace name is omitted, the current working keyspace is used.

Second, what gets persisted into a view is defined by a `SELECT` statement.

Finally, a view primary key and an optional clustering order are defined simlarly to the respective `CREATE TABLE` definitions.

Most importantly, the following restrictions apply to any materialized view definition:
- A view and a base table must belong to the same keyspace;
- No base table static column can be included in a view;
- All base table primary key columns must become materialized view primary key columns;
- At most one base table non-primary key column can become a materialized view primary key column;
- All view primary key columns must be restricted to not allow nulls.

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"step1"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
 <a href='command:katapod.loadPage?[{"step":"step3"}]'
    class="btn btn-dark navigation-bottom-right">Next ➡️
  </a>
</div>
