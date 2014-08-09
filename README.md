# noodle
Clean-room implementation of the [Puppet External Node Classifier](http://docs.puppetlabs.com/guides/external_nodes.html)
and server database that we [use at work](bit.ly/noodlerockeagle2013).

## Future dreamland
* Duplicate existing functionality
* Magicaly templated Heira backend
* Relationships, including enough to define network config for an entire stack (from IPs to firewall and load balancer, etc)

## Running it (untested)
* `git clone`
* `cd noodle`
* `bundle install`
* Run tests: `rake`
* Start app: `rackup`

## Examples
```bash

# Search
curl -s -XGET http://localhost:9292/nodes/jojo.example.com
# (returns nothing)

# Create
curl -s -XPOST http://localhost:9292/nodes/jojo.example.com -d @node.json
# Name:   jojo.example.com
# Ilk:    host
# Status: surplus
# Params:
#   site = moon
# Facts:

# Search again
curl -s -XGET http://localhost:9292/nodes/jojo.example.com
# Name:   jojo.example.com
# Ilk:    host
# Status: surplus
# Params:
#   site = moon
# Facts:

# Delete
curl -s -XDELETE http://localhost:9292/nodes/jojo.example.com
# Deleted jojo.example.com


```

## Thanks and references and notes to self
* [elasticsearch-persistence](https://github.com/elasticsearch/elasticsearch-rails/tree/master/elasticsearch-persistence)
* [Sinatra](https://github.com/sinatra/sinatra)
* [Heroku HTTP+JSON API design](https://github.com/interagent/http-api-design)
* [REST](http://en.wikipedia.org/wiki/Representational_state_transfer#Applied_to_web_services)

