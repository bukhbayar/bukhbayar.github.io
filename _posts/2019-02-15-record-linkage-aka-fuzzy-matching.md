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

There are many different approaches to solve this problem by using different algorithms and techniques. All of them has strength and weaknesses. For instance, before python demand, people were using SOUNDEX in SQL query which have many issues. In python, there is many different libraries and algorithms such as dedupe, jellyfish and record-linkage. Based on my experience, record-linkage might one of the good approaches because it use a combination of many algorithms and applied machine learning with supervised and unsupervised methods.

However, my problem was running a record-linkage model in big data. Record Linkage library only supports and built on top of the python panda data frame which has a limitation in big data. Most of the record linkage problem requires more resource and power. After I have done some research, I was inspired by a talk at Spark Summit where Edward Pantridge and Nicholas Chammas were talking about their solution which is Splynkr 3. It was their internal application which was solving the same problem. Splynkr might be big application solving many things, but I simplified this solution based on my actual problem.

Here is the solution: 