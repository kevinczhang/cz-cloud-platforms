# ElastiCache

* ElasticCache is a fully managed, in-memory cache engine used to improve database performance by caching results of queries that are made to a database 
* ElasticCache is great for large, high-performance or high-taxing queries - and can store them inside of a cache \(Elastic Cache Cluster\) that can be accessed later \(instead of repeat request continually hitting the primary database\) 
* ElastiCache allows for managing web sessions, and also caching dynamically generated data 
* Available engines to power ElastiCache include: Memcached \(Mem-Cache-D\) and Redis 
* Generally, the application needs to be built to work with either Redis or Memcached 
* Popular options like MySQL have Memcached plugins, which allow an application to easily work with ElastiCache \(if using Memcached as the engine\)

## Caching Strategies

#### Lazy Loading: 

* With lazy loading, you write data to the cache when a cache miss occurs 
* Lazy loading avoids filling up the cache with data that wont be requested 
* Data in the cache can become stale if lazy loading is implemented without other strategies 

#### Write Through: 

* When using a write through strategy, the cache is updated whenever a new write or update is made to the underlying database 
* A write through strategy allows cache data to remain up-to-date 
* A write through strategy can add wait time to write operations in your application 
* A write through strategy without a TTL can result in a lot of cached data that is never read 

#### Adding Time To Live \(TTL\) 

* Drawbacks of lazy loading and write through techniques can be helped by a TTL 
* A TTL is the length of time before a key expires 
* When reading an expired key, the application checks the value in the underlying database 
* TTLs do not garuntee fresh information, but they keep the data from getting too stale and allow the cache to clean up unused keys

