# Ruby Tic Tac Toe
Tic Tac Toe is not a complicated game. Coding it, however, especially when you are just starting to learn a language, is hard. Here I will write a detailed step-by-step of each lab done on the Learn platform.

### Lab 1: Welcoming the player.
I needed to create a script that output a welcome message whenever someone ran the script. Seems simple? It kind of is.

```ruby
puts "Welcome to Tic Tac Toe!"
```

`puts` is short of *output string,* as in, write something. Strings are can be anything, but since this is a sentence (not a variable,) we use "" around them to signify that.

It is important to note that in Ruby there are six different types of data: booleans, symbols, numbers, strings, arrays, and hashes.

### Lab 2: The Tic Tac Toe board
Now I needed to create a variable that allowed me to set "X" and "O" on 9 positions (that represent the board). For that we need an array, which is a container where you can store variables. Arrays are created by stating `array = [variable1, variable2,..., variablen]`. Since we need the array to contain strings, we will set each position to be `" "`.

```Ruby
board = [" "," "," "," "," "," "," "," "," "]
```

`board` represents the variable containing the board positions.

### Lab 3: Printing a Tic Tac Toe Board
Methods are the way for Ruby to know how to manipulate things in your program. They are a way to mold variables to what you want them to do. The assignment was to `print`, or output, a generic Tic Tac Toe board in ASCII, which just means standard keyboard characters. For that we are going to define the `display_board` method and then we are going to `print` it.

```Ruby
def display_board
  print "   |   |   \n-----------\n   |   |   \n-----------\n   |   |   \n"
end
```

`def` simply means the start of the definition of a method. `\n` is the way of creating a line break and not having to use `print` 5 times. Finally, `end` is just the way to finalize the process of defining `display_board`.

The output will be:
```
   |   |   
-----------
   |   |   
-----------
   |   |   
```
