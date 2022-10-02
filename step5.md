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
 <a href='command:katapod.loadPage?[{"step":"step4"}]'
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 5 of 8</span>
 <a href='command:katapod.loadPage?[{"step":"step6"}]'
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">Creating materialized view "users_by_date_joined"</div>

Next, create materialized view `users_by_date_joined` to be able to retrieve 
users based on their joining date. For example, the view should support the following query:

<pre class="non-executable-code">
SELECT * FROM users_by_date_joined
WHERE date_joined = '2020-01-01';
</pre>

✅ Create the materialized view:
<details>
  <summary>Solution</summary>

```
CREATE MATERIALIZED VIEW IF NOT EXISTS 
users_by_date_joined AS 
  SELECT * FROM users
  WHERE date_joined IS NOT NULL AND email IS NOT NULL
PRIMARY KEY ((date_joined), email);
```

</details>

<br/>

✅ Retrieve users from the base table and materialized view:
<details>
  <summary>Solution</summary>

```
SELECT * FROM users;
SELECT * FROM users_by_date_joined;
```

</details>

<br/>

✅ Delete one user from the base table:
<details>
  <summary>Solution</summary>

```
DELETE FROM users WHERE email = 'jim@datastax.com';

SELECT * FROM users;
SELECT * FROM users_by_date_joined;
```

</details>

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"step4"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
 <a href='command:katapod.loadPage?[{"step":"step6"}]'
    class="btn btn-dark navigation-bottom-right">Next ➡️
  </a>
</div>

