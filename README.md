# An Extra 100 Ideas for Computing (In progress)

Some ideas for computers I thought of that I enjoyed thinking about and writing down. This page is unfinished. Please see the other complete pages of the series. This page changes frequently as I add to it.

* [Follow me on Twitter](http://twitter.com/mrsamuelsquire)
* The first page of this series [100 Ideas for Computing](https://github.com/samsquire/ideas)
* The second page of this series [Another 85+ Ideas for Computing](https://github.com/samsquire/ideas2)

Themes:

* global deduplication of effort
* software breakage no-more

# 1. Community Idea: Peer naming

Reading code that uses awful names is painful. We could improve the code we write by collecting peer contributed and voted names.

# 2. Ultra monolith

A web based framework codebase that everyone shares the same codebase for. Allows optimisations by people to benefit everyone simultaneously.

# 3. Nested search

Applications advertise that they can be searched. When you activate the system wide search, a subquery is made for each application. So on Android, a search for an application that is not installed will create a query onto the Play store amongst a web search with the browser.

# 4. Search Integrated Programming Language

A language with search built-in: any use of an undefined symbol causes a lookup request to a server that monitors library packages for exports. When a symbol is found, it is downloaded for the system for use as library code.

See [importless lang for a proof of concept with Python](https://github.com/samsquire/importless-lang)

# 5. Forum powered desktop

A desktop distribution of Linux that has a a [deep lever](https://github.com/samsquire/ideas2#99-deep-lever--action-at-distance) into a web forum. Translations and GUIs are rendered in the web forum and people vote on layouts.

# 6. Bandwidth chargers

Billing for users of bandwidth from services like AWS. So open source projects could create high data transfer services.

# 7. Rendering engine asset detection

Rendering engines throw a lot of content away. I wonder if some content can be recognised as being static, as unchanging and re-used between frames. Or If there's a list of thousand items, is it possible to recognise that the content of each list item is static and the only thing that changes is the ordering. So all that's needed is rendering cached bitmaps in a unique ordering.

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
initiator: g393 insert into orders (user_id, product, qty) values (20, "Schlongs", 10) returning id
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

When we write a request handler in a web framework, with most frameworks we are typically writing functions that are leaf nodes of the stack. They just call into the framework. This idea is to write a framework where your code is not so lonely and your code's output is used by other parts of the stack.

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
 * **Notifications interface** The key to productivity with a high latency system is that you're always working while the remote machine is working. So we have a notifications interface that lets you create a session from a notification of completedness.

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
* Has a studio component for running simulations of various exceptions that if thrown, run what-if scenarios against the system as a whole
* Allows you to define error handling later, when the error is better understood.

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

There's few digital equivalent of the place prepositions of putting some thing on top of another in computing - except maybe Docker files or layered architectures. When we talk of tech stacks, we build on top of other things by using and depending on. There could be an interface of a surface and things placed on top of the surface act in a certain way. A surface offers a promise for things placed upon it. Like a game engine, objects in the engine obey the laws of the engine.

Some surfaces I'd like to rest my code upon:

 * **Function scaling** A large grid where any function placed in the grid is deployed and scaled.
 
 A surface is a precanned environment where every thing has already been set up for you to use and has a surface to place things on top of.

# 26. Title sparklines

A user surfaceable measurement that is displayed when there is a progress bar and when an application is busy. It shows the throughput per unit time that some thing is taking. Perhaps copying files or a network connection or network transfer. It can show in the titlebar. There should always be a visible throughput number for reference and comparison.

# 27. Has-a queries

Define what should be on a web page by making various 'has a' declarations which specify what components should be rendered on the page. 

```
contactsPage is page
standardLayout hasA logo
contactsPage hasThingsFrom standardLayout
contactsPage hasA contactUsForm
contactUsForm hasA field:email
contactUsForm hasA textarea:body
```

Components have data dependencies which causes data queries to automatically populate data for them.

# 28. Accelerated mode, temporary write safety off

When you're reasonably sure that the software won't crash and the power won't go out. The ability to scale down write safety settings at run time for accelerated performance. Currently this requires restarts for most software.

 * Postgres, `synchronous_commit`, `fsync` settings

# 29. Per-server request log

When a request is received, serialize the request and write it to the machine readable log in the background. Do not acknowledge success until it is written to the per-server log. Aggregate the per-server write ahead logs every few minutes.

# 30. Algorithm servers

With [configurable imports](https://github.com/samsquire/ideas2#96-data-structure-configurer), we can have telemetry about what algorithms people are requesting. We can have a Leetcode style website where people's solutions compete and implement requested algorithms for different constraints. We know what's in demand. 

For data that is not private, we can automatically upload data that is running through various algorithms and this can be uploaded to the algorithm server. People can solve challenges for different variations of the same problem to make things faster.

The goal of this idea is that there is a public interchange where you can see live algorithms running against live data, like a fusebox. People can submit code and optimizations to the public interchange to benefit everybody at once.

![](markus-spiske-kK7uPfb2YWU-unsplash.jpg)
Photo by [Markus Spiske](https://unsplash.com/photos/kK7uPfb2YWU) on Unsplash

# 31. API usage telemetry

When an API is used, the usage of the API is reported to the API developers so they know if they will break any consumer.

This could be accomplished by using a code coverage tool to trace calls to APIs.

# 32. Naive is correct

The naive way of doing some thing should be the correct way to do it. Optimisations behind the scenes can do things efficiently.

For example, there is a natural paging size for each object in your system. For a GUI component it might be how many items can be displayed efficiently.

* **JSON Paging** Imagine you have an application with buttons and the buttons load data that could possibly be millions of records, I should be able to write my code as if it is very naive and all the data fits in memory, even if it doesn't. Before the GUI code is scheduled to run, the plumbing should automatically make paged requests to the server.

# 33. Person stack

Distill a tech stack into those people responsible and who worked on it to buy them all beer or support them via patronage.

Depending on a library or piece of software is to depend on a chain of people and organisations (that map to people). These people should be rewarded. Think of this idea as an index

# 34. Community Idea: Talk with code

A community where every reply is a piece of code. You must express your reply as code.

# 35. MRSGREN

A digital organism, such that each phone is a node in a network of people that work together to fulfil some common goal. The organism software has a menu system that looks like the following:

* **Move** To physical move assets around, To take up some kind of position in the world
* **Respire** Controlled burning of resources, such as constructing new things or commanding work to be done
* **Sensing** seeing, information gathering 
* **Growth** Advertising
* **Reproduction** Information needed to create additional nodes
* **Excretion** Cleaning up
* **Nutrition** Acquring resources and new people.

# 36. Person Coordination API

Each person in an organisation might want to control digitally how information is retrieved and goes through to them. I propose people define an API for themselves in how to get them to do what you want them to do.  I offer a number of services, and this is the information I require.

# 37. Data Flows and queries per widget

Generate GUI data population with a data flow description of the GUI. For example, in an email client, emails flow into folders, when folders are clicked change the email list which when clicked flows into the mail preview.

Alternatively, each click changes the query of the widgets on the screen. Clicking an email folder changes the results that are in the mail list.

# 38. Built in desktop Queue

# 39. Built to cluster with others

Each installation of a desktop environment is a set of resources that could be shared.

# 40. Text zoom

Text can be folded and made it so that more is available at a different zoom level.

```
<document>
<text level="1">I am visible at zoom level 1. <text level="2">I'm visible at zoom level 2</text></text>
</document>
```

# 41. Library Router

![](john-barkiple-l090uFWoPaI-unsplash.jpg)
Photo by John Barkiple on Unsplash

Imagine a language where you import a list of all the actual OS system calls you want to make. But you don't necessarily wire up call sites at this time. Usually OS API calls are called with a pointer to a struct and a return value is important. Think of it as a wire that comes out of the OS and into user space. At some point, user space wants to make another OS system call, as a result of some logic, so it makes another system call. This is a wire that goes back into the OS, using some of the original system call as arguments.

Now imagine if sequences of OS system calls could be grouped together to indicate that the sequence of API calls will always happen together. Some of the call sites can be generated. With library routing, we can define a pattern of an application once, and provide convenient places to place user logic. Code Autowire is given a list of API calls, and calculates the arguments that are common to them and generate code to thread the arguments together.

An example is:

```
getaddrinfo();
int socket = socket();
bind(socket);
listen(socket);
accept(socket);
```



# 42. User simulation caching

If we know it takes 100ms to render a page in our app, we could simulate an average journey for a user and cache the responses for performance.

# 43. Digital Ghostwriter

When you write client or server side code, it would be nice if the other side wrote itself automatically. This idea is for a digital ghostwriter to generate code for an equivalent clientside.

* If you wrote readInt, in the  client code a sendInt would be written. If you wrote sendInt, the other side would write readInt.
* If you write window.fetch("/data/blah") then a request handler for blah would be generated.

# 44. Instant signup

Browsers could cache your user data according to some browser defined API, first name, last name, email address, generated password. Without prefilling a form, you could sign up and have an account immediately.

# 45. Community Idea: Ideological match up

There's somewhere someone that thinks exactly like you on all matters. Let's uses quizes and questionnaires to make them easy to find.

I propose a statement is shown and you say whether you agree or disagree with it. And you can specify clauses that you apply to the statement.

I see a synergy with [1. Digital contracts](https://github.com/samsquire/ideas2/blob/master/README.md#1-digital-contracts), the [Person Coordination API](https://github.com/samsquire/ideas3#36-person-coordination-api) and the [World splitting app](https://github.com/samsquire/ideas2/blob/master/README.md#43-world-splitting-app) whereby people come to agreements through digital means.

The website would provide a community area for users that match up.

[Identikit](https://github.com/samsquire/identikit) is my project that attempts to represent people's stances in a compact format.

# 46. Business Skeletons

A think tank sole purpose is to churn out business strategies which are a combination of job descriptions, operational manuals and business plans.

# 47. Non-core business wrapped instruments

Companies are obliged to raise profits for their shareholders. Stakeholder capitalism means companies must also consider the demands of local communities, suppliers and employees. There are many demands on companies nowadays.

One cannot serve two masters: the shareholders and everybody else.

I propose a financial instrument to solve the problem, I call a non-core business wrapped instrument which is software and labour combined together. There's a digital marketplace that has a catalogue of products which are things like environmental friendliness or customer service.

A company can buy one of these assets and outsource customer service or environmental friendliness on the market of digital labour.

# 48. Request Priming

Continue processing requests before fsync is received but create everything in a pending state. Send an additional signal when fsync is received to activate pending requests.

# 49. Invisible union

A secret technology union for programmers and people in the computer industry. Run neural networks on salary data of members to calculate best combination to get a higher salary. Members share all communication of their employer with the union for group negotiation expertise recommendations.

# 50. Capacity planned language

# 51. World Happiness Index

A mood tracking application that is aggregated across many different dimensions: every interaction with a company or government should produce an identifier. This identifier should be used to track a reaction to the interaction in terms of happiness. Scores can be aggregated by country, by council, by shop, by county, by month, by business.

# 52. Span programming

There are tools to implement distributed tracing. How about a tool that takes spans as placements and uses the span placement to schedule code in parallel and asynchonously?

# 53. Data Locality System

Break up your API call request handlers into a series of spans. Each span has an input data source and output. The DLS runs a server on every host (database, application, web) whereby any host can carry out any span. The DLS will try minimize data transfers and keep execution nearby data. So queries that deal with lots of data and reduce it to small amounts of data run on the database server and queries that return lots of data to clients run on the application tier.

# 54. Responsibility Index

There's a set of people responsible for some things. Finding these people is a challenge. I propose an index of responsibilities and a tracker of who is responsible for what. This way protest can be effective by targeting the right people. Currently it goes through representatives or through protests on the street, an ineffective way of getting things changed.

# 55. Problem database

A database of problems.

Existing:

* [Infinity Family](0oo.li)

# 56. GUI Data Ordering

A stream based data encoding that lays out the data in the order that it appears on a screen. So the first block of data is the data needed to render onto the screen immediately. After the first screenful of data, include data for the next screen, once this screen has been tapped. The data following is additional screenfuls, such as the result of scrolling to the next page.

Could create two TCP connections to the backend server. One for the current screen and one for the screens to come.

# 57. Graph database visual editor

An office suite program for editing graphs visually but are backed by a graph database.

# 58. In memory data model

Most application servers have the capacity to have objects that outlive requests. I propose this opportunity to load an object graph that represents application state in each application server. This model could be used for read only queries for added performance.

# 59. Life indicators - Situational awareness apps

My phone should know where I'm going to be sleeping and where I'm going to be eating in advance. I liken it to another status indicator along the notification area of the phone. I should be able to swipe down the notification area and click food and click what I want to eat and have it automatically sourced.

# 60. Combined truth

Don't repeat yourself often means a single point of truth exists. But it's poorly implemented in practice. I'm going to come out and say a single point of truth is not always accomplished. I want there to be multiple points of truth about a thing. But for them to be combined. You can say things about the same thing but from different perspectives and they might not always live in the same place.

 * Security is a good example.
 
Truth should be defined closest to where the responsibility lies, so it could be defined in any of the following:

 * BDD syntax
 * Issue tracker
 * In sourcecode
 * In a JSON file on a server

# 61. Simple kubernetes command line application

A command line application that feels like Docker but actually generates Kubernetes manifests.

# 62. Centralised account dependency management

To get started in a job, you often need access to lots of separate systems. It would be nice if even the tracking of what dependencies you require were centrally tracked. You could even automate the provision of access.

# 63. Backup Hooks

We shouldn't have to write backup code manually each time anew for each system if the components in the system are the same at each company. I propose a backup server which speaks a protocol that other systems can implement for timely backups.

# 64. Offline Websites

Companies could generate websites in advance as static websites that are downloadable as a single file.

# 65. Ending not found errors

# 66. Searchable data structures

Imagine a JSON file that you could refer to a field at any level and have meaningful data returned.

# 67. Earncode

Earn money solving implementing unit tests.

# 68. Guided browsing - Web What I Mean

We're often browsing to solve a problem. I want to browse with a context in mind. Perhaps I'm looking for API examples on how to call an API and want to "pick" a solution online. Or I'm browsing to follow a tutorial. I want some finality in the browsing concept, by picking or selecting the page with the answer I want to use on.

Picking the final page of the browsing session should import whatever machine readable context into the application that initiated the browsing session, such as an IDE call site search or a tutorial application.

# 69. Cloud model

A single page application for defining cloud resources in YAML.

# 70. Loop merging

Sometimes I write naive code first, a simple for loop and a search. I think it should be possible to automatically detect naively written searches and generate more efficient joins such as hash joins or hash table lookups.

This code calculates build success in a hierarchy that is three levels deep: an environment contains components and components contain commands. Failures ripple out from commands; a component with a failing command is failed and an environment with a failing component (or command) is failed.

I'm effectively doing a manual join on a number of records in memory and I'm doing it more than once (5 times).

```
  for environment in state["environments"]:
      environment["status"] = "ready"

  for component in state["components"]:
      component["status"] = "ready"
      component["progress"] = 100
      component["build_success"] = "success"

  for item in state["running"]:
      provider, running_component, command, manual, local = parse_reference(item["reference"])


      if "log_file" in item:
          item["current_size"] = os.stat(item["log_file"]).st_size
          if item["last_size"] != 0:
              item["progress"] = (item["current_size"] / item["last_size"]) * 100

              for environment in state["environments"]:
                  if item["environment"] == environment["name"]:
                      environment["status"] = "running"

              for component in state["components"]:

                  component_provider, component_name = component["name"].split("/")
                  if item["environment"] == component["environment"] and component_provider == provider and running_component == component_name:
                      component["status"] = "running"
                      component["progress"] = item["progress"]

              for latest in state["latest"]:
                  if latest["environment"] == item["environment"] and latest["name"] == "{}/{}".format(provider, running_component):
                      for current_command in latest["commands"]:
                          if current_command["name"] == command:
                              current_command["progress"] = item["progress"]


  state["running"] = sorted(state["running"], key=lambda item: item["reference"])

  for component_data in state["latest"]:
      provider, component = component_data["name"].split("/")
      component_data["build_success"] = "success"
      for command_data in component_data["commands"]:
          command = command_data["name"]
          builds, last_build_status, next_build = get_builds(component_data["environment"], provider, component, command)

          if builds:
              current_build = builds[-1]
              command_data["build_number"] = current_build["build_number"]
              command_data["build_success"] = "success" if last_build_status else "failure"

              if not last_build_status:
                  component_data["build_success"] = "failure"


              if not command_data.get("progress"):
                  command_data["progress"] = 100

  for component in state["components"]:
      for component_data in state["latest"]:
          if component_data["environment"] == component["environment"] and component_data["name"] == component["name"] and component_data["build_success"] == "failure":
              component["build_success"] = "failure"

  for environment in state["environments"]:
      environment["build_success"] = "success"
      for latest in state["latest"]:
          if latest["environment"] == environment["name"] and latest["build_success"] == "failure":
              environment["build_success"] = "failure"
```



# 71. Query like primitives for application code

# 72. Community Idea: I would pay £10

"I would pay" is a community where people say how much they'd pay for certain things.

# 73. Magic links

I have a file on my host machine that I want in my guest machine, usually in locked down environments I base64 encode the file and paste it into the guest VM and decode it. But what I want some thing more robust. A special string that encodes all the information needed to get to the file. When pasted, it contains the information needed to transfer the file from one environment to another.

# 74. Community Idea: Life strategy

A community of people that share their life strategy for different topics.

# 75. Web application format

* Define an SQL query
* Define the query's React renderer function for that query.
* Define the relationships between the queries on the screen

```
widget title
return <h1>Welcome</h1>
---
comment
Query -> Widget Mapping -> Predicates
POST handler
---
query
select id, strategy_name from strategies
---
widget strategy_list
var items = items.map(item => {
	return <li><input type="text" name="strategy[{item.id}]" value="{item.strategy_name}"></li>
return <div><ul>
{items}
})
</ul></div>
---
predicates
this atURL /strategies
this below title
this inForm action=/strategies method=post
---
widget submit
<button type="submit">Submit</button>
---
predicates
submit below strategy_list
---
POST /strategies
sql
update strategies set
    strategy_name = c.new_strategy_name
from (values
	(%gen_form_values_array("strategy")%)
) as c(column_id, new_strategy_name) 
where c.column_id = strategies.id;

```

# 76. Community Idea: Imaginary formats

A community of people that define imaginary formats that they wish existed.

# 77. Where can I get to within 20 minutes, Where can I get a job within 15 minutes

Use public transport and maps to work out where I can realistically go to within 20 minutes. I'd like to apply to jobs by physical area too.

Existing

 * [Walkscore (kind of buggy though)](https://walkscore.com)

# 78. Put a trie in front of a hashmap

We end up with a simple database when we put a trie in front of a hashmap. This allows for almost constant access times. [See this repository](https://github.com/samsquire/hash-db).

There must be a way of getting the best of both worlds: an SQL database with the performance of a NoSQL database. I'd like to synchronize an SQL database with DynamoDB.

# 79. Scaling Plan

An PaaS that begins while the application is hosted on a single box and then scales out to load balancer boxes, database boxes -- all while being on the same platform. Can automatically determine when to scale based on rules.

# 80. Wantsfiles

Every domain should have a `Wantsfile` at the root of the domain which states what that person or organisation wants. Sellers can provide a `Sellfile` at the root of their domain.

Matching between `Wantsfile` and `Sellfile` is automatic with an order matching engine so that purchases are automatic, even handling the exchange of money.

* I can request coffee at £2.65 for 500g, milk for £1.50 for 4 pints and so on and have them automatically delivered to me.
* I can set a price for hosting some files and an archive and have someone automatically host them for me.
* I can request a Postgres database and its backups every day and have someone provide that interface for me.

# 81. Person heads up display

When I'm with someone in person, my phone should show a screen with that person's profile on it and should show me all the things I can do with that person digitally.

# 82. Entity management software

Track all the entities you know, whether or not you trust them.

# 83. Monetization.txt

monetization.txt is a file you keep at the root of your web domain where you show people how to support you financially.

# 84. Do a range query on page load

If you store data in a hashmap and use a trie in front of it, you can fetch all the data to render a webpage with a partition key and sort key and this can map to a hash map access for each object fetched. Much faster than an SQL query.

* /products/ can do a partition key search of PK=products SK="begins_with(products)"
* /products/product-100 can do a partition key search of PK=products SK="product-100"

# 85. Layers lang

Some algorithms are easier to explain when they are transferred to paper and moved around on a table with bits of virtual string connecting them. I propose a layer language for building algorithms this way.

Creating a movement of a layer, prompts the user for a machine readable reason for moving and what to move. I envision a btree being easy to create with layer language.

# 86. Build server configured by YAML in Markdown

# 87. Embedded resources marked for caching

Why not embed CSS and Javascript in HTML and have an attribute to mark the resource as cacheable. There would be some way to communicate the fact that the resource is cached to the server. Perhaps a header. Then on other pages, we can include an empty CSS and Javascript block with an attribute to say use the cache.

# 88. 

# 89. 

# Generating ideas

 * marketplace
 * schedule
 * tree
 * additive/combined
 * auto
 * mesh
 * hooks

# Incomplete thoughts and ideas 

Scope magic

# Combined truth

Tree programming

Function Mesh, automesh

Fluent system

# Query Optimisers

# For loops flow control

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
