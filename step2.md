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
 <a href='command:katapod.loadPage?[{"step":"step1"}]'
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 2 of 8</span>
 <a href='command:katapod.loadPage?[{"step":"step3"}]' 
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">Consistency levels</div>

Every write (`INSERT`, `UPDATE`, `DELETE`) or read (`SELECT`) operation in Cassandra is executed with a *consistency level* (CL), which 
defines how many replicas that are writing or reading data must respond to a request coordinator 
before the coordinator responds to the client. These are the consistency levels we use in our examples.

| Consistency Level | Description |
|------------------------|-------------|
| `ONE`, `TWO`, `THREE`  | One, two and three replicas must respond, respectively |
| `LOCAL_ONE`            | One replica in the local datacenter must respond | 
| `QUORUM`               | A majority (n/2 + 1) of the replicas must respond |
| `LOCAL_QUORUM`         | A majority (n/2 + 1) of the replicas in the local datacenter must respond |
| `EACH_QUORUM`          | A majority (n/2 + 1) of the replicas in each datacenter must respond |

It is important to understand that write operations are always sent to all replicas. The write consistency level 
only controls how many responses the request coordinator waits for before responding to the client.
For read operations, the coordinator generally only issues read requests to enough replicas 
to satisfy the read consistency level. However, if the selected replicas are slow to respond, the read request 
may be forwarded to additional replicas.

Finally, note that there are also CLs `ALL` and `ANY`, which represent the extreme cases. `ALL` requires all replicas to respond and 
`ANY` can be used for writes when either one replica responds or zero replicas respond and the coordinator stores a hint. You should avoid using 
these consistency levels in production. There are also CLs `SERIAL` and `LOCAL_SERIAL` that are used with lightweight transactions.


<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"step1"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
 <a href='command:katapod.loadPage?[{"step":"step3"}]'
    class="btn btn-dark navigation-bottom-right">Next ➡️
  </a>
</div>
