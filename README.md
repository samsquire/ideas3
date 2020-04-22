# An Extra 100 Ideas for Computing

Some ideas for computers I thought of that I enjoyed thinking about and writing down.

* [Follow me on Twitter](http://twitter.com/mrsamuelsquire)
* The first page of this series [100 Ideas for Computing](https://github.com/samsquire/ideas)
* The second page of this series [Another 85+ Ideas for Computing](https://github.com/samsquire/ideas2)

# 1. Community Idea: Peer naming

Reading code that uses awful names is painful. We could improve the code we write by collecting peer contributed and voted names.

# 2. Ultra monolith

A web based framework codebase that everyone shares the same codebase for. Allows optimisations by people to benefit everyone simultaneously.

# 3. Nested search

Applications advertise that they can be searched. When you activate the system wide search, a subquery is made for each application. So on Android, a search for an application that is not installed will create a query onto the Play store amongst a web search with the browser.

# 4. Search Integrated Programming Language

A langauge with search built-in: any use of an undefined symbol causes a lookup request to a server that monitors library packages for exports. When a symbol is found, it is downloaded for the system for use as library code.

See [importless lang for a proof of concept with Python](https://github.com/samsquire/importless-lang)

# 5. Forum powered desktop

A [deep lever](https://github.com/samsquire/ideas2#99-deep-lever--testing-in-the-field) into desktop applications that is powered by a web forum.

# 6. Bandwidth chargers

Billing for users of bandwidth from services like AWS. So open source projects could create high data transfer services.

# 7. Visual re-flow invalidation

Not all layers of a GUI need to re-drawn during a layout change. This idea is to visually map physical regions on the screen to code blocks. If there's no change to the code of these blocks, the divider doesn't need to be re-rendered.

# 8. Flat HTML

Write HTML with a flat data structure to avoid nested editing and to stream data more efficiently.

See my repository https://github.com/samsquire/flat-html

![form-streaming](flat-form-streaming.png)

# 9. Self perpetuating desktop

Without downloading additional packages, a Linux distribution that can also run as a continuous integration server and build server. This means that the desktop can build .ISOs to distribute itself. The desktop can also build any package that is available in package repositories.

# 10. Time based paging

When making API calls, track the amount of time it takes to receive 0.3 seconds worth of items and return that many items.

# 11. Timeline budgeting

A way of adding a budget to each request that is track resource budget usage with request. For example, if you have a budget of each request must take 100 milliseconds, this budget will tell you when you go over the budget and why you went over the budget.

An identifier that is appended to every request log entry and message headers to show the current budgeted amount used and deadline, like a TTL.

# 12. Class sharing - ontologic class sharing

The unit of sharing in programming is quite large. It's rare that just a single class or set of classes is shared. I propose we make classes shareable. I would like rich class hierarchies to be shared to share models of how things work. I propose a Forum class and a Network class which are classes of how forums work and how Networks work.

# 13. Peer optimizable software

How can software be written so that other people can optimize it? This idea is so that I can write my software once and get performance optimisations from random people on the internet days after writing it. How do you write optimizable software? Some ways of writing self-optimizable software I can think of are:

* Reify (make concrete) technical decisions explicitly as modules in the system and provide a way to map between technical decisions
* Invert the control of the software so that the software is called by framework rather than as a library.
* Create interfaces that support usage in different ways
* Intent written code

The following are optimisations that can be reified.

 * Change synchronous to asynchronous
 * Change asynchronous to synchronous
 * Partition the problem
 * Run a function in parallel
 * Run in a thread
 * Map reduce
 * Distribute between threads
 * Distribute across machines
 * Stream
 * Buffer
 * Execute as a vector (SIMD)
 * Index
 * Queue
 * Send asap and flush
 * Flow control

Software that is modular and written at a high level of abstraction can be optimized. I imagine a software viewer which lets users see the decisions made by a piece of software, such as architecture and queries made.

# 14. Distributed transaction protocol with IRC

Use IRC to lock resources in a microservice architecture.

```
initiator: g393 LOCK users orders deliveries
initiator: g393 update users set last_use = date.now()
userservice: g393 ok
initiator: g393 insert into orders (user_id, product, qty) values (20, "Schlongs", 10) returning id orderservice: g393 ok
orderservice: g393 ok
initiator: insert into deliveries (user_id, order_number, address) values (20, 10, "120 pemwinkle drive, birmingham, uk")
deliveriesservice: g393 ok
initiator g393 COMMIT
userservice: g393 done
orderservice: g393 done
deliveriesservice: g393 done
```

# 15. Beautiful Codebases

Imagine if a codebase was like a magazine that you could flick through. Or print out in a glossy book. Each folder has a README and explains its purpose.

# 16. Community Idea: Collaborative optimisation

Database plans and histograms are uploaded to a Twitter of optimization for handmade plan optimisations.

# 17. Query database

A database system that stores queries like stored procedures but uses the plan of the query to optimize data storage format. The queries are analaysed to determine the optimal data structure to make the query fast at reading and writing. The data storage format is optimised to fulfil the stored queries and to meet read and write budgets of the queries.

* The database might decide to store data in column orientated style if a query uses the whole table.
* The database can be automatically sharded for queries like `select * from table where category == "BLAH"` in this scenario, the rows matching "BLAH" can be stored in a different file. I call this particular optimisation table promotion.
* For a join such as `select people.firstname, orders.name from people join orders on people.id = orders.person_id where people.firstname = 'fuz46'` we can store orders by people. If we were using LevelDB, we could store a key "person-1F40-order-0002"
* The database would take consideration of the data structure of queries, if the data to be retrieved has various nested associations, it could choose to use a document orientated storage mode rather than one that uses joins over row based data.

# 18. Non-leaf framework

When we write a request handler in a web framework, with most frameworks we are typically writing functions that are leaf nodes of the stack. This idea is to write a framework where your code is not so lonely, and your code is callback to other parts of the stack.

* Your code is hosted: it is ran with performance testing, timeline budgeting
* Your code implements an interface and has multiple entry points.
* Your code is part of a wider circuit

In most frameworks, it is dubious what the framework does for you.

# 19. Mouseover fetch

Fetch data on mouseover, in the background for perceived performance.

# 20. High latency remote desktop

Imagine a remote computer that has high bandwidth but high latency. The system would be frustrating to use with typical software. Assuming we can edit files locally without high latency. An approach to make this bearable is the following:

 * **Nested Branched Sessions** You cannot work serially with high latency because you depend on the output of the previous step. So instead you work on things in parallel but independently.
 * **Isolated changes**: Make changes to parts of files independent and queue them together. If they both work with tests independently, merge them together.
 * **Success detectors** Write a detector of success, it detects if some thing works. For example, if you're trying to get a Docker image built, you would have a detector for docker image being built that passes some test. You might want to use the output name somewhere, in a future session. You can use a placeholder to do so.
 * **Fuzzy success matchings** If you wrote an output match for success, it is fuzzily matched.
 * **Notifications interface** The key to productivity with a high latency system is that you're always working while the remote machine is working. So we have a strong notifications interface in the browser.

# 21. Call site library

Systems should have a ceremony for calling an external system. I propose a general purpose library external call API:

* **written to a log first**
* **be queuable**
* **be traceable**
* **be retryable**
* **be idempotent**

# 22. Error subsystem and server

Software is tied to an error server with an error subsystem. The error server is:
* responsible for monitoring a codebase for exceptions that could be thrown.
* should have a GUI which acts like a searchable database of errors that can be thrown
* It tracks call sites where errors are possible
* Has a studio component for running simulations of various exceptions that if thrown, what would happen to the system as a whole

In a given piece of software, at startup the error subsystem is loaded with an error specification and the error specifications defines that actions to take if a given request errors.

* Allows the centralised definition of error handlers and what should happen when errors happen while recovering from errors.
* Allows centralised specification of error contingency. 
* Outsource exception handling to the error server.
* Define what should happen while some thing fails while doing some other thing.
* Errors are provided with full context of the initiating request.

# 23. Cache aware programming libraries

It should be possible to write a system that is cache-aware. There is process for loading data into each of the caches in the architecture. Even if its a warm up loop that loads data through the system. There are multiple levels of caches in modern computer systems:

* CPU caches: L1, L2, L3
* File system caches
* Disk firmware caches
* Network buffer caches

# 24. Personal Knowledge subsystem

A personal knowledgebase of things learned.

# 25. Surface programming

There's few digital equivalent of the place prepositions of putting some thing on top of another in computing - except maybe Docker files. When we talk of tech stacks, we build on top of other things by using and depending on. There could be an interface of a surface and things placed on top of the surface act in a certain way. A surface offers a promise for things placed upon it. Like a game engine, objects in the engine obey the laws of the engine.

Some surfaces I'd like to rest my code upon:

 * **Function scaling** A large grid where any function placed in the grid is deployed and scaled.
 
 A surface is a precanned environment where every thing has already been set up for you to use and has a surface to place things on top of.

# 26. Title sparklines

A user surfaceable measurement that is displayed when there is a progress bar and when an application is busy. It shows the throughput per unit time that some thing is taking. Perhaps copying files or a network connection or network transfer. It can show in the titlebar. There should always be a throughput number for reference and comparison.

# 27. Has-a queries

Define what should be on a web page by making various 'has a' declarations which specify what components should be rendered on the page. Let additive guis handle the layout.

```
contactsPage hasA contactUsForm
contactUsForm hasA field:email
contactUsForm hasA textarea:body
```

Components have data dependencies which get automatically ran to populate data for them.

# 

# For loops flow control

# Incomplete thoughts and ideas 
Function Mesh

# Visual paging

# Latency language

Place data in different boxes.

# Data suction

Flow control

# Notes

literate programming story introduce test case all together

Things written as communication protocols are easier to program and reason about. Concurrency too (see go and occam pi)
Turn the GUI into a communication problem.

Permutations and validity.

A data structure that represents a forum or a blog that can be rendered into a CRUD app.
