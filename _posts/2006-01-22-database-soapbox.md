---
layout: post
title: 'Database Soapbox'
date: 2006-01-22 21:59
comments: true
categories : []
---  

When doing full joins across multiple tables you need to limit your results with a WHERE clause to reduce the result set to a more manageable size.

For an example: A full join/cross join between three tables that contain 10, 20, and 30 rows, respectively, WOULD return 10x20x30 = 6,000 rows.

So this is bad mkay...

<em>SELECT t1.*, t2.*, t3.* FROM t1, t2, t3;</em>

This isn't....

<em>SELECT t1.*, t2.*, t3.* FROM t1, t2, t3 WHERE t1.i1 = t2.i2 and t3=i3;</em>

So remember to use a WHERE clause kiddoes.

