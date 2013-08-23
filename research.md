---
layout: global
title: Research
type: "page singular"
navigation:
  weight: 6
  show: true
---
<h2>Spark Research</h2>

<p>
Spark started as a research project at UC Berkeley in the <a href="https://amplab.cs.berkeley.edu">AMPLab</a>, which focuses on big data analytics.
</p>

<p class="noskip">
Our goal was to design a programming model that supports a much wider class of applications than MapReduce, while maintaining its automatic fault tolerance. In particular, MapReduce is inefficient for <em>multi-pass</em> applications that require low-latency data sharing across multiple parallel operations. These applications are quite common in analytics, and include:
</p>

<ul>
  <li><em>Iterative algorithms</em>, including many machine learning algorithms and graph algorithms like PageRank.</li>
  <li><em>Interactive data mining</em>, where a user would like to load data into RAM across a cluster and query it repeatedly.</li>
  <li><em>OLAP reports</em> that run multiple aggregation queries on the same data.</li>
</ul>

<p>
MapReduce and Dryad are suboptimal for these applications because they are based on acyclic data flow: an application has to run as a series of distinct jobs, each of which reads data from stable storage (e.g. a distributed file system) and writes it back to stable storage. They incur significant cost loading the data on each step and writing it back to replicated storage.
</p>

<p>
Spark offers an abstraction called <a href="http://www.cs.berkeley.edu/~matei/papers/2012/nsdi_spark.pdf"><em>resilient distributed datasets (RDDs)</em></a> to support these applications efficiently. RDDs can be stored in memory between queries <em>without</em> requiring replication.  Instead, they rebuild lost data on failure using <em>lineage</em>: each RDD remembers how it was built from other datasets (by transformations like <em>map</em>, <em>join</em> or <em>group-by</em>) to rebuild itself.  RDDs allow Spark to outperform existing models by up to 100x in multi-pass analytics. We showed that RDDs can support a wide variety of iterative algorithms, as well as interactive data mining and a highly efficient SQL engine (the <a href="http://shark.cs.berkeley.edu">Shark</a> project).
</p>

<p class="noskip">You can find more about the research behind Spark in our papers:</p>

<ul>
  <li>
    <a href="http://www.eecs.berkeley.edu/Pubs/TechRpts/2012/EECS-2012-214.pdf">Shark: SQL and Rich Analytics at Scale</a>. Reynold Xin, Joshua Rosen, Matei Zaharia, Michael J. Franklin, Scott Shenker, Ion Stoica. <em>Technical Report UCB/EECS-2012-214</em>. November 2012.
  </li>
  <li>
    <a href="http://www.cs.berkeley.edu/~matei/papers/2012/hotcloud_spark_streaming.pdf">Discretized Streams: An Efficient and Fault-Tolerant Model for Stream Processing on Large Clusters</a>.  Matei Zaharia, Tathagata Das, Haoyuan Li, Scott Shenker, Ion Stoica. <em>HotCloud 2012</em>. June 2012.
  </li>
  <li>
    <a href="http://www.cs.berkeley.edu/~matei/papers/2012/sigmod_shark_demo.pdf">Shark: Fast Data Analysis Using Coarse-grained Distributed Memory</a> (demo). Cliff Engle, Antonio Lupher, Reynold Xin, Matei Zaharia, Haoyuan Li, Scott Shenker, Ion Stoica. <em>SIGMOD 2012</em>. May 2012. <b>Best Demo Award</b>.
  </li>
  <li>
    <a href="http://www.cs.berkeley.edu/~matei/papers/2012/nsdi_spark.pdf">Resilient Distributed Datasets: A Fault-Tolerant Abstraction for In-Memory Cluster Computing</a>.  Matei Zaharia, Mosharaf Chowdhury, Tathagata Das, Ankur Dave, Justin Ma, Murphy McCauley, Michael J. Franklin, Scott Shenker, Ion Stoica. <em>NSDI 2012</em>. April 2012. <b>Best Paper Award</b> and <b>Honorable Mention for Community Award</b>.
  </li>
  <li>
    <a href="http://www.cs.berkeley.edu/~matei/papers/2011/tr_spark.pdf">Resilient Distributed Datasets: A Fault-Tolerant Abstraction for In-Memory Cluster Computing</a>.  Matei Zaharia, Mosharaf Chowdhury, Tathagata Das, Ankur Dave, Justin Ma, Murphy McCauley, Michael J. Franklin, Scott Shenker, Ion Stoica. <em>Technical Report UCB/EECS-2011-82</em>.  July 2011.</li>
  <li>
    <a href="http://www.cs.berkeley.edu/~matei/papers/2010/hotcloud_spark.pdf">Spark: Cluster Computing with Working Sets</a>. Matei Zaharia, Mosharaf Chowdhury, Michael J. Franklin, Scott Shenker, Ion Stoica. <em>HotCloud 2010</em>. June 2010.
  </li>
</ul>