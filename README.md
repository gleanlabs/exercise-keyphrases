# Exercise: keyphrases

Here is a sample set of keyphrases extracted from some documents (fields `keyphrase`, `weight` and `doc_id`):

```scala
("performance", 0.03, 101)
("performance", 0.001, 203)
("Java Just-In-Time compiler", 0.4, 501)
("java just In Time compiler", 0.1, 208)
("Performance", 0.2, 102)
("JAVA JUST-IN-TIME COMPILER", 0.002, 1001)
("Java Just-In-Time compiler", 0.99, 23)
```

## Problem 
Some keyphrases are obviously identical with each other, but spelled slightly differently.
In fact, in the example, there are only two distinct keyphrases: "performance" and "Just-In-Time compiler",
but they contain number of strictly distinct variants.

## Task

Remap the data so that all the *loosely identical* keyphrases become *strictly identical*. Of all the different
spellings, always pick the one which is *the most prevalent*. In the sample data, from the group (performance, Performance)
"performance" is picked, as it appears 2x, while "Performance" only once.

Rules for loose equality:

* case insensitivity, e.g. "JAVA" ~ "java" ~ "Java"
* dash/whitespace, e.g. "just in time" ~ "just-in-time"

So remapping the sample data should result in:

```scala
("performance", 0.03, 101)
("performance", 0.001, 203)
("Java Just-In-Time compiler", 0.4, 501)
("Java Just-In-Time compiler", 0.1, 208)
("performance", 0.2, 102)
("Java Just-In-Time compiler", 0.002, 1001)
("Java Just-In-Time compiler", 0.999, 23)
```

The order of the data doesn't have to be preserved.

## Tools

The task should be solved using Apache Spark.

PySpark is totally fine, Spark solution in Scala will make us even happier.

Use the sample data for unit test(s).

Run the solution on [large set of data](./sample-dataset.tar.gz) and demonstrate how you validated the result.
