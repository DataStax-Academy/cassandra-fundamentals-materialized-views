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
 <a href='command:katapod.loadPage?[{"step":"step3"}]'
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 4 of 8</span>
 <a href='command:katapod.loadPage?[{"step":"step5"}]' 
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">Create a keyspace and a table</div>

To demonstrate how availability can be affected by different consistency levels, we can create 
a keyspace that prescribes to have more replicas than the number of nodes in the cluster. Let's 
use replication factors `1` and `3` for *DC-London* and *DC-Paris*, respectively. You can think of this 
situation as if we lost two replicas in *DC-Paris* due to a natural disaster ... will we still be able to write and read data?

✅ Create the keyspace:
```
CREATE KEYSPACE IF NOT EXISTS ks_tunable_consistency
WITH replication = {
  'class': 'NetworkTopologyStrategy', 
  'DC-London': 1,
  'DC-Paris': 3 };

USE ks_tunable_consistency;
```

✅ Create the table:
```
CREATE TABLE IF NOT EXISTS users (
  email TEXT,
  name TEXT,
  age INT,
  date_joined DATE,
  PRIMARY KEY ((email))
);
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

