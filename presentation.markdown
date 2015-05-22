title: Octoparts intro
author:
  name: Lloyd
  twitter: meta_lloyd
  github: lloydmeta
  url: https://beachape.com
output: index.html
theme: sudodoki/reveal-cleaver-theme
controls: true

--

# Octoparts intro
[beachape.com/octoparts-intro](http://beachape.com/octoparts-intro)

Largely based on [@cbirchall's](https://twitter.com/cbirchall/) [slides for ScalaMatsuri](https://docs.google.com/presentation/d/1XxIwilp3OhLeTBOFotBb_6tieYJS888wYsNK9KEkI58)

--

## Overview

1. Distributed systems is hard
2. Octoparts overview
3. Octoparts features
4. Using Octoparts

--

### Distributed systems is hard

* Fault tolerance
  * 1 backend goes down → takes down 5 backends and 10 frontends with it
* Visibility
  * debugging and recovering when things go wrong
  * measuring performance of backend APIs
* Performance
  * lots of serial API calls
  * timeouts too long/non-existent
  * caching of API responses inconsistent across clients

--

![octoparts](imgs/octo_logo.png)

--

### Octoparts

* API request aggregation service.
* Implemented in Scala, making heavy use of the Hystrix library.

--

### Octoparts features

* API call parallelization
* Hard timeouts
* Fault tolerance
* Powerful and flexible caching
* Visibility
* Admin UI
* Alert mails
* Stateless, async → scalable

--

### Octoparts features: parallelization

![parallelization](imgs/parallelisation.png)

--

### Octoparts features: timeouts

![timeouts](imgs/timeouts.png)

--

### Octoparts features: timeouts

![timeouts](imgs/timeouts2.png)

--

### Octoparts features: fault tolerance

![timeouts](imgs/fault_tolerance.png)

--

### Octoparts features: caching

![timeouts](imgs/caching.png)

--

### Visibility: Hystrix

![timeouts](imgs/hystrix.png)

--

### Visibility: Kibana

![timeouts](imgs/kibana.png)

--

### Visibility: Zipkin

![timeouts](imgs/zipkin.png)

--

### Moving parts

![moving parts](imgs/moving_parts.png)

--

### Using Octoparts

```ruby
# create client
client = Octoparts::Client.new
# invoke with builder
aggregate_request = Octoparts.build_aggregate_request do
  request_meta(id: 'test', timeout: 500)
  requests do
    part_request(part_id: 'echo').add_param('fooValue', 'test')
  end
end
response = client.invoke(aggregate_request)
```

--

### Resources

* [GitHub](https://github.com/m3dev/octoparts)
* [Docs](http://m3dev.github.io/octoparts)
* [Octoparts Ruby client](https://github.com/ma2gedev/octoparts-rb)

--

### Questions?

