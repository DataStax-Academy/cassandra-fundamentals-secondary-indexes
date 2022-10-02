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
 <a href='command:katapod.loadPage?[{"step":"step4"}]'
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 5 of 10</span>
 <a href='command:katapod.loadPage?[{"step":"step6"}]'
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">Using a 2i for equality queries</div>

Next, create a secondary index to support 
retrieving rows from table `ratings_by_movie` based on the `date_rated` column like in this query:

<pre class="non-executable-code">
SELECT * FROM ratings_by_movie
WHERE title      = 'Alice in Wonderland'
  AND year       = 2010
  AND date_rated = '2020-05-10';
</pre>

✅ Create the 2i:
<details>
  <summary>Solution</summary>

```
CREATE INDEX IF NOT EXISTS 
   date_rated_ratings_by_movie_2i 
ON ratings_by_movie (date_rated);
```

</details>

<br/>

✅ Retrieve rows based on a date value: 
<details>
  <summary>Solution</summary>

```
-- Real-time transactional query
SELECT * FROM ratings_by_movie
WHERE title      = 'Alice in Wonderland'
  AND year       = 2010
  AND date_rated = '2020-05-10';
``` 

```
-- Expensive analytical query
SELECT * FROM ratings_by_movie
WHERE date_rated = '2020-05-10';
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

