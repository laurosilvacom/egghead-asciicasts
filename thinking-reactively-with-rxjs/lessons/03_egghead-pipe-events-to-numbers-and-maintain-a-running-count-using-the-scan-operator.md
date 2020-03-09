# Pipe events to numbers and maintain a running count using the scan operator

[Video link](https://www.egghead.io/lessons/egghead-pipe-events-to-numbers-and-maintain-a-running-count-using-the-scan-operator)

Instructor: [00:00] Let's look at the first problem we have to solve. I'll paste it here so we can follow more easily. I'll use my raw initial sources that I have up here to create a more specialized load up observable that emits one anytime a task starts.

[00:16] I'll do the same thing for a load down observable that emits a minus one anytime a task completes. Now, we can use these two to combine them into an even more useful load variations observable that gives us plus ones and minus ones, depending on how tasks are starting and ending.

[00:36] Notice how I've imported map to from the RxJS operators package because it's meant to be piped and merged because we're actually using it to create a brand new observable. It's being imported from the root RxJS package.

[00:50] Let's celebrate progress. We're already in a much better position than when we started. This observable is actually all we need from now on to solve our problem. We can forget anything that we have up here.

[01:01] I'll actually make this more obvious and use the special comment from that one to mark that we can stop worrying about anything we have above it. This helps us work in a very restricted space. My cognitive demand is much lower when I can be sure that all the context I need to keep in my head is what I have highlighted versus this whole page.

[01:23] Because we're pretending that we don't have access to whatever is above this, variable names are very important when we work like this. We shouldn't really have to go back up to see how all of this works. It should make sense from its name.

[01:35] We'll consider our current problem solved, if we have this, an observable that gives us the current load count of tasks in our app. We'll start with our load variations observable. Because we need to maintain a running count between emissions, I'm going to pipe that to a scan. I'll quickly go up and import it.

[01:57] Scan has the same API as the reduce array method. It accepts a function, which will receive two arguments, the total current number of load and the change in loads. Our variation that we get from here. What it's going to return is the previous load count to which we will add the new change in the number of load.

[02:24] It also accepts a starting value after our function and we wanted to start from zero.

[02:28] Just to quickly go back and recap, the moment the task starts, it will get mapped to a number one so load variations will limit to one, which will in turn increase the count by one. If a task ends, it will get mapped to a minus one, so load variations will emit the minus one which will decrease our count by one.

[02:45] We started from some very raw streams, and we used those to create two more specialized streams. Then we combined those to create an even more useful stream, all the way up to this. A stream that whenever somebody subscribes to it, they'll get the current number of loads in our application.
