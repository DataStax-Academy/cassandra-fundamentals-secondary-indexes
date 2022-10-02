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
 <a href='command:katapod.loadPage?[{"step":"step7"}]'
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 8 of 10</span>
 <a href='command:katapod.loadPage?[{"step":"step9"}]'
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">Using a SASI with the LIKE operator</div>

Finally, let's create an SSTable-attached secondary index on column `user_location` of type `TEXT` to 
see how the `LIKE` operator can be used.  

✅ Create the SASI:
```
CREATE CUSTOM INDEX IF NOT EXISTS 
   user_location_ratings_by_movie_sasi 
ON ratings_by_movie (user_location)
USING 'org.apache.cassandra.index.sasi.SASIIndex';
```

✅ Retrieve rows for countries starting with **U**: 
```
-- Real-time transactional query
SELECT * FROM ratings_by_movie
WHERE title  = 'Alice in Wonderland'
  AND year   = 2010
  AND user_location LIKE 'U%';
```

```
-- Expensive analytical query
SELECT * FROM ratings_by_movie
WHERE user_location LIKE 'U%';
```

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"step7"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
 <a href='command:katapod.loadPage?[{"step":"step9"}]'
    class="btn btn-dark navigation-bottom-right">Next ➡️
  </a>
</div>

