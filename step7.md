<!-- TOP -->
<div class="top">
  <img class="scenario-academy-logo" src="https://datastax-academy.github.io/katapod-shared-assets/images/ds-academy-2023.svg" />
  <div class="scenario-title-section">
    <span class="scenario-title">Secondary Indexes in Apache Cassandra®</span>
    <span class="scenario-subtitle">ℹ️ For technical support, please contact us via <a href="mailto:aleksandr.volochnev@datastax.com">email</a> or <a href="https://dtsx.io/aleks">LinkedIn</a>.</span> 
  </div>
</div>

<!-- NAVIGATION -->
<div id="navigation-top" class="navigation-top">
 <a href='command:katapod.loadPage?[{"step":"step6"}]'
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 7 of 10</span>
 <a href='command:katapod.loadPage?[{"step":"step8"}]'
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">Using a SASI for range queries</div>

Practice creating an SSTable-attached secondary index to support 
retrieving rows from table `ratings_by_movie` based on the `date_rated` column 
like in this query:

<pre class="non-executable-code">
SELECT * FROM ratings_by_movie
WHERE title  = 'Alice in Wonderland'
  AND year   = 2010
  AND date_rated >= '2020-05-01' 
  AND date_rated < '2020-06-01';
</pre>

✅ Create the SASI:
<details>
  <summary>Solution</summary>

```
CREATE CUSTOM INDEX IF NOT EXISTS 
   date_rated_ratings_by_movie_sasi 
ON ratings_by_movie (date_rated)
USING 'org.apache.cassandra.index.sasi.SASIIndex';
```

</details>

<br/>

✅ Retrieve rows based on a date range: 
<details>
  <summary>Solution</summary>

```
-- Real-time transactional query
SELECT * FROM ratings_by_movie
WHERE title  = 'Alice in Wonderland'
  AND year   = 2010
  AND date_rated >= '2020-05-01' 
  AND date_rated < '2020-06-01';
```

```
-- Expensive analytical query
SELECT * FROM ratings_by_movie
WHERE date_rated >= '2020-05-01' 
  AND date_rated < '2020-06-01';
```

</details>

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"step6"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
 <a href='command:katapod.loadPage?[{"step":"step8"}]'
    class="btn btn-dark navigation-bottom-right">Next ➡️
  </a>
</div>

