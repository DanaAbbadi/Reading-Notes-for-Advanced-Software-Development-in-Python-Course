# Curses

The curses is a library that can be used to create text user interface application. It is terminal controlled library i.e. the code written using curses can only be run through terminal.

Display terminals support various control codes to perform common operations such as moving the cursor, scrolling the screen, and erasing areas.

#### Starting and ending a curses application ¶

First initialize curses. This is done by calling the *initscr()* function, which will determine the terminal type, send any required setup codes to the terminal, and create various internal data structures.

If successful, initscr() returns a window object representing the entire screen.

    import curses
    stdscr = curses.initscr()

#### Curses functions:

To turn off automatic echoing of keys to the screen, in order to be able to read keys and only display them under certain circumstances.
    curses.noecho()   

To react to keys instantly, without requiring the Enter key to be pressed

    curses.cbreak() 

To use curses.KEY_LEFT. To get curses to do the job, you’ll have to enable keypad mode.

    stdscr.keypad(True)

Terminating a curses application is much easier than starting one. You’ll need to call:

    curses.nocbreak()
    stdscr.keypad(False)
    curses.echo()

To reverse the curses-friendly terminal settings. Then call the endwin() function to restore the terminal to its original operating mode.

    curses.endwin()


