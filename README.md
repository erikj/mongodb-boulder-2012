# mongodb boulder 2012

## background

<http://www.10gen.com/events/mongo-boulder>

## notes

- opening address from 10gem president Mac Schireson


## sessions

### MongoDB Versatility: Scaling the MapMyFitness Platform

- 9:45-10:45
- Chris Merz, Data Storage Engineer, MapMyFitness
- <http://www.mapmyfitness.com/>

> The MMF user base more than doubled in 2011, beginning an era of rapid data growth. With Big Data come Big Data Headaches. The traditional MySQL solution for our suite of web applications had hit it's ceiling. MongoDB was chosen as the candidate for exploration into NoSQL implementations, and now serves as our go-to data store for rapid application deployment. This talk will detail several of the MongoDB use cases at MMF, from serving 2TB+ of geolocation data, to time-series data for live tracking, to user sessions, app logging, and beyond. Topics will include migration patterns, indexing practices, backend storage choices, and applicat

### Schema Design Principles and Practice

- 10:30 am - 11:15 am
- Robert Stam, Software Engineer, 10gen

- see also <http://www.slideshare.net/mongodb/schema-design>

> One of the challenges that comes with moving to MongoDB is figuring how to best model your data. While most developers have internalized the rules of thumb for designing schemas for RDBMSs, these rules don't always apply to MongoDB. The simple fact that documents can represent rich, schema-free data structures means that we have a lot of viable alternatives to the standard, normalized, relational model. Not only that, MongoDB has several unique features, such as atomic updates and indexed array keys, that greatly influence the kinds of schemas that make sense.

#### basic data modeling for doc-based DBs

- <http://en.wikipedia.org/wiki/Data_modeling>
- <http://en.wikipedia.org/wiki/Data_model>

document-based db = different normalization

- embedding documents instead of relations
- tables : collections
- rows : documents
- joins : embeds and links
- partition : shard
- individual documents have a schema

- collections are cheap (max 24000)
- documents:
  - zero or more elements
  - elements are name / value pairs
  - JSON / BSON
  - <http://www.mongodb.org/display/DOCS/Data+Types+and+Conventions>
  - times in mongo are always UTC
  - regex data type
    - querying: <http://www.mongodb.org/display/DOCS/Data+Types+and+Conventions>
  - max document size: 16MB
  - design documents that map simply to your application

- one-to-many options
  - embedded arrays
  - embedded trees
  - normalize into other collection
    - e.g.
      - books    = [ {comment_ids : [1,2]]} ]
      - comments = [ {_id:1, book_id:1}, {_id:2, book_id:1} ]

- many-to-many queries

      > product = db.product.findOne()
      > categories = db.categories.find({$in:product.category_ids)

- trees can be hard to search

- relational mongodob example:
  - <http://seanhess.github.com/2012/02/01/mongodb_relational.html>

### MongoDB Case Study

- 11:15-12noon
- Nathan Wells, [Adaptive Computing](http://www.adaptivecomputing.com/about/index.php)

- hibernate is lame
- ORM is a leaky abstraction
- RDBMS's are inflexible by nature
- hiccups w/ grails plugin for mongodb
- increased dev complexity => increased deployment complexity


### Indexing and Query Optimization

Max Schireson, President, 10gen

