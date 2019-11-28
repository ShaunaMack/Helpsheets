# Loops

Control flow in code means we are able to direct which lines of code needs to be executed and in which order. We have already explored sequential flow which is just running one line of code after another. And we have also done selection flow which was our if, unless, and case statements. Now lets take a look at repetition flow also know as loops.

Loops allows us to repeat a process over and over again until a certain condition is met and the program determines it is ok to exit the loop. Ruby has several different loops that can be used in different circumstances.
while loop - executes as long as the given conditional is true
until loop - opposite of the while loop
for loop - executes over a specific number of items within a collection (array or hash)

Lets think about if we needed to fill a jar using a mug.
Setup example of an empty jar and ask the class how many mugs of water it will take to fill it. We should get a variety of answers but in the end we have no certain idea how many it would take. But we could use some logic (a conditional) that first checks if the jar is full of water and if it is not to add a cup of water.
Ok working off our real world example lets turn this into code.
jar_size = 12
jar_empty= true
cups_added = 0

``` ruby
while jar_empty
  cups_added = cups_added + 1
  puts “Added ＃{cups_added} cup(s) of water”
  if cups_added >= jar_size
    jar_empty= false
  end
end

puts "The jar is full"
```

This is the syntax for a while loop. We use the keyword while to declare that loop followed by a conditional. Each time the loop runs we call this an iteration. As long as that conditional remains true the loop will continue to iterate, so inside of our loop we must adjust variables so that at some point this loop will return false and carry on executing the rest of our code. Finally to declare the end of the loop we have to use the end keyword.

If we didn’t adjust any variables within the loop we could create what is known as an infinite loop. Which is loop that never ends. Let’s create an infinite loop on purpose. Remember to shut down our code manually from the CLI we can use the keyboard command ctrl + c, which we will need in this case because our code will run forever.

``` ruby
iterations = 0
while true
    iterations += 1
    puts "Iteration ＃{iterations}"
end
```

When we run our code we continue to get “Iteration {x}” printed to the CLI until we manually end the process. Also notice just how many lines printed to your CLI. Wow! Our computers can run code really really really fast.
Before we move on and explore the other loops ruby gives us lets take a look at two keywords we can use within a loop to control its behaviour. First lets look at the break keyword.
The break keyword will automatically exit the loop no matter if the conditional is still true or not. Lets see this in action by using our infinite loop…

``` ruby
iterations = 0
while true
    iterations += 1
    puts "Iteration ＃{iterations}"
    break
end
```

This loop only iterates one time because we immediately encountered the break keyword within the loop. The other keyword we can use within a loop is the next keyword. This keyword will skip to the next iteration within the loop as soon as it is executed.
Lets use this keyword to only print out the even iterations within our infinite loop…

``` ruby
iterations = 0
while true
    iterations += 1
    if iterations % 2 != 0
        next
    end
    puts "Iteration ＃{iterations}"
end
```

Success! That is because the puts method never has a chance to run when our iteration is an odd number because the next keyword is executed. When this happens no further lines of code are executed within that iteration of the loop and the loop proceeds to it’s next iteration.
Alright since we have a handle on while loops lets take a look at an example of a for loop.
For loops are used for iterating over a collection (array, hash) of items…
cities = ["Sydney", "Brisbane", "Melbourne"]

```ruby 
for i in cities
    puts i
end
```

If we run this code we see each city being printed out to our CLI.
Lets break down exactly what is happening…
First we use for keyword to declare we are starting a for loop, then we give the name of a variable, in this case we named our variable i but we could have named it anything we wanted. During the for loop the value of that variable will change to each item within our collection. Then we had to declare which collection we are running this loop on - we do that with the in keyword and the name of the collection. Finally just like the while loop we must use the end keyword to declare the end of the loop.
This loop iterated 3 times. One for each city in our collection.
What if we wanted to run a loop not on a collection but just for a certain amount of iterations. We could use a while loop to accomplish this…
iterations = 0

``` ruby

while iterations < 5
iterations += 1
puts iterations
end
```

This loop will iterate 5 times but really a while loop is intended when we don’t know the intended number of iterations. A for loop is better suited when we do.

``` ruby
for i in 1..5
    puts i
end
```

This will also run exactly 5 times but what is this strange syntax of 1..5? In Ruby this is called a range.
Ranges in ruby allow us to express a sequence of values. The range we used in the for loop allowed us to express the numbers 1, 2, 3, 4, 5 in that order.
If we used 3 dots instead of 2 we express a sequence of values not including the last. Lets try it out in our loop…

``` ruby
for i in 1...5
    puts i
end
```

Brain Teaser Questions:
* Array has some methods which do not mutate the array. List them
* Can Array hold mixed data types in ruby??

