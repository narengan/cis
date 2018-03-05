---

copyright:
  years: 2018
  lastupdated: "2018-03-05"

---

# Caching Concepts

This document contains some concepts and definitions related to Caching and how it affects your IBM CIS deployment.

## Caching

Caching is the process of storing static files on our edge servers in order to increase response time. Examples of static files
include image and text files. By default we do not consider HTML file to be static but it is possible to cache them with Page Rules.
Cached files have a specified expiration time, after which they will be purged from the cache. If the need arises it is possible
to manually purge files from the cache. A deeper explaination of the available settings of options can be found on [Caching and Page Rules tutorial](caching-tutorial.html).