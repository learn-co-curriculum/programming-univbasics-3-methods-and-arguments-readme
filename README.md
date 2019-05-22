# Ruby Method Arguments

## Learning Goals

- Describe the functionality of arguments
- Define a method that accepts arguments
- Recognize the difference between arguments and parameters

## Introduction

In the real world, many interactions have a "template" behavior that is applied
to every interaction, but these behaviors change only slightly depending on a
tiny factor.

For example, if you go to a coffee shop, they take down **your** name to call
you up when your order is ready. If you visit a doctor's office, they may call
**your** name when it's your turn to be seen. Methods can also be written to
have a "template" of shared activity, but this activity can be changed just a
little bit when necessary.

The particular bits that make the change are called "arguments."

## Describe the Functionality of Arguments

When we log into email, social media, or any other user-based platform, what do
we normally see after logging in?

Our name somewhere on the account, right?

So far, we've only discussed how to create methods that return static
information. For example:

```ruby
def greeting
  puts "Hi, Ruby programmer!"
end

greeting
#=> Hi, Ruby Programmer
```

As amazing as this method is, it's _static_. It hard-codes, or directly
specifies, the name of the person we are greeting as `"Ruby programmer"`. If we
wanted to build a method that can greet _anyone_ by name, we'd need to be able
to add input into the body of the method.

Just like with a real-world greeting, we'd want our method to be more _dynamic_,
more abstract, and _more re-usable_. Remember our DRY (Don't Repeat Yourself)
principle? The method should maintain the elements that will always be the same,
no matter whom we greet, but allow us to change, or swap out, the name of the
person we are greeting. This is considered _dynamic_, or able to adapt to change
or progress, as opposed to _static_, which in the case of programming means
"hard-coded".

## Define a Method That Accepts Arguments

Now that we see the limitations of static methods, how do we take the information
we know about arguments and apply them to real-world scenarios like that of a
doctor's office or a coffee shop?

To define the arguments you expect a method to take, you specify parameters in the
line that starts with `def`.

For example, if we want to write a method called `greeting_a_person` that
accepts an argument of a person's name, we would do it like this:

```ruby
    #method name      #parameter
def greeting_a_person(name)
  "Hello #{name}"
end
```

As you can see in the example above, the `name` parameter now holds a name, which
is being passed in as an argument its invocation.

Arguments that are passed into methods create new _local_ variables that can be
used within the _scope_ of the method. We call these local variables _parameters_.
When you name an argument, you are defining what word you want to use to access
that data, just like when you create a variable. Arguments follow the same rules
as local variables: they can be any word that starts with a lowercase letter and
they should be as descriptive of the data as possible.

In our `greeting_a_person` method example, we are saying: When you call the
`greeting_a_person` method with an argument of `"Maria"`, set a variable `name`
equal to the value of `"Maria"`.

Let's open up IRB and try this out! First, take the `greeting_a_person` code
sample and paste it into your command line. Once that has been entered, you can
test out the method like this:

```bash
greeting_a_person("Maria")
# => "Hello Maria"
```

or this:

```bash
name = "Maria"
greeting_a_person(name)
# => "Hello Maria"
```

This same pattern works for passing in as many arguments as you want by adding a
comma (`,`) between each argument you want to pass in. Let's try creating a
method that accepts two arguments: a person's name and their programming
language of choice.

```ruby
  # method name      first_parameter, second_parameter
def greeting_programmer(name, language)
  puts "Hello, #{name}. We heard you are a great #{language} programmer."
end

greeting_programmer("Maria", "Ruby")
# > Hello, Maria. We heard you are a great Ruby programmer.

greeting_programmer("Steven", "Elixir")
# > Hello, Steven. We heard you are a great Elixir programmer.
```

Once you define arguments for a method, they become _required_ when you invoke
or call the method. What happens when you don't pass in the required argument?
When an argument with a value is not passed in, you get an `ArgumentError`.
Here's an example:

```ruby
def greeting(name)
  puts "Hello, #{name}!"
end

greeting # We call the method without a value for the argument `name`
# > ArgumentError: wrong number of arguments (0 for 1)

greeting(name) # If we call the method without setting a value for name, or passing in a value for the argument `name` we see:
# > NameError: undefined local variable or method `name' for main:Object
```

The word, in this case `name`, that we use as a parameter in the method
signature becomes a local variable within the method. Through that variable, we
can reference the value of the argument inside the body of the method.

The number of arguments, or inputs, an operation expects is called _arity_. The
_arity_ of addition is two: we expect two numbers to add. The `arity` of
`greeting` is one: we told ruby to expect one argument for its parameter, `name`
and by golly, Ruby will get mad if we break our promise to it.

A method defined to accept one argument will raise an error if
called with more than one argument.

```ruby
def greeting(name)
  puts "Hello, #{name}!"
end

greeting("Maria", "Ruby") # The method accepts 1 argument and I supplied 2.
# > ArgumentError: wrong number of arguments (2 for 1)
```

Again, the arity of greeting is one, by providing it two arguments, Ruby gets
upset. By default, all arguments defined in a method are required in order to
correctly invoke (or "call", or "execute") that method and method arguments
create local variables for you use when the method is actually called.

## Recognize the Difference Between Arguments and Parameters

Now that we know how to define a method with arguments, let's define the
difference between _arguments_ and _parameters_, which are subtle, but important
to know when working with or discussing code.

A _parameter_ is a value that the method expects you to pass when you call it.

An _argument_ is the value you pass to a method when you call the method.

In simpler words, parameters appear in method definitions; arguments appear in
method calls. For example:

```ruby
def greeting(parameter)
  puts "Hello, #{parameter}!"
end

greeting(argument)
```

In the `greeting` method, the variable `parameter` is the parameter for the
method and when calling the method, the value passed for `argument` is the
argument.

## Conclusion

In order to create dynamic functions in Ruby, pass in arguments, which are
stored as _parameters_ within the scope of the method, that can be used in the
body of the method.

This gives us a lot more flexibility to maintain efficient code bases, as well
as to apply real-world concepts when building our programs. You'll learn more
about arguments in future lessons.

## Resources

[Difference between Argument and Parameter in Ruby on Rails](http://rorguide.blogspot.com/2011/06/difference-between-argument-and.html)
