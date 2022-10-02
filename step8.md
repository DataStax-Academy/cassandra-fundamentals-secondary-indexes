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
 <a href='command:katapod.loadPage?[{"step":"step7"}]'
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 8 of 8</span>
 <a href='command:katapod.loadPage?[{"step":"finish"}]'
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">Materialized view limitations</div>

First and foremost, it is possible that a materialized view and a base table 
become out-of-sync. Cassandra does not provide a way to automatically detect and fix such inconsistencies 
other than dropping and recreating the materialized view, which is not an ideal solution in production: 

```
DROP MATERIALIZED VIEW users_by_name;

CREATE MATERIALIZED VIEW IF NOT EXISTS 
users_by_name AS 
  SELECT * FROM users
  WHERE name IS NOT NULL AND email IS NOT NULL
PRIMARY KEY ((name), email);
```

To substantially lower the risk of base-view inconsistency, use consistency levels `LOCAL_QUORUM` and higher for 
base table writes. In addition, standard recommended repair procedures should be performed on both tables and views regularly or 
whenever a node is removed, replaced or started back up. 

Second, in terms of performance, even though writes to base tables and views are asynchronous, 
each materialized view slows down writes to its base table by approximately 10%. We recommend to not create more than two materialized views per table. 

Finally, statement `CREATE MATERIALIZED VIEW` has restrictions on its query and primary key definitions that we previously discussed. In some cases, 
it is simply impossible to use a materialized view, while a regular table is always an excellent option. Take a look at this example:


```
-- View returns an error
CREATE MATERIALIZED VIEW IF NOT EXISTS 
users_by_name_age AS 
  SELECT * FROM users
  WHERE name IS NOT NULL AND email IS NOT NULL
    AND age  IS NOT NULL
PRIMARY KEY ((name, age), email);

-- Table works
CREATE TABLE users_by_name_age (
  email TEXT,
  name TEXT,
  age INT,
  date_joined DATE,
  PRIMARY KEY ((name, age), email)
);
```

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"step7"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
 <a href='command:katapod.loadPage?[{"step":"finish"}]'
    class="btn btn-dark navigation-bottom-right">Next ➡️
  </a>
</div>

