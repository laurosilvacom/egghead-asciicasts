Instructor: 0:00 We made a clock application. Here, it's rendering out the time and we get that time with new date toLocaleTimeString, and then we put that inside of a div and render that. The problem is that it gets out of date as soon as you refresh the page. Every time you refresh the page or get that updated, but you have to keep on refreshing the page, and what a pain that is.

0:19 What I want to do instead is I'm going to put this into a function and have that function called every second. Let's go ahead and make that function called tick. We'll put all this inside of tick, and then we'll call tick. We just refactored, just put something in a function. That's a very normal thing to do. Now I'm going to say set interval, tick, every 1,000 milliseconds. I'm getting that update.

0:48 The thing that I want to show you about the way that this is working is if we look in the body and then come down here to our app. We're going to see that update happening on our string right here. If I were to add something in here, like we put another div, hello, and another div right there, and then paste that time in there, then we're going to notice that the only thing that's updating is this clock time and not this div.

1:14 Let's see how this differs if we were to just turn this into an HTML string, and we'll interpolate that. Then instead of ReactDOM.render, we're going to say root element.innerHTML equals that element.

1:31 We're getting that same behavior that we had before, except the way that it works is it's updating the entire contents of our application every time, starting from this root element. That's not optimal, because it causes a couple of problems. Let's take a look at an example.

1:47 If I make an input and set the value to that time, and let's go ahead and we'll put two in here, then we'll save that, and now we have two of those, and they are updating every second, but as I click in here, my focus is going away. That's because the old elements that were the inputs there are getting totally removed from the DOM, and the new elements are getting put in their place. React doesn't have this problem.

2:13 Let's go ahead and turn this back into JSX. Just take away that, take away that, and the closing quotes, and then we'll remove this and comment that out. Now we're back, and all that we're getting is an update to the values that actually matter for our application, which are the properties for both of these inputs.

2:36 This has great implications for the performance of our applications, as well as the accessibility, because React is keeping track of our focus for us.

2:44 This isn't how you normally re-render new application. Typically, whenever state changes, you don't have to re-render your entire application, but I wanted to show you this so you have an understanding of what React is really doing for you.

2:56 When you create these React elements, you give that to ReactDOM.render or you trigger a re-render of a component, and React is going to compare the elements that you returned this time with the elements that you returned last time.

3:09 It's going to do a div of those two elements, and then it will update the DOM surgically to only update the things that were different between the last time and this time you returned JSX.


