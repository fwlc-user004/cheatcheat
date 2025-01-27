# Ruby Cheat Sheet

## Basics

### Output
```ruby
puts "Hello, Ruby!"  # Prints with a newline
print "Hello"         # Prints without a newline
```

### Comments
- Single-line comment: `# This is a comment`
- Multi-line comments:
  ```ruby
  =begin
  This is a multi-line comment
  =end
  ```

### Variables
- Dynamic typing: No need to declare types.
```ruby
name = "John"      # String
age = 25            # Integer
is_active = true    # Boolean
```

### Constants
- Start with an uppercase letter.
```ruby
PI = 3.14159
```

## Data Types

### Numbers
```ruby
integer = 42
float = 3.14
```

### Strings
```ruby
str = "Hello, Ruby!"
multiline = <<~TEXT
  This is
  a multi-line string.
TEXT
```

### Arrays
```ruby
arr = [1, 2, 3]
arr << 4  # Add element
```

### Hashes
```ruby
hash = { key: "value", another_key: 42 }
hash[:key]  # Access value
```

### Symbols
```ruby
sym = :my_symbol
```

## Conditionals

### If/Else
```ruby
if condition
  # code
elsif another_condition
  # code
else
  # code
end
```

### Ternary Operator
```ruby
result = condition ? "true" : "false"
```

### Case Statement
```ruby
case variable
when "value1"
  # code
when "value2"
  # code
else
  # code
end
```

## Loops

### While Loop
```ruby
while condition
  # code
end
```

### Until Loop
```ruby
until condition
  # code
end
```

### For Loop
```ruby
for i in 1..5
  puts i
end
```

### Each Loop
```ruby
[1, 2, 3].each do |num|
  puts num
end
```

### Times Loop
```ruby
5.times do |i|
  puts i
end
```

## Methods

### Define a Method
```ruby
def method_name(param1, param2)
  # code
end
```

### Default Parameters
```ruby
def greet(name = "World")
  puts "Hello, #{name}!"
end
```

### Return Values
```ruby
def add(a, b)
  a + b
end
```

## Classes

### Define a Class
```ruby
class Person
  def initialize(name, age)
    @name = name
    @age = age
  end

  def greet
    puts "Hello, I am #{@name}!"
  end
end

person = Person.new("Alice", 30)
person.greet
```

### Class Variables and Methods
```ruby
class Example
  @@count = 0

  def self.increment
    @@count += 1
  end
end

Example.increment
```

## Modules

### Define and Include a Module
```ruby
module Greetable
  def greet
    puts "Hello!"
  end
end

class Person
  include Greetable
end

person = Person.new
person.greet
```

## File Handling

### Reading a File
```ruby
File.open("file.txt", "r") do |file|
  file.each_line { |line| puts line }
end
```

### Writing to a File
```ruby
File.open("file.txt", "w") do |file|
  file.puts "Hello, File!"
end
```

## Error Handling

### Begin/Rescue
```ruby
begin
  # Code that may raise an error
rescue StandardError => e
  puts "Error: #{e.message}"
end
```

## Gems and Bundler

### Install a Gem
```bash
gem install gem_name
```

### Create a Gemfile
```ruby
source "https://rubygems.org"
gem "gem_name"
```

### Install Gems with Bundler
```bash
bundle install
```

## Debugging

### Use Pry
```bash
gem install pry
```
```ruby
require 'pry'; binding.pry
```

## Best Practices
- Follow naming conventions: snake_case for methods and variables, CamelCase for classes.
- Use meaningful variable and method names.
- Write tests for your code using RSpec or MiniTest.
