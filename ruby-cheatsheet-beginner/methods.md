# Methods

## What

Methods are repeatable and executable parts of our code that we can call anywhere in our code. Instead of writing the same or similar blocks of code we can re-write this as a method and call that method when we need it.

Given the following code

``` ruby
  puts 'Maths is fun'
  puts 'Lets play a game'
  num1 = rand(1..100)
  num2 = rand(1..100)
  puts "What is #{num1} + #{num2}?"
  input = gets.chomp.to_i
  puts "You are #{input == num1 + num2 ? "correct" : "wrong"}!"

  puts "That was fun, again!"
  puts 'Lets play a game'
  num1 = rand(1..100)
  num2 = rand(1..100)
  puts "What is #{num1} + #{num2}?"
  input = gets.chomp.to_i
  puts "You are #{input == num1 + num2 ? "correct" : "wrong"}!"
  
  puts "That was fun, one last time!"
  puts 'Lets play a game'
  num1 = rand(1..100)
  num2 = rand(1..100)
  puts "What is #{num1} + #{num2}?"
  input = gets.chomp.to_i
  puts "You are #{input == num1 + num2 ? "correct" : "wrong"}!"

  puts "Bye!"
```

Thats an awful lot of repeated code. All this manual typing can lead to user errors and it just looks plain ugly. Let's clean this up slightly.


``` ruby
  def math_game()
  puts 'Lets play a game'
  num1 = rand(1..100)
  num2 = rand(1..100)
  puts "What is #{num1} + #{num2}?"
  input = gets.chomp.to_i
  puts "You are #{input == num1 + num2 ? "correct" : "wrong"}!"
  end

  puts 'Maths is fun'
  math_game()
  puts "That was fun, again!"
  math_game()
  puts "That was fun, one last time!"
  math_game()

  puts "Bye!
```

So now we have moved all of our code into one place, if we needed to change our code we would only need to change it once inside the method instead of each time our code is executed. This limits our possible errors.

Ok so what does everything mean? Let's look at each component of the method step by step.

``` ruby 
  # def is the keyword that begins the method.
  # Now ruby knows you want to make a method
  def

  # Next is the name of the method we want to create.
  # Make sure your method name describes what is happening
  def sum_two

  # Inside parenthesis are our expected values to be passed each time the method is called. These are called arguments or parameters.
  # If there are no values then we can leave it blank
  def sum_two(num1, num2)

  # Methods are special in that they can give back a value when they are called.
  # In this example we are giving back the value of num1 plus num2.
  # Returning will stop the method in its track and not execute any code below.
  def sum_two(num1, num2)
    return num1 + num2

  # Always end your methods!
  def sum_two(num1, num2)
    return num1 + num2
  end

  # We can assign these returned values into variables. Can you think of places where this would be useful? There are many!
  # Just like defining a method, if there are no arguments needed we just pass empty parenthesis
  big_number = sum_two(100, 200)
  puts big_number
    => 300

  # Arguments can also be functions. This might look confusing but take it step by step.
  # Here we are taking two rand(1..100). These rand methods will execute and return their own random number before the sum_two executes.
  # sum_two will wait for its parameters to be ready before it starts is own thing.
  another_number = sum_two(rand(1..100), rand(rand(1..100)))
```

## How

Now that we know what methods look like and how to call them, lets have a look at how methods are scoped.

``` ruby
  def secret_generator
    my_secret = "I like pie"
    return "you cannot know my secret"
  end

  puts my_secret
    => unknown local variable my_secret
```

In this example, we aren't able to access my secret outside of the method. This is because variables created inside a method are scoped to only be used inside the method UNLESS we return the variable.

``` ruby
  def secret_generator
    my_secret = "I like pie"
    puts "you cannot know my secret"
    return my_secret
  end

  puts my_secret
    => "I like pie"
```

## Where

Often, we may need to call a method INSIDE another method. When we are writing our methods we need to make sure that they are written above the instances of where they are called.

``` ruby 
  def get_user_input
    puts "Options: "
    puts "1. Feed Cat"
    puts "2. Pet Cat"
    puts "3. Train Cat"
    puts "4. Quit"
    puts "Select a number"
    return gets.chomp.to_i
  end

  def do_option(input)
    case get_user_input()
    when 1
      feed()
    when 2
      pet()
    when 3
      train()
    when 4
      return true
    else
      puts "I don't understand. Try again!"
    end
  end

  def care_loop
    quit = false
    until quit == true do
      # This is called circuit breaking logic. In our do_option method there is only a true return. So when it is called it will either return true (which means quit) or nil.
      # The piping will instead give false if not previously true.
      # Research circuit breaking logic.
      quit = do_option() || false
    end
  end

  care_loop()
```

There is a lot going on here. So take some time to review the code and figure out what is happening.

I am only calling 1 function in my code, the care_loop, which is calling methods inside itself.

## Terms to remember

Term | Meaning
--- | ---
Local Variable | Variables created inside methods are only available inside methods.
Return | Each method can give back a value and this is how we can access those local variables
def; end | How we start and end a method
DRY | Don't Repeat Yourself
