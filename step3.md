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
 <a href='command:katapod.loadPage?[{"step":"step2"}]' 
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 3 of 8</span>
 <a href='command:katapod.loadPage?[{"step":"step4"}]' 
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">Find information about the cluster and start the CQL shell</div>

✅ Use `nodetool` to find information about the cluster:
```
docker exec -i -t Cassandra-1 bash -c 'nodetool status'
```

Notice that we have:
- two nodes in the cluster
- two datacenters named *DC-London* and *DC-Paris*
- one node in each datacenter

✅ Start the CQL shell:
```
cqlsh
```

Notice that, in this example, `cqlsh` connects to the node in *DC-London* using default `localhost:9042`. The node in *DC-Paris* can be connected to by running command `cqlsh localhost 9043`.

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"step2"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
 <a href='command:katapod.loadPage?[{"step":"step4"}]'
    class="btn btn-dark navigation-bottom-right">Next ➡️
  </a>
</div>
