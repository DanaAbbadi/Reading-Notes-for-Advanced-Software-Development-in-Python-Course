# Snake Game 

You can find the implementation of the game and the full code in my repo [here](https://github.com/DanaAbbadi/snake-game)

The is a tutorial to learn how to create a snake game using python.

If you are not familliar with curses, check out my notes [here](https://danaabbadi.github.io/Reading-Notes-for-Advanced-Software-Development-in-Python-Course/curses) 



**The game implementation is divided into parts:**

1. Initializing Game Screen
2. Initialize snake and apple initial positions
3. Specifying Game Over Conditions and Scoring
5. Playing the Game with the game logic

## Part 1: Initializing Game Screen

* Import Libraries: 

        import random
        import curses
        import time


* Initilize the screen using curses 
  
        sc = curses.initscr()

* Set height and width of the window
  
        h, w = sc.getmaxyx()

* Return a new window, whose left-upper corner is at (0, 0), and whose height/width is h/w.
  
        win = curses.newwin(h, w, 0, 0)

* Initiate the keyboard to take the user’s input for the game.

        win.keypad(1)

* Set the cursor mode to be invisible in the screen.
  
        curses.curs_set(0) 



## Part 2: Initialize snake and apple initial positions

* Initiliazing the positions is done by setting the snake_head and position with a list that represnts positions on the screen.

* snake_head is the first element in snake_position, Snack_head[0] controls up and down
snake_head[1]: controls left and right

        snake_head = [10,15]
        snake_position = [[15,10],[14,10],[13,10]]
        apple_position = [20,20]
        score = 0

        win.addch(apple_position[0], apple_position[1], curses.ACS_DIAMOND)
        key = curses.KEY_RIGHT
        button_direction = 1


* **win.addch()** will add a diamond like symbol in the game screen according to specified apple position.
* **key** will represnt the user input, its initial value is to the right, so the snake will start moving to the right.
* **button_direction** represnts direction:
   0: left, 1: Right, 2: Down, 3: Up

## Part 3: Specifying Game Over Conditions and Scoring

* Game will end if snake collide with one of the game window boundaries or if snake collides with itself.

        def collision_with_boundaries(snake_head):
            if snake_head[0]>=h-1 or snake_head[0]<=0 or snake_head[1]>=w-1 or snake_head[1]<=0 :
                return 1
            else:
                return 0

        def collision_with_self(snack_position):
            snake_head = snake_position[0]
            if snake_head in snake_position[1:]:
                return 1
            else:
                return 0

* if either function returns 1, the game will end.

* if the snake eats the apple: add unit to its head, and change apple position to a random one
  
        def collision_with_apple(score):
            apple_position = [random.randint(1,h-2),random.randint(1,w-2)]
            score += 1
            return apple_position, score

## Part 4: Playing the Game

In this game we will use four keyboard buttons, ‘up’, ‘down’, ‘left’ and ‘right’. To get a user input from keyboard we need to use win.getch() function.

    win.border(0)
    win.timeout(100)

    next_key = win.getch()
    if next_key == -1:
        key = key
    else:
        key = next_key

* **win.border(0)** will create a border around our game screen.

* **win.timeout(100):** If delay is positive, then read blocks for delay milliseconds: will wait for an input from the user, if there is no input, will return -1

* **window.getch([y, x]):**  Get a character. Note that the integer returned does not have to be in ASCII range: function keys, keypad keys and so on return numbers higher than 256. In no-delay mode, -1 is returned if there is no input, else getch() waits until a key is pressed.

#### Game Logic

Now we will see the logic to move snake and eat apple. According to the game rules, snake will continue to move in the same direction if user do not press any button. Also snake can not move backward. In case user press any button, we need to update snake head’s position. 

    if key == curses.KEY_LEFT and prev_button_direction != 1:
        button_direction = 0
    elif key == curses.KEY_RIGHT and prev_button_direction != 0:
        button_direction = 1
    elif key == curses.KEY_UP and prev_button_direction != 2:
        button_direction = 3
    elif key == curses.KEY_DOWN and prev_button_direction != 3:
        button_direction = 2
    else:
        pass

    prev_button_direction = button_direction

    if button_direction == 1:
        snake_head[1] += 1
    elif button_direction == 0:
        snake_head[1] -= 1
    elif button_direction == 2:
        snake_head[0] += 1
    elif button_direction == 3:
        snake_head[0] -= 1




Next there are two situations. One, in next step snake will move to a new position and second, in next step snake will eat apple. In case snake only moves to a new position, we will add one unit at it’s head and remove one unit from its tail according to the pressed direction. Another situation, if snake eats apple then we will add one unit at snake’s head and do not remove from it’s tail. We will also display a new apple at different location.

* If the snake ate the apple:

        if snake_head == apple_position:
                apple_position, score = collision_with_apple(score) 
                snake_position.insert(0, list(snake_head))
                a.append(apple_position)
                win.addch(apple_position[0], apple_position[1], curses.ACS_DIAMOND)

* if the snake is just moving around:
  
        else:
            snake_position.insert(0,list(snake_head))
            last = snake_position.pop()
            win.addch(last[0], last[1], ' ')



* Ending the game:
  
        if collision_with_boundaries(snake_head) == 1 or collision_with_self(snake_position) == 1:
                break

* Display the snake
  
        win.addch(snake_position[0][0], snake_position[0][1], '#')
