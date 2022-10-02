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
 <a href='command:katapod.loadPage?[{"step":"step6"}]'
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 7 of 8</span>
 <a href='command:katapod.loadPage?[{"step":"step8"}]'
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">Creating materialized view "movies_by_genre_country"</div>

Finally, create materialized view `movies_by_genre_country` to be able to support the 
following query:

<pre class="non-executable-code">
SELECT * FROM movies_by_genre_country
WHERE genre = 'Adventure' 
  AND country = 'USA'
  AND year >=2010
ORDER BY year DESC;
</pre>

✅ Create the materialized view:
<details>
  <summary>Solution</summary>

```
CREATE MATERIALIZED VIEW IF NOT EXISTS 
movies_by_genre_country AS 
  SELECT * FROM movies_by_genre
  WHERE genre IS NOT NULL AND country IS NOT NULL
    AND title IS NOT NULL AND year IS NOT NULL
PRIMARY KEY ((genre, country), year, title)
WITH CLUSTERING ORDER BY (year DESC, title ASC);
```

</details>

<br/>

✅ Retrieve movies from the base table and materialized view:
<details>
  <summary>Solution</summary>

```
SELECT * FROM movies_by_genre;
SELECT * FROM movies_by_genre_country;
```

</details>

<br/>

✅ Delete the *Alice in Wonderland* movie from the base table:
<details>
  <summary>Solution</summary>

```
DELETE FROM movies_by_genre
WHERE title = 'Alice in Wonderland' AND year = 2010
  AND genre IN ('Fantasy','Adventure');

SELECT * FROM movies_by_genre;
SELECT * FROM movies_by_genre_country;
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

