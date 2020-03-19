Kent C Dodds: 0:00 Here we have an app component that is rendering some JSX here for there have been events, click me, you typed, and then an input here. We have some state that is running this application component. If I update the event count to 10, then we're going to see there have been 10 events.

0:16 If I update the username to 'Hello there' and save that, then we're going to see you typed Hello there. The value of the input isn't getting updated and there have actually not been 10 events, so let's go ahead and wire up things so we can update our state and re-render the app.

0:32 We already have a function here called setState, which will update our state variable and then render the app. That will just call React.render on our root again. This is not typically how you re-render an application or manage state in a React application, but this will work for our purposes of learning how events work in React.

0:51 First let's deal with this button. We have on button's an onClick event that we can call. This we're going to provide a function. I can make this an inline arrow function here.

1:03 We'll just say setState, calling this function down here with the new state of an object, eventCount. We want that eventCount to be the current state. eventCount + 1. If we save that and then I go over here and click, we're going to get an increment every single time I click.

1:21 There are a lot of different events that we can use here. We can have an onFocus and save that and every time I focus the input we're going to get an increment on that event. Or we could say onMouseOver, save that, and then every time I mouse over, we'll get an increment on that event count. There are a lot more events that are supported by React.

1:43 Let's set this back to onCount and then we can also extract this to handleClick. We could put that right here. Function handleClick() and then we'll call setState there. That will work just as well. It would work if we used onClick instead of onCount. There we go.

2:03 Then let's take a look at this input. We want this you typed to get updated when we enter some new username. I'm going to say onBlur and we'll say setState('username'). Then we need to specify a value here.

2:18 What we need is to get the value of the input that is receiving the onBlur event. As an argument to the event handler, we receive the event. Then we can use that event to get the target of the event, which will be our input. Then we'll get that value from the input.

2:36 If we save that, then we can type in Kent C Dodds and then blur. Our state gets updated. If we want this to get updated as we're typing, then we can change this to onChange. As the user types in this input, we'll get that update to our state and we'll re-render the application.

2:54 Let's go ahead and pull this onChange handler out. We'll say handleChange. We'll bring it up here. Function handleChange will take the event. Let's go ahead and take a look at that event. We'll say console.log(event), save that.

3:10 We'll pop open our Dev Tools here, look at the console, and then type in one character. We'll notice we get a synthetic event object here. That's not the native event. The native event is this property nativeEvent input event. React does some serious performance optimizations for our events and that's what this synthetic event thing is all about.

3:33 Most of the time you don't need access to the native event, but if you ever do then you can say event.nativeEvent and we'll hit save. We'll type in a character and we'll get that native input event. But the synthetic event has pretty much all the same properties as a regular event, so that's what you're typically going to use.

3:54 One thing I like about React's event system is that you pass the event handler directly to the element that you want to attach the event to, so it makes following the flow of events and state updates really straightforward.


