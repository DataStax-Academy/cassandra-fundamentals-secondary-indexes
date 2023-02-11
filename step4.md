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
 <a href='command:katapod.loadPage?[{"step":"step3"}]'
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 4 of 10</span>
 <a href='command:katapod.loadPage?[{"step":"step5"}]' 
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">Using a 2i for equality queries</div>

Our first task is to create a secondary index to support 
retrieving rows from table `ratings_by_movie` based on the `rating` column like in this query:

<pre class="non-executable-code">
SELECT * FROM ratings_by_movie
WHERE title  = 'Alice in Wonderland'
  AND year   = 2010
  AND rating = 9;
</pre>

✅ Create the 2i:
```
CREATE INDEX IF NOT EXISTS 
   rating_ratings_by_movie_2i 
ON ratings_by_movie (rating);
```

✅ Retrieve rows based on a rating value: 
```
-- Real-time transactional query
SELECT * FROM ratings_by_movie
WHERE title  = 'Alice in Wonderland'
  AND year   = 2010
  AND rating = 9;
```
 
```
-- Expensive analytical query
SELECT * FROM ratings_by_movie
WHERE rating = 9;
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

