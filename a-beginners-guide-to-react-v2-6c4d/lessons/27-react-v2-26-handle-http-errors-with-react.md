Instructor: 00:00 Now, what would happen if there was some sort of server error or maybe we made the request incorrectly? Let's take a look here. Let's go down to our query, and we'll make a typo. We'll say nam instead of name, and we'll save that.

00:12 Then when I type in here, I can say Mew and then submit. As a user, I'm just going to see this "...". That's not going to be useful at all. Let's see what's going on here in our developer tools. I'll go ahead and refresh.

00:26 We'll type Mew again. Let's clear out our network tab, and then we hit submit. We're going to get a network error indicating that we cannot query field nam on type Pokemon, and it gives a suggestion for, "Did you mean name?"

00:41 The specific error is beside the point. We just need to show the user a little bit more useful than leaving them in a loading state forever. Let's come back up here before we fix our code, and let's add some state for the error state.

00:55 We'll say setError, initialize that to null, and then we'll say if there's an error, then we'll return, "Oh, no..." In a real application, maybe you'd be a little bit more helpful than that. Let's add an error handler here as a second argument to our then call.

01:14 This will be our error data, and we'll say setError with the error data. Then we could submit that, and we'll type the Pokemon name again. We see, "Oh, no...", and now, we need to try again. The problem that we'll face now is that, if the user does try again, and the server is successful, the way that we have our code structured is not going to work with that.

01:37 What I'm going to do is I'm going to add a new state here for status. We'll have setStatus, and we'll initialize that status to idle, meaning right now, the Pokemon info is not doing anything useful.

01:51 Then we can say that the idle status is when we want to render submit a Pokemon. If the status is idle, then we'll say submit a Pokemon. Then when we start fetching a Pokemon, then we can say setStatus pending.

02:10 Then we can have this represent if the status is pending, then we want to return a "..." to indicate to the user that we're pending. When we have a successful, then we can say setStatus to resolved.

02:26 If we're resolved, then we want to return the Pokemon data. If the status is resolved, then we'll return the Pokemon data in a pre tag here. Then if there's an error, we'll say setStatus rejected, and down here, we'll say status is rejected. Then we'll render, "Oh, no..."

02:50 Now, our render method is very predictable, and we always know when our component is going to render what. Now, if I try to type in Mew again, we're going to see, "Submit a Pokemon first." Then we'll see "..." while it's pending, and then we'll see "Oh, no..." when it's been rejected.

03:06 We'll fix our typo right here. We'll save that, and now, we see "Submit a Pokemon," because we're idle. We'll type in Mew, hit submit. We get that "...", and then we see Mew's details. If we try another Pokemon, then we'll see a "...", and we'll see that Pokemon's details.

03:25 Let's go ahead and review. We added some error handling by creating some error state management, and we added an error handler to our promise. If we get some error data, then we're going to set that error data so that we can render something useful to the user indicating that there's been a problem.

03:42 Then, to avoid some state bugs, we added a status state so that we could start out with idle. Then, when we start fetching the Pokemon, we can set it to pending. Then, when we get the Pokemon, we can set it to resolved, or if there's a failure in getting the Pokemon, then we'd set it to rejected. That helps us to avoid bugs.


