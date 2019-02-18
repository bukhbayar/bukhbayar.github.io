---
layout: post
title:  "Record Linkage aka Fuzzy Matching at Scale"
author: bukhbayar
duration: 9
categories: [ blog ]
image: https://www.dqglobal.com/wp-content/uploads/2011/10/Michael-Smithm.smith@designs.com_-1.png
credit: https://www.dqglobal.com/knowledge-base/fuzzy-matching-software
tags: [ blog, python, spark, azure, databricks, machine-learning, record-linkage, fuzzy-matching ]
---

Record linkage aka fuzzy matching is one of the common problems in many organisations. The problem is simple which organisations are integrating data from various sources which do not have a unique identifier to identify which record is duplicated to which. For example, customers required to use a different system with the same information but they made some mistakes like misspelling their name, leave blank or filling phone number instead of email etc.

There are many different approaches to solve this problem by using different algorithms and techniques. All of them have many strengths and weaknesses. For instance, people were using SOUNDEX in SQL query before Python became popular, but it has many issues and hard to solve. In python, there is many different libraries and algorithms such as dedupe, jellyfish and record-linkage. Based on my experience, record-linkage might one of the good approaches because it use a combination of many algorithms and applied machine learning algorithm with supervised and unsupervised learning methods.

However, Record Linkage library only supports and built on top of the python Panda data frame which has some limitation in big data. Spark data frame API does not fully support python Panda data frame, and it only stays in driver of the spark cluster. In general, most of the fuzzy matching solutions require more resource and more power because of many potential combinations. Luckily, I found and inspired by a talk at the Spark Summit where Edward Pantridge and Nicholas Chammas were sharing their solution called Splynkr 3. It was their internal application that solves almost the same problem. Splynkr 3 might be a big application and solving many things, but I simplified this solution based on my actual problem.

Sark

Depending on the amount of data that you working, you can choose to use a python library called RecordLinkage or spark.
Unfortunatly, we do not have 3rd pary library in spark which is why I develop from scratch.

```python
from pyspark.sql import Row
from pyspark.sql.types import StructField, StructType, IntegerType, StringType, FloatType
from pyspark.sql.functions import udf, col, struct, regexp_replace, lower, substring, when
import jellyfish
from graphframes import GraphFrame
```