<!-- TOP -->
<div class="top">
  <img src="https://datastax-academy.github.io/katapod-shared-assets/images/ds-academy-logo.svg" />
  <div class="scenario-title-section">
    <span class="scenario-title">Tunable Consistency and Consistency Levels in Apache Cassandra®</span>
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

<div class="step-title">ONE, TWO, THREE, LOCAL_ONE</div>

Let's experiment with these consistency levels and see why 
they can or cannot be satisfied.
 
✅ Add a row using CL `ONE`:
```
CONSISTENCY ONE;
INSERT INTO users (email, name, age, date_joined) 
VALUES ('joe@datastax.com', 'Joe', 25, '2020-01-01');
```
CL `ONE` was satisfied by one of the two nodes in the cluster.


✅ Add a row using CL `TWO`:
<details>
  <summary>Solution</summary>

```
CONSISTENCY TWO;
INSERT INTO users (email, name, age, date_joined) 
VALUES ('jen@datastax.com', 'Jen', 27, '2020-01-01');
```

CL `TWO` was satisfied by the two nodes in the cluster.

</details>

<br/>

✅ Add a row using CL `THREE`:
<details>
  <summary>Solution</summary>

```
CONSISTENCY THREE;
INSERT INTO users (email, name, age, date_joined) 
VALUES ('art@datastax.com', 'Art', 33, '2020-05-04');
```

CL `THREE` could not be satisfied because the cluster does not have three replicas to respond.

</details>

<br/>

✅ Add a row using CL `LOCAL_ONE`:
<details>
  <summary>Solution</summary>

```
CONSISTENCY LOCAL_ONE;
INSERT INTO users (email, name, age, date_joined) 
VALUES ('jim@datastax.com', 'Jim', 31, '2020-05-07');
```

CL `LOCAL_ONE` was satisfied by the node in our local datacenter *DC-London*.

</details>

<br/>

✅ Retrieve all rows from the table:
```
CONSISTENCY ONE; SELECT * FROM users;
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

