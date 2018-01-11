---
title: Welcome
layout: docs
---
<style>
.row {
    display: flex;
    flex-flow: row wrap;
    justify-content: space-evenly;
}

.cell {
    display: flex;
    width: 300px;
}

.card {
  width: 100%;
  padding: 25px;
  border: 1px solid transparent;

  text-align: center;
  text-decoration: none;
  font-family: "Open Sans", sans-serif;
}

.card:hover {
  border: 1px solid #3583d6;
  border-radius: .5rem;
}

.card .card-title {
  font-weight: 600;
  font-size: 2rem;
  color: #3583d6;
}

.card .card-icon {
  font-size: 64px;
  padding: 10px;
}

</style>
<div class="row">
   <div class="cell">
   {% include clickable-card.html link="/" title="Getting Started" description="Get a quick overview of Apptuit’s capabilities" ico="rocket" %}
   </div>
   <div class="cell">
   {% include clickable-card.html link="/xcollector" title="XCollector" description="Install &amp; configure the Agent to collect data" ico="xing" %}
   </div>
   <div class="cell">
   {% include clickable-card.html link="/" title="Queries" description="Learn how to query your data" ico="search" %}
   </div>
   <div class="cell">
   {% include clickable-card.html link="/" title="Graphing" description="Visualize your data to gain insight" ico="area-chart" %}
   </div>
   <div class="cell">
   {% include clickable-card.html link="/" title="Alerting" description="Create &amp; manage your monitors &amp; notifications" ico="exclamation-circle" %}
   </div>
   <div class="cell">
   {% include clickable-card.html link="/" title="Admin" description="Invite your team &amp; manage user accounts" ico="users" %}
   </div>
</div>
