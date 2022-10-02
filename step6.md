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
 <a href='command:katapod.loadPage?[{"step":"step5"}]'
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 6 of 8</span>
 <a href='command:katapod.loadPage?[{"step":"step7"}]' 
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">Creating materialized view "movies_by_genre_year"</div>

Our third task is to create a materialized view with name `movies_by_genre_year` that will allow retrieving 
movies based on their genres and release years like in this query:

<pre class="non-executable-code">
SELECT * FROM movies_by_genre_year
WHERE genre = 'Adventure' AND year = 2010;
</pre>

We can use table `movies_by_genre` as a base table for the view.

✅ Create the materialized view:
```
CREATE MATERIALIZED VIEW IF NOT EXISTS 
movies_by_genre_year AS 
  SELECT * FROM movies_by_genre
  WHERE genre IS NOT NULL AND year IS NOT NULL
    AND title IS NOT NULL
PRIMARY KEY ((genre, year), title);
```

✅ Retrieve movies from the base table and materialized view:
```
SELECT * FROM movies_by_genre;
SELECT * FROM movies_by_genre_year;
```

✅ Update the *Alice in Wonderland* movie average rating:
```
UPDATE movies_by_genre SET avg_rating = 8.44 
WHERE title = 'Alice in Wonderland' AND year = 2010
  AND genre IN ('Fantasy','Adventure');

SELECT * FROM movies_by_genre;
SELECT * FROM movies_by_genre_year;
```

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"step5"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
 <a href='command:katapod.loadPage?[{"step":"step7"}]'
    class="btn btn-dark navigation-bottom-right">Next ➡️
  </a>
</div>

