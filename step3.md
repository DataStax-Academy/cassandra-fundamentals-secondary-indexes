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
 <a href='command:katapod.loadPage?[{"step":"step2"}]' 
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 3 of 10</span>
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
CREATE KEYSPACE ks_indexes
WITH replication = {
  'class': 'NetworkTopologyStrategy', 
  'DC-Houston': 1 };
```

✅ Create and populate the tables:
```
USE ks_indexes;

CREATE TABLE users (
  email TEXT,
  name TEXT,
  age INT,
  location TEXT,
  PRIMARY KEY ((email))
);
INSERT INTO users (email, name, age, location) 
VALUES ('joe@datastax.com', 'Joe', 25, 'USA');
INSERT INTO users (email, name, age, location) 
VALUES ('jen@datastax.com', 'Jen', 27, 'UK');
INSERT INTO users (email, name, age, location) 
VALUES ('jim@datastax.com', 'Jim', 31, 'Canada');
INSERT INTO users (email, name, age, location) 
VALUES ('jon@datastax.com', 'Jon', 25, 'Mexico');
INSERT INTO users (email, name, age, location) 
VALUES ('job@datastax.com', 'Job', 40, 'Japan');
INSERT INTO users (email, name, age, location) 
VALUES ('joy@datastax.com', 'Joy', 40, 'Brazil');
SELECT * FROM users;

CREATE TABLE ratings_by_movie (
  title TEXT,
  year INT,
  email TEXT,
  rating INT,
  date_rated DATE,
  user_location TEXT,
  PRIMARY KEY ((title, year), email)
);
INSERT INTO ratings_by_movie (title, year, email, rating, date_rated, user_location) 
VALUES ('Alice in Wonderland', 2010, 'joe@datastax.com', 9, '2020-05-10', 'USA');
INSERT INTO ratings_by_movie (title, year, email, rating, date_rated, user_location) 
VALUES ('Alice in Wonderland', 2010, 'jen@datastax.com', 9, '2020-04-21', 'UK');
INSERT INTO ratings_by_movie (title, year, email, rating, date_rated, user_location) 
VALUES ('Alice in Wonderland', 2010, 'jim@datastax.com', 8, '2020-05-08', 'Canada');
INSERT INTO ratings_by_movie (title, year, email, rating, date_rated, user_location) 
VALUES ('Alice in Wonderland', 2010, 'jon@datastax.com', 4, '2020-06-10', 'Mexico');
INSERT INTO ratings_by_movie (title, year, email, rating, date_rated, user_location) 
VALUES ('Alice in Wonderland', 2010, 'job@datastax.com', 5, '2019-12-11', 'Japan');
INSERT INTO ratings_by_movie (title, year, email, rating, date_rated, user_location) 
VALUES ('Alice in Wonderland', 2010, 'joy@datastax.com', 10, '2020-05-22', 'Brazil');
INSERT INTO ratings_by_movie (title, year, email, rating, date_rated, user_location) 
VALUES ('Alice in Wonderland', 1951, 'joe@datastax.com', 7, '2020-03-01', 'USA');
INSERT INTO ratings_by_movie (title, year, email, rating, date_rated, user_location) 
VALUES ('Alice in Wonderland', 1951, 'jen@datastax.com', 6, '2020-05-17', 'UK');
INSERT INTO ratings_by_movie (title, year, email, rating, date_rated, user_location) 
VALUES ('Alice in Wonderland', 1951, 'joy@datastax.com', 9, '2020-05-10', 'Brazil');
SELECT * FROM ratings_by_movie;
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
