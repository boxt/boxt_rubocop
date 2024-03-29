# BOXT Rubocop

[![Gem Version](https://badge.fury.io/rb/boxt_rubocop.svg)](https://badge.fury.io/rb/boxt_rubocop)
[![CI](https://github.com/boxt/boxt_rubocop/actions/workflows/ci.yml/badge.svg)](https://github.com/boxt/boxt_rubocop/actions/workflows/ci.yml)

Base [Rubocop](https://rubocop.org) settings for all Boxt Ruby projects.

## Requirements

- Ruby >= 3.0

## Installation

Add this line to your application's Gemfile:

```ruby
group :development, :test do
  # ...
  gem "boxt_rubocop"
end
```

And then execute:

```sh
bundle
```

## Usage

Put this into your .rubocop.yml.

```yml
require:
  - boxt_rubocop
```

To enable additional configuration for `rubocop-rails` and `rubocop-rspec`, add the following to your .rubocop.yml:

```yml
inherit_gem:
  boxt_rubocop:
    - rails.yml # use Rails cops - see Additional Extensions/Cops
    - rspec.yml # use rspec cops - see Additional Extensions/Cops
```

## Creating new custom cops

Use the rake task new_cop to generate a cop template:

```sh
$ bundle exec rake 'new_cop[Boxt/Name]'
[create] lib/rubocop/cop/boxt/name.rb
[create] spec/rubocop/cop/boxt/name_spec.rb
[modify] lib/rubocop/cop/boxt_cops.rb - `require_relative 'boxt/name'` was injected.
[modify] A configuration for the cop is added into config/default.yml.

```

Documentation on creating a new cop can be found [here](https://docs.rubocop.org/rubocop/1.56/development.html#create-a-new-cop).

### NewCops

`NewCops` is enabled by default.

### Additional Extensions/Cops

The following Rubocop gems are also installed with this gem:

- [rubocop-faker](https://github.com/koic/rubocop-faker)
- [rubocop-performance](https://github.com/rubocop/rubocop-performance)
- [rubocop-rails](https://github.com/rubocop-hq/rubocop-rails)
- [rubocop-rake](https://github.com/rubocop-hq/rubocop-rake)
- [rubocop-rspec](https://github.com/rubocop-hq/rubocop-rspec)

To enable these add the following to your `.rubocop.yml` file.

```yml
inherit_gem:
  boxt_rubocop:
  # .... add cops

require:
  - rubocop-faker # if your project is using the Faker gem then add this
  - rubocop-performance # Add this for performance cops
  - rubocop-rails # if your project is a Rails app/engine then add this, plus the - rails.yml setting above
  - rubocop-rake # if your project is using rake then add this
  - rubocop-rspec # if your project is using rspec then add this, plus the - rspec.yml setting above
```

## Editor Plugins

There are also some useful Rubocop editor plugins to help with in-editor linting.

### Atom

- [linter-rubocop](https://atom.io/packages/linter-rubocop)
- [rubocop-auto-correct](https://atom.io/packages/rubocop-auto-correct)

### RubyMine

- [rubocop](https://www.jetbrains.com/help/ruby/rubocop.html)

### VSCode

- [ruby-rubocop](https://marketplace.visualstudio.com/items?itemName=misogi.ruby-rubocop)

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/boxt/boxt_rubocop.

## License

The gem is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).
