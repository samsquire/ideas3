# An Extra 100 Ideas for Computing

Some ideas for computers I thought of that I enjoyed thinking about and writing down. Please see the other pages of the series.

* [Follow me on Twitter](http://twitter.com/mrsamuelsquire)
* If you like my ideas, please start a chat or discussion with me. I'd love to hear your thoughts!
* Please use issues to start discussions on ideas.
* The first page of this series [100 Ideas for Computing](https://github.com/samsquire/ideas)
* The second page of this series [Another 85+ Ideas for Computing](https://github.com/samsquire/ideas2)
* The forth page of this series [An Additional 100 Ideas for Computing](https://github.com/samsquire/ideas4)
* Looking for business ideas? Checkout my [startups repository](https://github.com/samsquire/startups) where I list business ideas.


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

A desktop distribution of Linux that has a [deep lever](https://github.com/samsquire/ideas2#99-deep-lever--action-at-distance) into a custom web forum. Translations and GUIs are rendered in the web forum and people vote on things such as layouts. People decide how the desktop should work by talking of it in threads because threads decide how the desktop works. People can go against the grain and vote for their desktop to work in a way that is not the consensus. 

# 6. Business Idea: The Configurator

Run a small program from a startup company to extract all running servers (from DNS) and SSH hostnames, bastion host, send this to startup, the startup works out how to configure complicated software like Envoy for you, with your configuration based off of your environment. Once this configuration is generated, a dynamic program is ran regularly to update this configuration (as service discovery).

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

In the Java ecosystem, ontologic class sharing would consist of a set of builders.

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

A database system that stores queries like stored procedures but uses the plan of the query to optimize data storage format. The queries are analaysed to determine the optimal data structure to make the query fast at reading and writing. There would be tunables for optimising for read or write loads.

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

# 28. Backup as a service

Backup is fundamental to running computer services, it should be available as a service. Postgres backup as a service. A dashboard should be provided to show available backups and to restore them.

# 29. Per-server request log

When a request is received, serialize the request and write it to the machine readable log in the background. Do not acknowledge success until it is written to the per-server log. Aggregate the per-server write ahead logs every few minutes. Every request therefore has a write ahead log.

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

Desktops should have a built in queuing system for queuing up moves, copies, renames, installs. 

See https://github.com/samsquire/cloud-desktop#desktop-queuing for an example

# 39. Built to cluster with others

Each installation of a desktop environment is a set of resources that could be shared.

# 40. Text zoom

Text can be folded and made it so that more is available at a different zoom level.

```
<document>
<text level="1">I am visible at zoom level 1. <text level="2">I'm visible at zoom level 2</text></text>
</document>
```

# 41. Digital law

The law system should be programmatic. It should be possible to fill in a form and get a legal result from it.

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

# 50. Capacity planning tool

An interactive tool that renders time charts of how long some thing takes. Imagine 60 frames a second visual output being a goal, you can drag pieces of work onto the chart to schedule it to run.

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

* [Infinity Family](http://0oo.li)

# 56. GUI Data Ordering

A stream based data encoding that lays out the data in the order that it appears on a screen. So the first block of data is the data needed to render onto the screen immediately. After the first screenful of data, include data for the next screen, once this screen has been tapped. The data following is additional screenfuls, such as the result of scrolling to the next page.

Could create two TCP connections to the backend server. One for the current screen and one for the screens to come.

# 57. Graph database visual editor

An office suite program for editing graphs visually but are backed by a graph database.

# 58. In memory data model

Most application servers have the capacity to have objects that outlive requests. I propose this opportunity to load an object graph that represents application state in each application server. This model could be used for read only queries for added performance.

# 59. Life indicators - Situational awareness apps

My phone should know where I'm going to be sleeping and where I'm going to be eating in advance. I liken it to another status indicator along the notification area of the phone. I should be able to swipe down the notification area and click food and click what I want to eat and have it automatically sourced.

* hotels/airbnbs/home
* travel purchase (flights, trains, buses)
* self storage
* food

# 60. Combined truth

Don't repeat yourself often means a single point of truth exists. But it's poorly implemented in practice. I'm going to come out and say a single point of truth is not always what you want. I want there to be multiple points of truth about a thing. But for them to be combined. You can say things about the same thing but from different perspectives and they might not always live in the same place.

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

Relative searches are the cause of not found errors. Computers could look everywhere for imported libraries to avoid unnecessary errors.

# 66. Searchable data structures

Imagine a JSON file that you could refer to a field at any level and have meaningful data returned. Without having to specify the path to get to that item.

# 67. Earncode

Earn money solving implementing unit tests.

# 68. Guided browsing - Web What I Mean

Imagine documentation that retained your goal that you're trying to solve. So every thing stems from a search parameter, you vote yes when the guided browsing took you to where you wanted to be.

We're often browsing to solve a problem. I want to browse with a context in mind. Perhaps I'm looking for API examples on how to call an API and want to "pick" a solution online. Or I'm browsing to follow a tutorial. I want some finality in the browsing concept, by picking or selecting the page with the answer I want to use on.

Picking the final page of the browsing session should import whatever machine readable context into the application that initiated the browsing session, such as an IDE call site search or a text editor.

Existing:

[Amna](https://getamna.com) - Write a task. Click on it. Get a browser just for that single context.

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
	})
return <div><ul>
{items}

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

# 86. Build server improvements

* **Build server configured by YAML in Markdown**
* **Build server installer API** Build server commands map to an installer API so that installers are easily created.

# 87. Embedded resources marked for caching

Why not embed CSS and Javascript in HTML and have an attribute to mark the resource as cacheable. There would be some way to communicate the fact that the resource is cached to the server. Perhaps a header. Can use serialized bloom filters to indicate what resources are cached. Then on other pages, we can include an empty CSS and Javascript block with an attribute to say use the cache.

# 88. Scalescript & method scale ups

Write the workflow of your distributed system as a simple program that can run on a single computer. Then scale it up by weaving the following:

 * Define method call replacements with queries, queues or distributed logs.
 * Introduce loops that stream data rather than wait for it all to be in memory.

A DSL for distributed systems. 

# 89. Join service

If you write a microservice architecture and have every database separated from every other and you have a good service oriented system.

I propose a join service that allows joins between different microservices, for the join query:

```
select * from user_orders inner join users.id = user_orders.user_id where users.id = 20
```

* Bulk extracts `select * from user_orders where user_orders.user_id = 20` from user_orders service and `select * from users where users.id = 20` from users.
* Transfers them to the join service database. Bulk imports.
* Run the join query.

# 90. Mouse button prediction

https://jsfiddle.net/yLjuc1d0/

# 91. Noun management software and Autodebugging

A GUI for tracking nouns and their relationships in a system. For example, a list of nouns that should be supported:

 * iam roles
 * kafka topics
 * s3 buckets
 * s3 objects
 * producers
 * consumers
 * kubernetes objects
 * ec2 instances
 * request ids

Autodebugging is to take an entered identifier and turn it into useful information about whether or not some thing works. For example:

 * Enter a Kafka topic name, get a list of consumers and producers. (Derived from your configuration files pointing to Kafka)
 * Enter an s3 bucket name, amongst objects, get a list of iam roles that can write to the bucket (Derived from the AWS API and based off of assume role policies)

Write ingesters for each system tool or API and have it warehoused in one place for introspection.

# 92. Acquire physical objects with computer

* Borrow physical objects with your computer.
* Define a computer configuration with code.

```
Import Gigabyte X399 AORUS PRO
Import AMD Ryzen Threadripper 2990WX 32-Core Processor, 3000 Mhz, 32 Core(s), 64 Logical Processor(s)
Construct
```

# 93. Desktop shop front - Buy/Sell interface and payment integrated into the desktop environment

Buying things and selling things are basic actions in the world that deserve decentralized infrastructure to action in the real world.

 * Start a shop with just your desktop environment. Accept payments.
 * Pay for bespoke software through the desktop with the option of making the resulting product open source.
 * Trade menu - like a video game where you can trade items, a way of trading with strangers online.
 * Auction

If we have a trading platform where people can list products to sell in a digital shop front, there needs to be some way of creating assets that is not necessarily a website even if web technologies are used. I propose users have the freedom of creating assets in various formats, videos, presentations and marketing materials in a common archive format. So we can realistically say that this file represents this product or service pretty accurately and completely.

The desktop environment would have a common powerful shopping interface that searches these products. The effort to build this shop front is paid once and maintained by the community. But who appears in this shop is also community defined.

* I propose a database of product features from all product fields.
* Every feature in a computer system is broken down into a list of SKUs. Such as "view files on filesystem" has an identifier.
* Marketing SKU database
* Calculation of ratios built into the shopping software.

# 94. Person dependencies

A decentralized work community whereby you can depend on the work of others to benefit you personally. There are millions of people working around the clock on different things. Owning index funds allow those working at companies to benefit you financially directly by increasing the value of your shares and increasing dividends. There must be a way to make what other people do daily benefit you directly too. Person dependencies allows me to depend on the output of a particular individual. I depend on the creators and maintainers of Python3 who increase its performance, remove bugs and fix security vulnerabilities. I want to make this dependency on particular people explicit.

So, how can the work that other people do benefit me directly?

* **Crowdsourced queries** I'm moving to a new area and need to find a job. Can the masses of people online help me find a job quickly?
* **Digital Work abstraction**. Pattern match on what a person is doing at a high level on a computer system and see if this pattern can be applied in other areas by other people with the same patterns. If someone is iterating through a spreadsheet, this loop should be detectable based on the searches and copy and paste history of the user into which fields that they are copying into. This work could then be automated.
* **Working games** People can play a first person shooter and investigate performance problems on production hardware by investigating a virtual room of stats looking for enemies.
* **Graph eyes** Outsource looking at graphs to the community.

I want to be able to import a person by writing down an import statement.

```
import sam@samsquire.com:
   ask "Can you review this idea https://github.com/samsquire/ideas3#94-person-dependencies "

```

# 95. Permutation Slots

Computers can calculate permutations and combinations ridiculously fast. The mouse creates a hard deadline on operational completion time for interactivity, the latency is very visible to computer users. I propose computers randomly generate solutions in the background for humans to review and like a slot machine, humans review the generated solutions for usage.

Examples where this is useable:

* For document outlines that follow a structure. Randomly generate presentations and word processed document formatting options.
* Web site design
* Data layouting
* Layout

# 96. Hackathon Hotel

A hotel whereby there is always a hackathon going on to build new things.

# 97. System bootstrap account

An online service whereby common dotfiles and configuration files can be protected by an online account and rsynced to the system at system login time.

This is what Ubuntu One should have been.

# 98. Personal services

Services built into the desktop or phone to benefit your life:

* automated job search, monitors the market for for jobs with higher salaries
* spaced repetition feed, shows content that has been read before hand (Anki integrated into the desktop)
* gamified behaviour tracker (time management)
* budget tracking, virtual bank account buckets
* quote follower - change your life according to quotations, put quotations into practice
* flash polling - run a poll for everybody
* family software: family management, location tracking, decision making, voting, what's for dinner

# 99. Process, an office suite programme

Corporations often have processes and workflow engines to manage flow between states. This could all be standardized by an office suite programme called "Process" which manages the transition of work items through different procedures.

# 100. Idea Collection

* **Messenger bot to file** Orchestrate software installation by talking to bots. So you might have a bot that installs services, by creating systemd services. Send the command to make a service from. So you would send a URL to untar to a bot, the bot would untar it, you would send a message to move the file to the right location.
* **Desktop clustering and Desktop cloud** Someone should be able to build a cloud infrastructure by networking desktop computers together. OpenStack could be integrated into the desktop. Desktops connect to one another to create a cluster.
* **Instabusiness** Business software built into the desktop, so people can run companies using just a computer.
* **Metadata enhanced storage** Instant storage consumption data due to indexes. Rather than running ncdu to calculate storage usage, we can get the information immediately. Would slow down the filesystem for a benefit in performance when running aggregations.
* **Community Idea: Always there** A community of people guaranteed to reply. You're in a supermarket and you have the option of two choices, at different prices. You're too lazy to work it out on your phone, so you take a photo of both price tags and ask people to help with the math.
* **Dimensionality reducer** Most people can handle a life of relative complexity, house, car, travel to work, rest, cook and sleep. Anything on top of this is complexity. I propose a computer system that tracks dimensionalities. Which are things to manage: If you have a car, you need car insurance and fuel, if you have a house you need house insurance. I propose the dimensionality reducer generates a stream of work to fulfil for other people, in return for payment. You get quizzed on your dimensionality score, which is how many dimensions of life you have to worry about, and then you are recommended businesses that manage these on your behalf.
* **Bandwidth chargers** Billing for users of bandwidth from services like AWS. So open source projects could create high data transfer services.
* **Possession tracking**
* **Focal point** We often lose track at what task we are doing. If we're making coffee and have a plan to make coffee and get into a conversation about some complicated thing, depending on our skill level, or if the task is more complicated, we lose the ability to make coffee. So we need a program reminding us what we are working towards. Perhaps a prominent word in a location on the computer screen which should be a focal point.
* **SLA marketplace** Buy an SLA

# 101 Community Idea: Instant job

High level services such as delivery services that are broken up into subjobs for people to accept. Can be paid to do work without a job interview and are reviewed by other users.

# More ideas

There's more ideas in [ideas4](https://github.com/samsquire/ideas4), it's not finished yet but you can give it a look.

