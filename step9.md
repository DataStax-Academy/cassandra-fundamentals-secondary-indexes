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
 <a href='command:katapod.loadPage?[{"step":"step8"}]'
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 9 of 10</span>
 <a href='command:katapod.loadPage?[{"step":"step10"}]'
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">Dropping secondary indexes</div>

We certainly went overboard by creating five secondary indexes for one table. Here is how to use the `DROP INDEX` statement 
to remove indexes.

Drop these three indexes:
```
DROP INDEX rating_ratings_by_movie_2i;
DROP INDEX rating_ratings_by_movie_sasi;
DROP INDEX user_location_ratings_by_movie_sasi;
```

Drop the remaining two indexes:
<details>
  <summary>Solution</summary>

```
DROP INDEX date_rated_ratings_by_movie_2i;
DROP INDEX date_rated_ratings_by_movie_sasi;
```

</details>

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"step8"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
 <a href='command:katapod.loadPage?[{"step":"step10"}]'
    class="btn btn-dark navigation-bottom-right">Next ➡️
  </a>
</div>

