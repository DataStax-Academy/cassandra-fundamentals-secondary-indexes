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
 <a href='command:katapod.loadPage?[{"step":"step3"}]'
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 4 of 8</span>
 <a href='command:katapod.loadPage?[{"step":"step5"}]' 
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">Creating materialized view "users_by_name"</div>

Our first task is to create a materialized view with name `users_by_name` that will allow retrieving 
users based on their names like in this query:

<pre class="non-executable-code">
SELECT * FROM users_by_name
WHERE name = 'Joe';
</pre>

We can use table `users` as a base table for the view.

✅ Create the materialized view:
```
CREATE MATERIALIZED VIEW IF NOT EXISTS 
users_by_name AS 
  SELECT * FROM users
  WHERE name IS NOT NULL AND email IS NOT NULL
PRIMARY KEY ((name), email);
```

✅ Retrieve users from the base table and materialized view:
```
SELECT * FROM users;
SELECT * FROM users_by_name;
```

✅ Update a base table row and verify the effect on the materialized view:
```
UPDATE users SET name = 'Joseph' 
WHERE email = 'joe@datastax.com';

SELECT * FROM users WHERE email = 'joe@datastax.com';
SELECT * FROM users_by_name WHERE name = 'Joseph';
```

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"step3"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
 <a href='command:katapod.loadPage?[{"step":"step5"}]'
    class="btn btn-dark navigation-bottom-right">Next ➡️
  </a>
</div>

