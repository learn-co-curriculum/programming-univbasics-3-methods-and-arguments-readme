# Ruby Method Arguments

## Learning Goals

- Describe the functionality of arguments
- Recognize the difference between arguments and parameters
- Define a method that accepts multiple arguments
- Define a method that uses default arguments

## Introduction

In the real world, many of our interactions have a "template" behavior that is
applied to every interaction, but these behaviors change only slightly depending
on a tiny factor. The key to being general most the time _but_ with room for slight
adjustments is the _argument_.

## Describe the Functionality of Arguments

For example, the barista at the coffee shop follows a _standard_ process
but will call out **your** name when **your** order is ready. The same _general_
process for other coffee-buyers, but, the name shouted will change per
customer.

Methods can also be written to have a "template" of shared activity, but this
activity can be changed _just a little bit_ when necessary. In the previous
lesson, we saw a method called `say_hello_five_times`. But what if we wanted
to say "Hello" three times? Nine times? Twenty-two times? Our code would be
very cluttered if we had to write a separate method for each of those counts.

In this case, we want the "general behavior" to be saying hello. But we want
to make it possible to vary the number of times `"Hello"` is said. The little
bit we want to change is the number of times.

The particular bits that make the change the way a method behaves when it's 
called are called "arguments."

## Recognize the Difference Between Arguments and Parameters

To define the ***arguments*** you expect a method to take, you specify ***parameters*** in the
line that starts with `def`.

> **WARNING**: Be careful of the vocabulary here. It gets _really_ tricky. We'll repeat
> ourselves because it's so easy to get confused.

_Parameters_ are the "catchers" to _arguments_. When you ***call*** a method, the data you
pass in during the ***call*** is called an _argument_. We access the data passed as ***arguments*** in the
method's call through the ***parameter***.

For example, if we want to write a method called `say_hello_multiple_times` that
accepts an argument of how many times to say `"Hello!"`, we would do it like this:

```ruby
    # method name            parameter
def say_hello_multiple_times(count)
  count.times do
    puts "Hello!"
  end
end
say_hello_multiple_times(3)
say_hello_multiple_times(2)
```

Three `"Hello!"`s are printed and then two `"Hello!"`s:

```text
irb(main):053:0> say_hello_multiple_times(3)
Hello!
Hello!
Hello!
=> 3
irb(main):054:0> say_hello_multiple_times(2)
Hello!
Hello!
=> 2
```

Looking at the code, the `count` parameter is given a value as an argument.
The argument is passed in as an argument in `say_hello_multiple_times`'s call.

Let's open up IRB and try this out! First, take the `say_hello_multiple_times` code
sample and paste it into your command line. Once that has been entered, you can
test out the method like this:

```ruby
def say_hello_multiple_times(count)
  count.times do
    puts "Hello!"
  end
end
say_hello_multiple_times(2)
```

returns:

```text
irb(main):014:0> say_hello_multiple_times(2)
Hello!
Hello!
=> 2
```

## Define a Method That Accepts Multiple Arguments

A method can have **multiple** parameters. Most methods have zero to four
parameters. Let's make our method a little bit more friendly by adding a name that we
want to say "Hello" to.

```ruby
def say_hello_multiple_times(count, name)
  count.times do
    puts "Hello #{name}!"
  end
end
say_hello_multiple_times(3, "Tom Skeritt")
say_hello_multiple_times(2, "Erin Moran")
```

We use `,` to separate parameters in the method signature. We use `,` to 
separate arguments in the method call:

```ruby
  # method name              first_parameter, second_parameter
def say_hello_multiple_times(count, name)
  count.times do
    puts "Hello #{name}!"
  end
end

say_hello_multiple_times(5, "Ruby")
say_hello_multiple_times(10 / 2, "Elixir")
```

Produces:

```text
irb(main):031:0> say_hello_multiple_times(5, "Ruby")
Hello Ruby!
Hello Ruby!
Hello Ruby!
Hello Ruby!
Hello Ruby!
=> 5
irb(main):032:0> say_hello_multiple_times(10 / 2, "Elixir")
Hello Elixir!
Hello Elixir!
Hello Elixir!
Hello Elixir!
Hello Elixir!
=> 5
```

Once you define arguments for a method, they become _required_ when you invoke
or call the method. What happens when you don't pass in the required argument to
an argument that expects a certain number of parameters?

```ruby
def say_hello_multiple_times(count, name)
  count.times do
    puts "Hello #{name}!"
  end
end

say_hello_multiple_times(10 / 2)
```

Error message:

```text
ArgumentError (wrong number of arguments (given 1, expected 2))
```

Similarly, a method defined to accept one argument will raise an error if
called with more than one argument.

```ruby
def greeting(name)
  puts "Hello, #{name}!"
end

greeting("Maria", "Ruby") # The method accepts 1 argument and I supplied 2.
# > ArgumentError: wrong number of arguments (2 for 1)
```

## Define a Method That Uses Default Arguments

It sure is a bummer when our method can't run because we failed to provide
an argument. We can get around this by telling Ruby to set a value
as default. If we leave out the argument, Ruby knows how to help
us. If we consciously pass the value, Ruby overrides its default.

Let's fix our broken example from above:

```ruby
def say_hello_multiple_times(count, name)
  count.times do
    puts "Hello #{name}!"
  end
end

say_hello_multiple_times(10 / 2)
```

We get an `ArgumentError` like we did when passing too many arguments.

Using a default argument we can provide a default value for `name` in
the event that an argument isn't provided. Default arguments are included
after the parameter name and an `=` as seen below for the `name`
parameter:

```ruby
def say_hello_multiple_times(count, name="Generic Ruby Programmer")
  count.times do
    puts "Hello #{name}!"
  end
end

say_hello_multiple_times(1 * 1)
```

Returns:

```text
irb(main):047:0> say_hello_multiple_times(1 * 1)
Hello Generic Ruby Programmer!
=> 1
```

## Conclusion

To create dynamic functions in Ruby, pass in arguments, which are
stored as _parameters_ within the body of the method. In the body,
we use those _parameters_ to "grab hold of" and use the data that
were passed in as arguments.

This gives us a lot more flexibility to maintain efficient codebases.

## Resources

[Difference between Argument and Parameter in Ruby on Rails](http://rorguide.blogspot.com/2011/06/difference-between-argument-and.html)
