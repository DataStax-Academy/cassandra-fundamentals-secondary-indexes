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
 <a href='command:katapod.loadPage?[{"step":"intro"}]'
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 1 of 8</span>
 <a href='command:katapod.loadPage?[{"step":"step2"}]' 
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">Materialized views</div>

Each table only supports a limited set of queries based on its primary key definition. 
To support additional queries, the most generic and efficient solution is to duplicate the same data into 
a new table with a different primary key. This process is frequently referred to as data *denormalization* and 
data *duplication*. The drawback is that now you have to do multiple inserts, updates and deletes 
to maintain the same data stored in multiple places. You may even need to use atomic batches in some cases. 

To remove the burden of keeping multiple tables in sync from a developer, Cassandra supports 
an experimental feature called *materialized views*. A *materialized view* is a read-only 
table that automatically duplicates, persists and maintains a subset of data from a *base table*. Any change to data 
in a base table is automatically propagated to every view associated with this table.   

Materialized views are great for convenience but you should also be aware of their limitations, which we discuss later in this presentation.

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"intro"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
 <a href='command:katapod.loadPage?[{"step":"step2"}]'
    class="btn btn-dark navigation-bottom-right">Next ➡️
  </a>
</div>
