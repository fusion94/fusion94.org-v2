---
layout: post
title: "Breadboards in Prototyping"
date: 2012-11-27 11:49
comments: true
categories: [Breadboards, Circuits, Prototyping ]
---

<div class="info">NOTE: This is the first blog post in a series of blog posts on how to build electronic circuits. If you're at all
interested then please subscribe to the RSS feed.</div>

What is a [solderless breadboard](http://en.wikipedia.org/wiki/Breadboard) and why would you want one? Solderless
breadboards, or just breadboards for short, are handy little boards that make prototyping significantly easier. You
can insert most electronic components as well as add wire to connect these various components. Often you will want
to make a more permanent version later (generally called a Printed Circuit Board or PCB), but sometimes you want
your project to be easily modifiable or maybe your breadboard is just the right size for your project. Either way
breadboards make wiring up, testing, fixing, retesting, and using your very own circuits easy and convenient.
<!-- more -->
> So basically a  breadboard is used to make up temporary circuits for testing or to try out an idea. No soldering
is required so it is easy to change connections and replace components. Parts will not be damaged so they will be
available to re-use afterwards.

Most electronic components in electronic circuits can be interconnected by inserting their leads or terminals into
the holes and then making connections through wires where appropriate. The breadboard has strips of metal underneath
the board and connect the holes on the top of the board. The metal strips are laid out as shown below. Note that the
top and bottom rows of holes are connected horizontally and split in the middle while the remaining holes are
connected vertically.

![](/images/blog/breadboard/breadboard_1.jpg)

Note how all holes in the selected row are connected together, so the holes in the selected column. The set of
connected holes can be called a node:

![](/images/blog/breadboard/breadboard_2.jpg)

To interconnect the selected row (node A) and column (node B) a cable going from any hole in the row to any hole
in the column is needed:

![](/images/blog/breadboard/breadboard_3.jpg)

Now the selected column (node B) and row (node A) are interconnected:

![](/images/blog/breadboard/breadboard_4.jpg)
