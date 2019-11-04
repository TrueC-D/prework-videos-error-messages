# Error Messages

## Learning Goals
+ Describe the importance of error messages in computer programs
+ Identify the different types of error messages
+ Use an error message to debug an application
+ Use the rubber ducking technique to debug an application
+ Explain why error messages are a good thing, rather than a bad thing, when developing applications

## Lesson
<iframe width="100%" height="720" src="https://www.youtube.com/embed/cGgRsGYkByI?rel=0&showinfo=0" frameborder="0" allowfullscreen></iframe>

+ Hi guys, it's Ian from Flatiron School. In this video, we're going to talk all about one of my favorite topics - error messages. Our learning goals for the video - after watching you should be able to:
+ Describe the importance of error messages in computer programs
+ Identify the different types of error messages
+ Use an error message to debug an application
+ Use the rubber ducking technique to debug an application
+ And to explain why error messages are a good thing, rather than a bad thing, when developing applications
+ As a computer user, you're probably used to an error message being bad news - this means that maybe you did something wrong or something you tried didn't work.
+ But as a programmer, error messages are a really good thing. Pretty much any program that you write is going to have errors. And this is really important - if your program didn't have any errors, that means you'd literally have nothing to program, you'd have no work to do.
+ Today we'll look at three different types of error messages you're likely to see, as well as what to do when you encounter those. Most of the errors that you'll see will fall into one of these three buckets.
+ Those three types are: Syntax Errors, Runtime Errors, and Logical Errors
+ The first type is a syntax error
  + This happens if you write some code that the interpreter can't compile. This usually happens because of a typo, or sometimes some confusion about how something should work.
  + For example, in Ruby, when I write the word `if`, it's required that I also write `end
  + Here in the Learn IDE sandbox, I have a file called `app.rb` with the word `if`
  + If I run this program now, we'll see `syntax error: unexpected end of input, expecting keyword end`
  + As I mentioned before, if you're not used to seeing error messages, this might look scary, but this is actually awesome. The computer is doing it's best job to describe what the problem is, and it's telling you what line number it's found the problem at. See the line number there on the side?
  + Likewise, if I write `"Barbara" = name` -> we see a great error message: `app.rb:1: syntax error, unexpected '=', expecting end-of-input
"Barbara" = name`
  + So the best way to debug this type of error message is to go to the line number, and read that line, and try to reason about what the problem might be. Describe out loud what it is that line is trying to do. In my case, I would say "I'm trying to make a variable called name and assign it a value of 'Barbara'"
  + Now, if I read this line, I will hopefully realize that I have this backwards - oops, I need to write `name = "Barbara"` to make this work. So now, I can make that change, run again, and now no news is good news.
  + This is sometimes called "Rubber Duck Debugging" - some programmers literally keep a rubber duck on their desk, and when they're stuck, they explain what they're trying to do to the rubber duck line by line. By walking through the code and checking all of your assumptions, you can actually find more bugs and figure out what's going wrong in your application.
  + One other tip to help avoid syntax errors: When you write a word that needs to be closed by end (if, do, def, etc) write `end` immediately, then fill in the middle. That way, you'll always have the closing ready to go and you don't have to go back and find it.
+ The next type of error we might see is a Runtime Error.
  + Once the interpreter makes sure that the syntax looks correct, it tries to run the program. Sometimes here, it runs into something that it can't do.
  + When that happens, the interpreter raises an error. There are a bunch of different types of these.
    + A NameError - this occurs when Ruby sees a bare word that it doesn't recognize. If I type `dog` at the top of the file - Ruby will say "hey, I don't know what that is, that's not defined. I'm looking for either a local variable or method named dog, but I don't have one" Hence, when we run this, we see this error: app.rb:1:in `<main>: undefined local variable or method 'dog' for main:Object (NameError)`
    + To debug this, we simply need to go to the line number and figure out why this thing isn't defined. It could be that we made a typo, or accessed something too early.
    + A NoMethodError happens when we try to call a method on something that doesn't actually have that method. For example: say I'm trying to see the first character of a string. I might try to do something like `"Hello".first` - this looks like it should work. But instead, I see this error: `app.rb:1:in <main>: undefined method 'first' for "Hello":String (NoMethodError)` So, my string just doesn't know what `.first` means. In this case, I'm trying to do something that doesn't make sense. Sometimes, the easiest way to fix this might be to actually define the method.
    + You'll also see this error if a value isn't the right data type. For example: `"9" / 4` will throw a NoMethodError: `app.rb:1:in <main>': undefined method /' for "9":String (NoMethodError)`  because  my "9" is a string in this case, and strings don't know how to do division.
    + Finally, you will see this a lot if you end up with a nil value in your program. So let's say you have something conditionally defined somewhere - we'll do a really contrived example in this code sample:
    ```ruby
    number = 10
    if number > 11
      name = "Bob"
    end
    name.upcase
    ```
    + This throws an error: `app.rb:5:in <main>': undefined method upcase for nil:NilClass (NoMethodError)` So, to fix this, we don't want to define the upcase method - the problem here is that `name` is nil, and we can't call `upcase` on our nil value. So we need to figure out how to avoid that nil.
    + Another really common error type is an Argument error - this happens when you give a method either too many or too few arguments. This is a really nice one to debug, because it will tell you pretty much exactly what the problem is.
    + Take the reverse method for a string - it doesn't take any arguments. `"Hello".reverse` returns the reversed string. If I pass an argument to that method - it's not going to be pleased. The good news - it points me write to the line number and says how many arguments it was expecting, and how many I gave it. `app.rb:1:in reverse': wrong number of arguments (given 1, expected 0) (Argument` - in this case, I gave 1 argument, but the method wanted zero.
  + If this is a method that you haven't defined, like the reverse method, you need to change how you're calling the method. If you did define this method yourself, then you can update your method definition if needed. A lot of times, when working through a lab on Learn, you'll see this error from the test suite, and that means that the test wants you to add additional argument options to your method definition.
+ Our last big bucket of errors are logical errors - this is when you were expecting something to happen that didn't happen. So this is really a bug in your program - I ran it, I thought it would do something, but it didn't do the thing.
  + These are by far the hardest to debug - because you get no information.
  + Say I want to write a program that prints out a name.
  ```ruby
  name = "Bob"
  ```
  + If I run this - well, I didn't get any errors, but it also didn't do what I wanted. So this is a logical error somewhere.
  + The best way to debug this is to use the rubber-duck technique -  read through your code, line by line, and explain out loud what it's doing. Remember as well, if you still can't find the bug, you can use the Ask a Question feature on learn and get a friend to help you.
+ So that's pretty much it for error messages. Just to recap what we talked about:
+ We talked about the importance of error messages in computer programs - they tell us what the problem is! They can point us exactly to the line number where the issue is.
+ We identified the different types of error messages - Syntax Errors, Runtime errors, and logical errors, plus a bunch of different types of runtime errors.
+ We used all three types of errors to debug our application
+ We talked about rubber ducking and how we can use that to get ourselves unstuck
+ And finally, we talked a lot about why error messages are a good thing, rather than a bad thing, when developing applications. If you have an error in your program, that means that you still have some work to do, and that's a really good thing.
+ So hopefully errors are a little bit less scary now. Thanks for watching and happy coding!
