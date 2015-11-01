##Simple Swifty Animation
######(a quick and dirty tutorial)

![gif1](http://i.imgur.com/mIh1BId.gif)

Pretty cool, right? Today, I'll be teaching you how to do this sort of slidey widey animation thing.

Let's get started with a brand spankin' new xcode project.

![img1](http://i.imgur.com/YQWah64.png)


--------
![img2](http://i.imgur.com/yhgWCMt.png)

First, we'll take a look at the storyboard. Drag a `Label` in and just stick it anywhere. Go ahead and set up a few constraints so xcode doesn't complain. I used center horizontally and vertically in container.

Head into the viewcontroller and we'll start setting up the code.

--------
![img3](http://i.imgur.com/KR8Lt3j.png)

Set up your label with an `IBOutlet` and then go ahead and make an empty function called `animateLabel` and call it inside of viewDidLoad.

--------
![img4](http://i.imgur.com/5vALjq2.png)

For this tutorial, we're just going to be using one of the built in animation functions: `animateWithDuration`. This is a function of the class `UIView`, so start typing in `UIView.animateWithDuration` inside of the function you just created and let xcode fill in the rest for you.

--------
![img5](http://i.imgur.com/cu5TNFv.png)

Now we'll fill it out. Set your preferred animation duration length (as a double) and your preferred animation duration delay (also as a double). We're not going to worry about options, so just set that to `[]`. Now set the portion after `animations:` up as a closure, like in the image above.

--------
![img6](http://i.imgur.com/Upsd9g1.png)

We're going to be using the frame of our label as a reference point for the animation. Declare a variable and assign it to your label frame. Remember to preface items _inside_ the closure that reference items _outside_ the closure with a `self.`. Closures are weird like that.

--------
![img7](http://i.imgur.com/a6fNka8.png)

Set the origin x coordinate of the label. I want this label to fly in from off screen from the left, so I'm going to use a large positive x value. Now, set your label frame to be equal to the `labelFrame` variable we just made.

Now, let's test it out. Remember to hook up your label to the IBOutlet we created in the viewcontroller, then start it up.

--------
![img8](http://i.imgur.com/8UaJR4z.png)

![gif2](http://i.imgur.com/R71ivts.gif)

If you followed everything correctly, you should now see the label fly in from the left edge of the screen!

One more thing; you can have other items follow this animation! Just set their frames as equal to the `labelFrame` variable we made and they'll tag along for the ride.

--------
![img8](http://i.imgur.com/oesa3Vb.png)

![gif3](http://i.imgur.com/T3iccU2.gif)
