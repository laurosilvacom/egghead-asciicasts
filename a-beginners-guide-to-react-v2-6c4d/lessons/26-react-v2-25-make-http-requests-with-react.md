Instructor: 00:00 Here we have an app that's managing a Pokémon name state. Then we're rendering out a form, and we're rendering an input. Every time we submit our form, we're going to update the Pokémon name to whatever the user typed in the input.

00:13 When this is rerendered, we're going to render the Pokémon info with that Pokémon name. Then the Pokémon info should render out information based on that Pokémon. If we type in Pikachu, then we should request some information for Pikachu.

00:31 We need to get that information by fetching it from a server, so we have this helper function here called fetch-pokemon that creates a Pokémon GraphQL query. We're using window.fetch to fetch to this public API that has Pokémon information.

00:47 We're making a post. We have our proper headers to accept JSON. We serialize, and then we specify our body is a JSON stringified version of our query, and then the variables for our query, which is the name of the Pokémon. When that promise resolves, we're going to take the response, parse it as JSON.

01:10 When that's done, we'll get that response object, and pluck the Pokémon off of the data in the response. We can call this function to get the information for this Pokémon that we get as a prop, but our render method here has to be synchronous, and our fetch-pokemon function is asynchronous.

01:30 Making HTTP requests like this is a side effect, so we're going to use the React useEffect hook. We'll say react.useEffect. The first thing that I want to say here is if there's no Pokémon name -- they haven't entered a Pokémon name yet, or they submitted an empty one -- then we'll simply return. We don't need to make a request for that.

01:52 Otherwise, we'll call that fetch-pokemon with the Pokémon name. Then in our success handler for this promise, we'll get the Pokémon data, and we can set some state. Let's go ahead and manage some state for this. We'll have useState for Pokémon. Then we'll call set-pokemon, and we'll initialize this to null.

02:15 Down here, let's rename this from Pokémon to Pokémon Data. Then we can call set Pokémon with the Pokémon data. Down here, we can say if no Pokémon, then we'll return just a ... to indicate that we're loading. Otherwise, we know we have the Pokémon data, and so we can render it right here.

02:38 Let's JSON stringify this. We'll put that in a pre so we get the right spacing. We'll say JSON stringify Pokémon null two to get nice spacing for our JSON. We'll save this. We have a ... right here because there's no Pokémon. Then we can enter in Pikachu, submit that, and we get Pikachu's information.

03:01 In our view, to do anything asynchronous, that is a side effect that needs to happen inside a useEffect callback. For our Pokémon info, we accept that Pokémon name. In our callback, if there is no Pokémon name specified, then we'll simply return. Otherwise, we'll fetch the Pokémon data with that Pokémon name.

03:19 When we get that data back, we'll update our own state to have that data. That'll trigger a rerender of Pokémon info, and then we can return the stringified version of that Pokémon data.

03:31 We could apply an optimization here to make sure that this useEffect only runs when we want it to by putting Pokémon name in here. That way, this useEffect will only rerun when the Pokémon name changes. We could also add an if statement here for if there's no Pokémon name supplied.

03:51 We could say return "Submit a Pokémon." With that, we get "Submit a Pokémon." Then we can type in something like Pikachu, submit that, and we'll get Pikachu's information loaded up.


