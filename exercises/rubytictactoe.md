# Ruby Tic Tac Toe
Tic Tac Toe is not a complicated game. Coding it, however, especially when you are just starting to learn a language, is hard. Here I will write a detailed step-by-step of each lab done on the Learn platform.

### Lab 1: Welcoming the player
I needed to create a script that output a welcome message whenever someone ran the script. Seems simple? It kind of is.

```ruby
puts "Welcome to Tic Tac Toe!"
```

`puts` is short of *output string,* as in, write something. Strings are can be anything, but since this is a sentence (not a variable,) we use "" around them to signify that.

It is important to note that in Ruby there are six different types of data: booleans, symbols, numbers, strings, arrays, and hashes.

### Lab 2: The Tic Tac Toe Board
Now I needed to create a variable that allowed me to set "X" and "O" on 9 positions (that represent the board). For that we need an array, which is a container where you can store variables. Arrays are created by stating `array = [variable1, variable2,..., variablen]`. Since we need the array to contain strings, we will set each position to be `" "`.

```Ruby
board = [" "," "," "," "," "," "," "," "," "]
```

`board` represents the variable containing the board positions.

### Lab 3: Printing a Tic Tac Toe Board
Methods are the way for Ruby to know how to manipulate things in your program. I will be defining methods inside this lab description with a `#` in fron of them to prevent confusion, but the do not have said `#` inside the files. They are a way to mold variables to what you want them to do. The assignment was to `print`, or output, a generic Tic Tac Toe board in ASCII, which just means standard keyboard characters. For that we are going to define the `#display_board` method and then we are going to `print` it.

```Ruby
def display_board
  print "   |   |   \n-----------\n   |   |   \n-----------\n   |   |   \n"
end
```

`def` simply means the start of the definition of a method. `\n` is the way of creating a line break and not having to use `print` 5 times. Finally, `end` is just the way to finalize the process of defining `#display_board`.

The output will be:
```
   |   |   
-----------
   |   |   
-----------
   |   |   
```

### Lab 4: Displaying a Tic Tac Toe Board
Now we need to display the board and the "X" and "O" it contains using the array we previously created as a template. In order to define a method that uses a variable, we need to encapsulate said variable inside the definition of the method. Since this is a brand new .rb file, we also need to use the variable `board` again.

```Ruby
board = [" "," "," "," "," "," "," "," "," "]

def display_board(board)
  puts " #{board[0]} | #{board[1]} | #{board[2]} "
  puts "-----------"
  puts " #{board[3]} | #{board[4]} | #{board[5]} "
  puts "-----------"
  puts " #{board[6]} | #{board[7]} | #{board[8]} "
end
```

There are some new things inside this method. For example `#display_board(board)` indicates that the method will use the `board` array. Ruby can output variables into a string, this is done by `#{array[position]}`, in this case. This just means that the variable used will be the one in the position inside the array used. The board will look exactly the same as the one in Lab 3, but it will be able to output "X" and "Y" on the desired location. Bear in mind, values inside the array start with 0, so position 1 will be variable 0 inside the array.

### Lab 5: Tic Tac Toe Move
In this lab, we had to use a CLI (command line interface) to ask the player where he would like to input his move on the board. I needed to make a tiny program that greeted the player, asked for his move and then output that move to the board.

```Ruby
#!/usr/bin/env ruby

require_relative '../lib/move.rb'

puts "Welcome to Tic Tac Toe!"
puts "What would you like to do?"

board = [" "," "," "," "," "," "," "," "," "]
input = gets.strip
index = input_to_index(input)

move(board, index, "X")

display_board(board)
```
`#!/usr/bin/env ruby` simply tells the interpreter that the program should be executed with Ruby. `require_relative '../lib/move.rb'` gives the file access to code we will be using to execute the program. The two `puts` greet the player and ask for input. `board` is there to create the array inside the file. `gets.strip` tells the program to wait for user input, the `strip` part converts the input into a string. `index` contains the input we just received and converts it into a index the board can use. `#move` then inputs an "X" into the board in the location the player said. Finally, `#display_board` displays the board with the "X" in the correct location.

To do all of this, we methods inside the `move.rb` file.

```Ruby
def display_board(board)
  puts " #{board[0]} | #{board[1]} | #{board[2]} "
  puts "-----------"
  puts " #{board[3]} | #{board[4]} | #{board[5]} "
  puts "-----------"
  puts " #{board[6]} | #{board[7]} | #{board[8]} "
end

def input_to_index(user_input)
  user_input.to_i - 1
end

def move(board, input_to_index, character = "X")
  board[input_to_index] = character
end
```

We already know the first method `#display_board`, it is the one we previously created on the last lab. `#input_to_index` takes the input we received using `gets` in `move` and converts it into an integer, as well as subtracting 1 from it (as we previously mentioned, position 1 on the board represents variable 0 inside the array.) Finally, `#move` takes the board and adds "X" in the position the player specified. `board[input_to_index] = character` tells the program to input "X" (`character` on this case) into `board` at the `input_to_index` position we previously got. 
