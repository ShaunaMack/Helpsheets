# Accessing Data inside objects 

### Everything is an object right? Thats right!

But depending on the data type the way we access that data changes. Hashes have key/value pairs and classes attributes.

#### Lets start at how we access data inside an array:
``` ruby
  developers = ["Kristy", "David", "Steph"] 
  # As arrays are indexed at zero, if we wanted the first element...
  developers[0] #"Kristy"
  developers[1] #"David"
  developers[2] #"Steph"
```
Seems simple enough right? What about if we had a 10k long list of developers, we wouldn't really want to do developers[n] 10k times would we?

**Of course not!** Thats why we have loops.

``` ruby
 developers = ["Dax", "Adam", "Adsy", "Asmaa", "Aurelia", "Caleb", "Dallas", "David", "Harrison", "Jeb", "Kristy", "Oscar", "Phil", "Ryan", "Shauna", "Steph", "Wilson"]

 # There are two ways go print each developer's name.
 # The solution is iteration (which means to go over)
 # When we say iterate over an array we mean go over each element of it
 

 # Remember syntax:
 #  name is each value inside the array 
 #  developers is the array we are iterating through
 for name in developers do
  puts name
 end 

 # or

 developers.each do |name|
  puts name
 end

 #two ways to do the same thing!

```

Arrays are cool, but limited in the amount of data each element has. 

#### What about hashes?
``` ruby
  # Hashes look like this:
  person = {
    name: "glen",
    age: 27,
    hair: "brown",
  }
```

If I wanted to get this person's name or age I would do something like this:
``` ruby
  person[:name] #"glen"
  person[:age] #27
  # Remember that we start with calling the variable which in this case is called person, then in square brackets the key that we are looking for
```

What if I had an **list** *(array)* of **people** *(hashes)*. What would that look like?

``` ruby
people = [
  {
    name: "Glen",
    age: 27,
    eyes: "blue"
  }, {
    name: "Nav",
    age: 26,
    eyes: "brown"
  }
]

# Just like in our previous example, each person in people is an element of an array, how do we access an element in array?
people[0]
people[1]

# If we tried that in IRB that will return the entire hash, but what if I only wanted a name?

people[0][:name] # "Glen"
people[1][:name] # "Nav"

# Because people is an array and our people are nested inside we need to access each element first then its key.

# Reading the line from left to right: 
people # we grab our people array,
[0]    # access the 0th element,
[:name] # then call on the name key to access it's value

# putting it all together...

people[0][:name] # => "Glen"
```

Again if I had an array of hundreds of people I wouldn't want to print each line individually so I can create a loop to iterate over each one. So if we can nest our objects inside of an array, we can iterate over it and print our data

``` ruby 
  people.each do |person|
    puts "My name is #{person[:name]}"
    puts "My age is #{person[:age]}"
  end
```

#### Now Classes

So hashes can hold all these different key/value pairs what do we need classes for? For one, classes come with some built in security; data can only be shown and changed if we allow it to be changed. Secondly classes will allow us to do some nifty things under the hood. But this sheet isn't about that, this is just how to access the data. So let us start with that

``` ruby
  # lets start by creating the class and making an instance of it

  class Developer
    def initialize(name, age, hair)
      @name = name
      @age = age
      @hair = hair
    end
  end

  dev = Developer.new("Glen", 27, "Brown")
```

If I wanted this dev's details then I can just ```puts dev``` right?

If you are trying this at home, you would see something like this:
``` ruby
  dev = Developer.new("Glen", 27, "Brown")
  puts dev
  # => <Developer 0x000013893a33>
```
That didn't work as intended, did it? The reason is because when we puts a class, what is output is the hexadecimal representation of that data. So we need another way to output their details.

To output a class value such as name, age etc we use the same notation as when we call chain methods. Can you think why that is?
``` ruby
  puts dev.name
  # => Error! name doesn't exist
```

But there is one thing we are forgetting! Remember how I brought up security, if we want to read or write data on a class we need to express that in our class definition.

So lets do that.

``` ruby
  class Developer

  # For when we only want to read a value
  attr_reader :name
  # For when we only want to write a value
  attr_writer
  # For when we want to read and write values
  attr_accessor

    def initialize(name, age, hair)
      @name = name
      @age = age
      @hair = hair
    end
  end

  dev = Developer.new("Glen", 27, "Brown")
  puts dev.name
  # => "Glen"
```

#### Putting it all together

``` ruby
  developers = [
    <Developer 0x00003452b34>, # Remember these are class instances
    <Developer 0x000089231d3>,
    <Developer 0x00010004356>,
    <Developer 0x00011005832>,
  ]

  # So this is an array of instances of the developer class.
  # Using what we've learnt about iterations and calling data from classes how would we get each name from developers?

  for dev in developers do
    puts "This developer's name is #{dev.name}"
  end

  # or 

  developers.each do |dev|
    puts "This developer's name is #{dev.name}"
  end
  
```

