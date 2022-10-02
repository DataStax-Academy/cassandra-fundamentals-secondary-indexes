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
 <a href='command:katapod.loadPage?[{"step":"step1"}]'
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 2 of 10</span>
 <a href='command:katapod.loadPage?[{"step":"step3"}]' 
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">Syntax</div>

To create regular secondary indexes (2i) and SSTable-attached secondary indexes (SASI), 
Cassandra Query Language provides statements `CREATE INDEX` and `CREATE CUSTOM INDEX`, respectively, with the following simplified syntax:

<pre class="non-executable-code">
CREATE INDEX [ IF NOT EXISTS ] 
   index_name
ON [keyspace_name.] table_name ( column_name ); 
</pre>

<pre class="non-executable-code">
CREATE CUSTOM INDEX [ IF NOT EXISTS ] 
   index_name
ON [keyspace_name.] table_name ( column_name )
USING 'org.apache.cassandra.index.sasi.SASIIndex' 
[ WITH OPTIONS = { option_map } ];
</pre>

First, notice that an index is identified by a name and is created 
on exactly one column of a given table. Indexes on multiple columns are not supported.

Second, the main different between 2i and SASI definitions is in the `USING` clause with the index class.

Finally, a SASI can have options, of which many are related to text analysis, tokenization, capitalization and so forth. 
A special `mode` option allows choosing between `PREFIX` (default), `CONTAINS` and `SPARSE` indexes. For simplicity, we will 
not use any explicit options with our SASI indexes but you are welcome to further explore SASI options in the documentation. 

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"step1"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
 <a href='command:katapod.loadPage?[{"step":"step3"}]'
    class="btn btn-dark navigation-bottom-right">Next ➡️
  </a>
</div>
