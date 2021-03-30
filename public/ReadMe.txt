https://dev.to/toluagboola/build-an-unsplash-photo-search-app-using-vanilla-javascript-441j

Section 1 - listing variables
    -Form - linking to the form in HTML
        --Event listener for submit button
    -next and previous buttons
    - resultSTats --
    -Spinner is for loading action
    -api key for Unsplash api requirement

Then I defined the callback function handleSubmit in the event listener as shown below:
This function takes an event as its argument and first of all prevents the page from reloading using the preventDefault() method. It then stores the value of the search input in inputValue and removes any whitespace with the trim() method. It stores the trimmed input value in searchQuery and passes it as an argument to the fetchResults function which is being called there. I logged the value of searchQuery to the console to make sure the right value was being passed.

fetch:
The function searchUnsplash takes one parameter (searchQuery), which is inserted into the endpoint as the value of the query query parameter. Now, the URL is stored in a variable endpoint which is passed as a parameter to fetch. The fetch() method takes one argument, the path to the resource you want to fetch, which is stored in endpoint in this case. It always returns a Promise. Now, if the response is 200 OK, it is parsed as JSON which is stored in the json variable. The result is logged to the console so as to view the contents of the JSON data.

Both functions above are asynchronous which means that the await keyword can be used to pause the execution of the function until a promise is resolved. This is achieved by placing the async keyword before declaring a function. I used a try...catch block in the fetchResults function. The try block 'tries' to execute the code within it and, should there be an exception or error, the catch block saves the day and responds appropriately with whatever code is written within it. This is a control flow mechanism which prevents the code from crashing if an error occurs while fetching the results.


JSON RESULTS:
The results property is an array in which the search results are contained. Each search result is an object and can be accessed using either dot or bracket notation.
An empty div with a class of search-results was already created in the HTML file. It is then selected in the JS file within a new function called displayResults which takes a JSON object as an argument. The textContent is also set to an empty string to clear all previous results.

Now, the results array is iterated over using the forEach method. Within the callback function, the nested object can be accessed through the result parameter. If you study the above image closely, you will find that each object in the array contains several keys such as links, user, urls. These can be used to access different categories of information on the object in question.

The first lines within the callback function are variables in which the different values needed are stored. They were all accessed using dot notation and include:

the image url
the link to the image on Unsplash
the name of the photographer
the link to the photographer's Unsplash profile
Afterwards, each result is inserted into the searchResults element using the insertAdjacentHTML method. This method takes two arguments: the position of the element, and the text to be parsed as HTML. Template literals are used in the second argument because of the parts of the code that will be changing constantly. These are represented by placeholders in the code. The function displayResults is then called in fetchResults.

Each image is set to be the background of its container, and is also a link to its Unsplash page. The name of the photographer, which links to his/her Unsplash profile, is placed right under the image and the result display was styled using CSS Grid.


LOADING INDICATOR:
This is something to be displayed when a search query is being executed to let the user know that the operation is still in progress. I selected a spinner from this website and pasted the HTML and CSS into my code. A referece to the spinner was stored globally in a variable spinner and then the fectchResults function was updated as follows: