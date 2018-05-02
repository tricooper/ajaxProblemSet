AJAX How to Guide


Intro: What is AJAX

In this guide, we’ll learn about using AJAX in your projects. AJAX, short for Asynchronous Javascript and XML, is a way to request data from a web server directly from your browser. In this guide, we’ll specifically be focusing on using AJAX with jQuery. You can also use AJAX with vanilla JS, but using it with jQuery allows us to easily focus on the main objective of creating an AJAX request and outputting data to a page. 

By the end of the practice set, you’ll be able to click a button and load movies from the MoviesDB API into a webpage.

	
			
Step 1: How do I use AJAX?

To get started with AJAX, we need to understand its syntax. Here’s the basic structure of an AJAX request:
``` javascript
	$(document).ready(function() {

	$.ajax({
		url: [insert url here],
		success: [callback that will run on success],
		error: [callback that will run on error]
	});

});
```

In this example, the URL parameter will represent the endpoint you’d like to request, “success” if a callback that will run when the parameter has successfully received a response and returns the data. “Error” is invoked only if the request fails, it will receive a string indicating the error type. 
	
*NOTE:* there are many ways to format an AJAX request including, but not limited to, using Promise methods. You should read here for all of the available parameters and methods. For now, this will be good enough to set up a simple response to a server. 


Step 2: Basic AJAX Request

Alright, let’s start to get our hands dirty:

•	First, clone this GitHub Repo for the Starter Code in this assignment: https://github.com/tricooper/ajaxProblemSet
o	In the directory for the file, make sure to run NPM install.
o	Run NPM start to run the file.
o	By default, it will run on port 8080. 

•	Next read through the OMDb API documentation and sign up for an API Key.

We’ll start by adding in a basic request and creating our success message to log directly into the console:
``` javascript
$(document).ready(function() {
	function onSuccess(data) {
		console.log(data);
	};

	function onError(error) {
		console.log(error)
	};

	$.ajax({
		url: 'http://www.omdbapi.com/?apikey=[apikey]&t=Tomb',
		success: function(data) { onSuccess(data) },
		error: function(error) { onError(error); }
	});
});
```

•	Here we can see the URL is 'http://www.omdbapi.com/?apikey=[apikey]&t=Tomb', we’ll be searching for any movies with the title of “Tomb”.
•	The onSuccess Function will run when the request has gone through successfully.
•	The onError function will run when there is an error.
•	Take this code and paste in your API key, reload the file and make sure you get a successful message logged to the console. 


Step 3: Output the Data to the Page

Next, we’ll actually output the data onto the page. To do this, we’ll create new variables for the properties we’d like to display on the page and access the data then, in our onSuccess function, we’ll target the ‘append-data’ class and append these variables to the Document Object Model.
	Here’s the updated onSuccess Function:
``` javascript
		function onSuccess(data) {
		console.log(data);
		var title = data.Title;
		var poster = data.Poster;
		$('div.append-data').append(`<p>${title}</p><img src="${poster}">`);
	};
```

You can see that we are storing the Title and the Poster URL from the data in the variables “title” and “poster”. We then output and append this to the page. If you reload your screen, you should make the appear.


Step 4: Next Steps, Practice problems

Now that we have outputted data to a page, there are a couple more steps involved you can take on your own:

	1. Add an event handler such as a button that the user can click to trigger the AJAX request and then output to the page.
	2. Add in Input Elements that will change the AJAX request and dynamically search for movies. For example, allow the user to search for the year, title, and genre of movie they would like to see. 
	3. Style this so it has a nice User Interface that is easy to engage with.
