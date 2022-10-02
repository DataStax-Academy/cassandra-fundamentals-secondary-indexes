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
 <a href='command:katapod.loadPage?[{"step":"step2"}]' 
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 3 of 8</span>
 <a href='command:katapod.loadPage?[{"step":"step4"}]' 
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">Create a keyspace and tables</div>

✅ Start the CQL shell:
```
cqlsh
```

✅ Create the keyspace:
```
CREATE KEYSPACE killr_video
WITH replication = {
  'class': 'NetworkTopologyStrategy', 
  'DC-Houston': 1 };
```

✅ Create and populate the tables:
```
USE killr_video;

CREATE TABLE users (
  email TEXT,
  name TEXT,
  age INT,
  date_joined DATE,
  PRIMARY KEY ((email))
);
INSERT INTO users (email, name, age, date_joined) 
VALUES ('joe@datastax.com', 'Joe', 25, '2020-01-01');
INSERT INTO users (email, name, age, date_joined) 
VALUES ('jen@datastax.com', 'Jen', 27, '2020-01-01');
INSERT INTO users (email, name, age, date_joined) 
VALUES ('jim@datastax.com', 'Jim', 31, '2020-05-07');
SELECT * FROM users;

CREATE TABLE movies_by_genre (
  genre TEXT,
  title TEXT,
  year INT,
  duration INT,
  avg_rating FLOAT,
  country TEXT,
  PRIMARY KEY ((genre), title, year)
);
INSERT INTO movies_by_genre (genre, title, year, duration, avg_rating, country) 
VALUES ('Fantasy', 'Alice in Wonderland', 2010, 108, 8.33, 'USA');
INSERT INTO movies_by_genre (genre, title, year, duration, avg_rating, country) 
VALUES ('Adventure', 'Alice in Wonderland', 2010, 108, 8.33, 'USA');
INSERT INTO movies_by_genre (genre, title, year, duration, avg_rating, country) 
VALUES ('Adventure', 'The Extraordinary Adventures of Adele Blanc-Sec', 2010, 107, 6.30, 'France');
INSERT INTO movies_by_genre (genre, title, year, duration, avg_rating, country) 
VALUES ('Action', 'The Extraordinary Adventures of Adele Blanc-Sec', 2010, 107, 6.30, 'France');
INSERT INTO movies_by_genre (genre, title, year, duration, avg_rating, country) 
VALUES ('Adventure', 'How to Train Your Dragon', 2010, 98, 8.10, 'USA');
SELECT * FROM movies_by_genre;
```

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"step2"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
 <a href='command:katapod.loadPage?[{"step":"step4"}]'
    class="btn btn-dark navigation-bottom-right">Next ➡️
  </a>
</div>
