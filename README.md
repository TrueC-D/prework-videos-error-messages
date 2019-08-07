# Error Messages

## Learning Goals
+ Describe the importance of error messages in computer programs
+ Identify the different types of error messages
+ Use an error message to debug an application 
+ Use the rubber ducking technique to debug an application
+ Explain why error messages are a good thing, rather than a bad thing, when developing applications

## Outline

NOTE: For this video, you can work in the IDE with a single ruby file

+ In the video, well discuss error messages. As a computer user, you're probably used to an error message being bad news - this means that maybe you did something wrong or something you tried didn't work.
+ But as a programmer, error messages are a really good thing. Any non-trivial program that you write is going to have error messages. We'll look at three different types of error messages you're likely to see, as well as what to do when you encounter those.
+ Syntax Error
  + This happens if you write some code that the interpreter can't compile. This usually happens because of a typo, or sometimes some coufusion about how something should work. 
  + Show what happens when you write `if` but not `end` 
  + Show that it's describing what's happening
  + HOW TO DEBUG: Look for the line number -> find the piece that doesn't make sense.
    + TOP TIP: When you write a word that needs to be closed (if, do, def, etc) write `end` immediately, then fill in the middle. 
+ Runtime Error 
  + Once the interpreter makes sure that the syntax looks correct, it tries to run the program. Sometimes here, it runs into something that it can't do.
  + When that happens -> the interpreter raises an error. Some common examples here:
    + NameError
    + NoMethodError
    + ArgumentError
  + HOW TO DEBUG: Go to the linenumber and read the error message carefully. Look for misspellings or values that don't make sense. 
+ Logical Error
  + By far the hardest to debug - this is when you were expecting something to happen, and it just didn't happen
  + I want to print out a name, but instead nothing prints out
  + HOW TO DEBUG: Read through your code, line by line, and explain out loud what it's doing. This technique is called "rubber-ducking" 
