# BigQuery
## Introduction
## Like SQL
## But with arrays and structures
# Example using BigQuery and DataFusion from GCP
## What is it about? Example description
## Problem description
## Suggested solution

----
## Introduction

en:

* Analyze petabytes of data using ANSI SQL at blazing-fast speeds, with zero operational overhead

* Run analytics at scale with 26%–34% lower three-year TCO than cloud data warehouse alternatives

* Democratize insights with a trusted and more secure platform that scales with your needs

* Gain insights from data across clouds with a flexible, multi-cloud analytics solution

de:

* Mit ANSI SQL unglaublich schnell und ohne operativen Aufwand Petabyte an Daten analysieren
* Umfangreiche Analysen im Vergleich zu anderen Cloud Data Warehouses mit 26 bis 34 % niedrigeren Gesamtbetriebskosten über drei Jahre ausführen
* Informationen mit einer zuverlässigen und sicheren Plattform, die sich Ihren Anforderungen anpasst, allgemein verfügbar machen
* Mit einer flexiblen Multi-Cloud-Analyselösung Informationen aus Daten in verschiedenen Clouds gewinnen 

## Like SQL

```
SELECT p.visitorId, v.name, v.age FROM `six20-298609.example1.purchase` AS p
JOIN `six20-298609.example1.visitor` AS v ON v.visitorId=p.visitorId
```

but noSQL (SAVE RESULTS)

```
SELECT v.name, v.age, basket FROM `six20-298609.example1.purchase` AS p
JOIN `six20-298609.example1.visitor` AS v ON v.visitorId=p.visitorId
```

```
SELECT p.visitorId, v.name, v.age, b.product, b.quantity FROM `six20-298609.example1.purchase` AS p
JOIN `six20-298609.example1.visitor` AS v ON v.visitorId=p.visitorId,
UNNEST(p.basket) AS b
```

## But with arrays and structures
Anzahl der Produkte = menge
```
SELECT
10 as visitorId, 2345 as basketId, ['t-shirt', 'pen', 'milk', 'butter'] AS basket.product, [1,5,1,2] AS basket.quantity
```

```
SELECT visitorId, b.product, b.quantity FROM `six20-298609.example1.purchase`,
UNNEST(basket) AS b
```
