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
 <a href='command:katapod.loadPage?[{"step":"step6"}]'
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 7 of 8</span>
 <a href='command:katapod.loadPage?[{"step":"step8"}]'
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">QUORUM, LOCAL_QUORUM, EACH_QUORUM</div>

Let's experiment with these consistency levels and see why 
they can or cannot be satisfied.
 
✅ Retrive a row using CL `QUORUM`:
```
CONSISTENCY QUORUM;
SELECT * FROM users WHERE email = 'joe@datastax.com';
```

CL `QUORUM` could not be satisfied because the cluster does not have three (`(1 + 3) / 2 + 1`) replicas to respond.


✅ Retrive a row using CL `LOCAL_QUORUM`:
<details>
  <summary>Solution</summary>

```
CONSISTENCY LOCAL_QUORUM;
SELECT * FROM users WHERE email = 'joe@datastax.com';
```

CL `LOCAL_QUORUM` was satisfied by the only replica in local datacenter *DC-London*. One (`1 / 2 + 1`) response wa required.

</details>

<br/>

✅ Retrive a row using CL `EACH_QUORUM`:
<details>
  <summary>Solution</summary>

```
CONSISTENCY EACH_QUORUM;
SELECT * FROM users WHERE email = 'joe@datastax.com';
```

CL `EACH_QUORUM` could not be satisfied because datacenter *DC-Paris* does not have two (`3 / 2 + 1`) replicas to respond.

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

