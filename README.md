# Fetchable

Provides a decorator to add a `Hash#fetch` like interface to any object.

You must specify a method which it should delegate to and pass the key.

`Hash#Fetch` is one of my favourite Ruby methods and can be tricky to implement
its full behaviour so here it is extracted for you to add to whichever object
you choose.

## Installation

Add this line to your application's Gemfile:

    gem 'fetchable'

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install fetchable

## Usage

```ruby
require "fetchable"

array = ["zero", "one", "two"]

fetchable_array = Fetchable.new(array, :finder_method => :[])

fetchable_array.fetch(0)
 => "zero"

fetchable_array.fetch(2)
 => "two"

fetchable_array.fetch(3)
 => KeyError key not found 3

fetchable_array.fetch(3, "three")
 => "three"

fetchable_array.fetch(3) { "Execute a block!" }
 => "Execute a block!"

fetchable_array.fetch(3) { |key| "Do something based on missing key #{key}" }
 => "Do something based on missing key 3"
```

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request