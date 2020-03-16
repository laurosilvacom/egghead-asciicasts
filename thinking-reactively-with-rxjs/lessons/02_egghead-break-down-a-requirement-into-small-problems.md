# Break down a requirement into small problems

[Video link](https://www.egghead.io/lessons/egghead-break-down-a-requirement-into-small-problems)

Instructor: [00:00] Our virtual manager comes in and tells us that we need to build a spinner for the app that will show any time there's any task going on. Instead of rushing to implement, let's try and break down the problem that we're trying to solve. I'll use this drawing of a building as an analogy for obstruction levels.

[00:16] The top floor is our highest level of obstruction and that's where we'll start. What's another way of thinking about the requirement? Well, when the spinner needs to show, show the spinner until it's time to hide it.

[00:29] Because we're at the highest level of obstruction, this way of seeing the problem is the most ambiguous because we still have no idea what any of these three things mean. But it's also the closest interpretation to our requirement. If we solve this, we solved our problem.

[00:44] Let's keep moving down and try to make this more specific by answering some of these questions. When does the loader need to show? Well, when the count of acing tasks goes from zero to one. Let's explain this other part now. When does the loader need to hide? Well, it needs to hide when the count goes to zero.

[01:03] Notice how we stayed at the same level of abstraction with these two sentences. We still don't know how we would get the count of async tasks. How do we count? Well, we start from zero and when an async task starts, increase the count by one. When the task ends, decrease the count by one. We'll stop here.

[01:22] Our goal was to start from something that resembles our initial requirement really closely, something vague that we wouldn't really know where to start solving. Break that down into more and more specific problems all the way to this, a simple counter that we can actually start tackling.

[01:41] If we look closely, we broke down and explained almost everything. We still have some unknown sources like what is async task starts? What is task ending? Even, what is show the spinner?

[01:56] If we had these free sources, then we could really nicely start going up to building and solve our problem. The nice part about solving problems this way is that we can imagine that we actually do have them. I'll just define task starts as a simple observable for now. I'll do the same for task completions. The same for show spinner. I'll just go ahead and import the observable token.

[02:21] The great thing about breaking down our problems into small chunks like we did with the floors of our building is that we can define placeholders for any unknown sources and assume they already exist. This keeps us focused on solving our problem, one floor at a time.
