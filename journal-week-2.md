# daaavid.github.io

####Journal, Week 2
Last week's homework was informative. A bunch of work on tableviews and cells. The SHIELD Hero tracker assignment helped with detail views transitioning from a table view. I'm getting comfortable with additional class relations. The calculator assignment really solidified that concept for me. Seems amazing for keeping things neat and tidy. The calculator app was really easy at first glance, but getting multiple operators in a row working was a pain.

##Calculator
######(a quick and dirty tutorial)



In the calculator app, we were tasked to obviously, make a calculator. The caveat was that we needed to wholly separate the view controller from the actual working guts of the app, which was a relatively novel way of doing things.

So let me walk you, the reader, through a quick run down of this app. Ignore the stuff I collapsed, it's unnecessary for the purposes of the demonstration.

###Storyboard and ViewController

To get started, let's assume you've already set up your storyboard and hooked up your display and all of your numbers and operators up to their respective things that need to be hooked up, like so:

![img](http://i.imgur.com/JjWK4BN.png)

Now, to actually set up what these buttons do. We only need one IBAction for all of the buttons, one IBAction for the operators, and then the clear and equal buttons get their own IBAction because they're special snowflakes.

#####The Number Button IBAction

![img2](http://i.imgur.com/Dfp2XNz.png)

As you can see, I'm not actually pulling out any values from the numbers I'm pressing in this function. We're going to do something a little different. So in this function all we're going to do is set it up so that we can have more than a single digit on the screen at one time. 

So on line 48, we set the display label to be whatever the current title of the sender is (a number). Then, we set our isTyping boolean to true, so that the next time the user presses the button, it'll pass that first if condition on line 42 and just add whatever we typed in to the current string in the display label. (Ex. 4 -> 2 becomes 42, instead of just being 4 and then changing the displayed number to 2.)

#####The Operator Button IBAction

![img3](http://i.imgur.com/0moaycn.png)

In this next function is where we're going to pull out the currently displayed number on the screen and store it in our brain class. Don't worry, we'll be checking out that class soon enough. 

So obviously we know the user is done typing their first number; they've went on and hit an operator, after all. So we can go ahead and set that isTyping bool on line 55 to false. 

On line 56, we pull out the current title of the sender (whatever is hooked up to the button) and set store it in our brain's operatorSign; we'll be using it soon to actually perform an operation. On line 58, we check if there's no value in the brain's first number, and if not, we assign whatever's on the calculator's display (calcDisplayLabel.text!) to our brain's first number storage (brain.firstNumStr).

After the user's pressed an operator and starts pressing numbers again, the logic of our program goes right back to the number IBAction. Easy, right?

#####The Equals Button IBAction

![img4](http://i.imgur.com/8VZF2Ps.png)

This one's split into two different functions. It doesn't have to be if you're just doing single operators (2 + 2 = vs 2 + 2 + 2 + 2 =)

So when the user presses the equals button, we know that they're done entering their second number and are ready to see what 1 + 0 equals. Or whatever numbers they chose. So we know it's okay now to go ahead and pull whatever number's currently displayed on the screen and store it in our brain's second number storage. So, on line 89, we do just that. Just like the last section, CalcDisplayLabel.text! is going to be whatever's currently displaying on the screen, so we grab that and put it in our brain.secondNumStr.

After that, we're cool to start calculating. 

So on line 99, we set that isTyping bool back to false (the user set it back to true when they were typing numbers again). We then declare a new constant, "answer," and set it equal to whatever the brain's calculate function spits out. We then set the calculator's display to the answer as a string, and we're all set. Don't worry about the following stuff!

#####The Clear Button IBAction

![img5](http://i.imgur.com/Rdy7GQH.png)

Before we dive into the brain function, let's check out one last thing in the viewcontroller: the clear button IBAction. This one is short, don't worry!

I split this one into two functions again, just in case we want to clear the stored values outside of pressing the clear button. So all that's happening in the clearButton IBAction is it's clearing off whatever's on the calculator's display, then calling the clearStorValues function on line 109. All that function does is clear out all of the stored values in all of our brainy stuff. Ezpz.

###The Brain Itself

![img6](http://i.imgur.com/G0nRlWd.png)

Alright! Let's do some impromptu surgery and see what exactly is going on in that brain function I keep spouting on about. So lines 13-15 are actually declaring the brain variables we were using in the last few sections. Otherwise, without this declaration, we wouldn't have been assigning anything! Line 16 just sets up our result value. We're explicitly declaring this value _outside_ the calculate function because we're going to use it later on in the brain class. If we just declared it inside of the calculate function, we wouldn't be able to use it outside of that function.

#####The Calculate Function

![img7](http://i.imgur.com/MzNoJjp.png)

Alright, remember when we assigned all that stuff in the view controller? Now we're actually going to use it. 

We start out our calculate function by running the two numbers we assigned values to back in the view controller (firstNumStr and secondNumStr) into our toDouble function in order to make them palatable to actual operators. So we assign the return value of our toDouble function to firstNumber and secondNumber. The next few lines is just a long switch/case statement that does different things based on what our operator was assigned to (back in the view controller).  Not as complicated as it looks!

The calculate function then returns the result to back when we called it in the view controller and puts it up on the display for the user to see.


#####The Other Stuff

![img8](http://i.imgur.com/SlaibEb.png)

The next part is just if you want to be fancy. Back in the viewcontroller, remember when we called the resultAsString function on the answer? This is where the actual function is! 

You've come this far, so I believe in your ability to understand my code! Try to figure out this part yourself! :^)
