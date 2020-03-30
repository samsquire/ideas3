# An Extra 100 Ideas for Computing

Some ideas I thought of that I enjoyed thinking about and writing down.

* [100 Ideas for Computing](https://github.com/samsquire/ideas)
* [Another 85+ Ideas for Computing](https://github.com/samsquire/ideas2)

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

# 9. Self perpetuating desktop

Without downloading additional packages, a Linux distribution that can also run as a continuous integration server and build server. This means that the desktop can build .ISOs to distribute itself.

# 10. Time based paging

When making API calls, track the amount of time it takes to receive 0.3 seconds worth of items and return that many items.

# 11. Timeline budgeting

A way of adding a budget to each request that is track resource budget usage with request. For example, if you have a budget of each request must take 100 milliseconds, this budget will tell you when you go over the budget and why you went over the budget.

# 12. Class sharing - ontologic class sharing

The unit of sharing in programming is quite large. It's rare that just a single class or set of classes is shared. I propose we make classes shareable. I would like rich class hierarchies to be shared to share models of how things work. I propose a Forum class and a Network class which are classes of how forums work and how Networks work.

# 13. Peer optimizable software

Software that is modular and written at a high level of abstraction can be optimized at the stage of application. I imagine a software viewer which lets users see the decisions made by a piece of software, such as architecture and queries made.

# 14. Distributed transaction protocol with IRC

Use IRC to lock resources in a microservice architecture.

```
initiator: g393 LOCK users orders deliveries
initiator: g393 update users set last_use = date.now()
userservice: g393 ok initiator g393 insert into orders (user_id, product, qty) values (20, "Schlongs", 10) returning id orderservice: g393 ok
initiator: insert into deliveries (user_id, order_number, address) values (20, 10, "120 pemwinkle drive, birmingham, uk")
deliveriesservice: g393 ok
iniator g393 COMMIT
userservice: g393 done
orderservice: g393 done
deliveriesservice: g393 done
```

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
