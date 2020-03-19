Kent C. Dodds: 0:00 We have this username form. Right now, we're returning just to do. We want to return a form. I'm going to make a form element here. Then we'll make a div to hold our label username.

0:17 Then we'll have an input of type text for our username input. Then we'll add a button of type submit. This is our submit button. We'll say submit. We'll save that. We get a refresh. Here's our form. Awesome.

0:33 We could put an onClick handler on our submit button here. That would work OK when we click on this button, but forms are actually automatically submitted when you hit enter in an input within the form. People are typically used to that user experience.

0:48 What I'm going to do instead is we'll add an onSubmit handler here. If somebody clicks on the submit button or if they hit enter in this input, then our onSubmit handler is going to be called. Let's make a function called handleSubmit. Then we'll put that handleSubmit right in here. We'll console.log submitted. We'll save that. Get a refresh. Say, "Joe." Hit Submit.

1:15 Huh, that's interesting. It goes away. Actually, if you watch closely, you'll see that it does log, but then we get a full page refresh. We can prove that by turning on preserve log. Then say, "Joe" again. Hit Submit. We get submitted and then navigated to that page.

1:32 The reason that this is happening is because when you submit a form in the browser, it automatically makes a post request to the current URL with the form data. We could see that if we looked at our network tab.

1:46 If you want to do some JavaScript stuff based on the user-submitted form, then we don't want the full page refresh. Instead, we can do our own JavaScript stuff. The handleSubmit function as an event handler will accept an event as the argument. Then we can say, "event.preventDefault." With that, we will no longer get a full page refresh. We'll still get the submitted string logged to the console.

2:09 Our next step is to get the value out of this input because we want to alert the value that the user entered. We need to get our username equals something. We'll say, "Alert. You entered username." We can get rid of that console.log here. Then we can say, "Joe" and "You entered ?."

2:31 How are we going to get that username value? One way we could do this, we could say, "document.querySelector input.value." Save that. We say, "Joe." Submit that. Here we go. We get Joe.

2:46 That's not going to work very well. It won't scale super-well in the real world because the page could have multiple inputs. If we were to render multiples of these, then they could conflict with one another.

2:56 Querying the entire document breaks the encapsulation of this component because it means that you can't use this component in the context of other components in an application. We don't want to query the document.

3:09 Another thing we can do is we can access the form element from the event. We could say, "console.log event.target." That is going to be our form element. We say, "Joe." Submit that. We'll get the form element right there.

3:25 That's great, but let's take a look at some of the properties on that form element. Chrome is rendering out this really cool DOM tree similar to what we see in the elements tab. I want to see the properties that are on the form element, so I'm going to use console.dir, which will log out the properties of that element.

3:41 We'll say, "Joe." Submit. Here we go. We have our form. Here there are a bunch of properties on here. We can see there's a zero and a one for input and button. We could actually say, "username is event.target." We want zero.value. We save this. We get Joe. We get our "You entered Joe" alert showing up. That works out nicely, but I'm going to get the username from another one of these properties.

4:10 Let's see. We've got elements right here. Elements has a zero and a one. We could say, "event.target.elements at zero.value." Save that. That will work as well, but I'm not super-jazzed about relying implicitly on the order in which these form elements appear. If I were to add another input right here, then I'm going to be toast. You entered undefined.

4:38 I don't want to rely on that. There's another thing that we can do here. That is by properly associating our label to the input by having an HTML for username input and then having an ID of username input right here, now the label and the input are properly associated, meaning that I can click on the label and it will focus on the input, which is good for accessibility.

5:03 When I say "Joe" in here, hit submit, then we look at our form and our elements property, now in addition to the zero and one indexes for each of these elements we also get this username input value here because the ID of this element inside of our form. You actually get the same thing using the name attribute as well.

5:29 If we look at our form elements, we see that username input still exists right there. Any elements that have a name or an ID will be attached by that name and ID to this elements property of the form node. You can reference those by those names and IDs.

5:45 That's what we're going to prefer here. We'll say, "username equals event.target" -- that's our form -- ".elements.usernameInput.value" to get the value out of that username input. With that, we can say, "Joe." We get everything working exactly as we want without the implicitness of querying the entire document or relying on the order of the elements.

6:09 Another thing that we could do is make a ref for our username input. We'll say "usernameInput ref equals React.useRef." Then we could say, "ref equals usernameInput ref." Instead of this, we could say, "username equals usernameInputRef.current.value." UsernameInputRef.current will be the DOM node for the input. We'll get the value from that. This will work as well.

6:43 There are a couple ways to do this. I'll go ahead and add username equals document.querySelector input.value. The reason that I removed that is I really want you to please not use this. It breaks encapsulation of our components.

7:00 That's one of the things that we really love about React, is that we can encapsulate logic within our components. I don't recommend this method or this method because those implicitly rely on the order in which the elements are rendered and could easily break if you change that order. Either one of these will work just fine.

7:16 Personally, I think that if you don't need a ref for the input that it's just easier to retrieve the input from the event target elements. It's recommended that you use HTML for an ID to associate labels to inputs anyway. Given that you already have to do that, this is the simplest way to get the value from the inputs in your form.

7:36 With that in mind, let's go ahead and get rid of all of these. We'll get rid of that, clean this up, and remove the ref. If I were writing this form today, this is what it would look like.

7:46 In review, what we had to do here was we created a form that has a single input and label associated to that input and a button with the type of submit. It's really important that any button you put inside of a form has a type because implicitly it will have a type of submit. That's not entirely clear, especially if you say cancel for the contents.

8:07 With no specified type, that gives this button a submit type, which is really confusing. If you do want to have a cancel button or a reset button, then you want to specify the type is button, which I know is a little redundant. If you don't specify a type, then the type will implicitly submit, which would really confuse your users when they try to click cancel.

8:28 We specify that type is submit. We put in submit for the value here. Instead of putting an onClick handler on the button, we put an onSubmit handler on the form. That way, any other way that the user tries to submit the form will call our submit handler.

8:44 To avoid a full page refresh, we use event.preventDefault. Then we retrieve the user's input using event target to get the form and then elements to get the elements of the form and username input to retrieve the input by its ID. Then we get the value from that input to get our username. Then we alert that to our users, or you could submit this to a back-end server.


