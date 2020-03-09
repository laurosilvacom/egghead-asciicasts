# Use the filter and pairwise operators to determine when to show and hide the spinner

[Video link](https://www.egghead.io/lessons/egghead-use-the-filter-and-pairwise-operators-to-determine-when-to-show-and-hide-the-spinner)

Instructor: [0:00] We solved this problem and now we can move up one floor of obstruction. I'll copy this to our source page, and I'll copy this comment over here, just to mark that we're moving up one level of obstruction in our code as well. We're building an observable that's going to answer this question. Let's name it accordingly.

[0:22] When the count of async tasks goes, we'll start with our current load count and once that goes to , we want to emit. I'll pipe this to the filter operator. We'll just go to the top and import it. It's only going to let values through that are .

[0:38] We don't care that this emits . We don't care what it emits. We just care when it emits because that's the time to hide the spinner.

[0:46] Let's pick our second requirement. I'll just paste it here. Now we'll build an observable that answers this question. We'll name it shouldShowSpinner. Again, we need to listen to the count. We'll pipe this to a filter function again that will only let emissions go through when the load is 1.

[1:05] This is not really right because we can go from a count of 2 to a count of 1 and then this will emit, but that doesn't really mean that we have to show it. It's already showing. This part is really important.

[1:18] We need to keep track of the previous value, as well as the current one and only emit when the previous is  and the current is 1. This is not going to work as it is. Filter only works with the current value. How do we keep track of the previous?

[1:32] Well, scan is one option. It allows us to keep track of previous state, but RxJS has a lot of operators that are named really well. If we can pretend for a moment that we just looked through the RxJS API, we notice that we can import the pairwise operator.

[1:50] If I go back and add it, we'll see that it emits a tuple of the previous and the current value. We're just going to use some destructuring here to get the previous and the current count from pairwise.

[2:01] Even though we could have done this with scan, with pairwise we signal our intent much better to other developers reading this. The more operators we know, the bigger the chance that we're going to find a nicely named obstruction that signifies intent much better than a custom solution.
