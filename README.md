# CIF Software Development Kit for Ruby 

The CIF Software Development Kit (SDK) for Ruby contains library code and examples designed to enable developers to build applications using CIF.

[![Build Status](https://travis-ci.org/csirtgadgets/rb-cif-sdk.svg?branch=master)](https://travis-ci.org/csirtgadgets/rb-cif-sdk) [![Coverage Status](https://coveralls.io/repos/csirtgadgets/rb-cif-sdk/badge.png)](https://coveralls.io/r/csirtgadgets/rb-cif-sdk)

# Installation
## Ubuntu
```bash
$ sudo apt-get update && sudo apt-get upgrade -y
$ sudo apt-get install -y libyaml-dev ruby2.0-dev
```

# Examples
## Client
```ruby
require 'cif-sdk'

config = {
  :token  => '1234',
  :remote => 'https://localhost/api'
}

cli = CIF::SDK::Client.new(config)
for i in 0 ... 3
  ret = cli.ping()
  puts "roundtrip: #{ret}ms..."
  select(nil,nil,nil,1)
end
```
## Search
```ruby
r = cli.search(:query => 'example.com')
```

## Ping
```ruby
r = cli.ping()

puts "ping successful"
```
## Submit
```ruby
obs = {
  :observable => 'example.com',
  :tlp        => 'amber',
  :provider   => 'me@me.com',
  :group      => 'everyone'
}
r = cli.submit(obs)
```

# License and Copyright
Copyright (C) 2014 the CSIRT Gadgets Foundation

Free use of this software is granted under the terms of the GNU Lesser General Public License (LGPL v3.0). For details see the file LICENSE included with the distribution.
