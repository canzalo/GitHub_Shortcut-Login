# GitHub_API
How to use GitHub API

To use GitHub API you must know the github API endpoints.
 https://api.github.com/users/canzalo/repos

This is an API endpoint that GitHub has provided that allows us to return the repos for a specified user in JSON format. 

DEPENDENCIES
- GitHub API
STEP 1:
- We will set up an <b>XMLHttpRequest</b> which will allow us to create a connection with GitHub's API server and request data from it.

STEP 2:
- Let's wrap our entire GitHub API call into a function so that we can dynamically pass in the GitHub username that we'd like to request info for.

function requestUserRepos(username){

}


STEP 3: Define Our GitHub API Endpoint

- Let's take the username argument that we're passing into to our function and use that dynamically within the GitHub API endpoint like so:


function requestUserRepos(username){

    
    // create new XMLHttpRequest object
    const xhr = new XMLHttpRequest();
    
    // GitHub endpoint, dynamically passing in specified username
    const url = `https://api.github.com/users/${username}/repos`;
    
}

N/B: 
- Make sure you use back-ticks and not single or double quotes for the url variable.

STEP 4: Establishing the Connection to GitHub's Server

Since we will be requesting data from GitHub, we will need to specify open our connection and specify that we will be using a
GET request, as opposed to a POST request which would mean we would be sending data.



function requestUserRepos(username){

    
    // create new XMLHttpRequest object
    const xhr = new XMLHttpRequest();
    
    // GitHub endpoint, dynamically passing in specified username
    const url = `https://api.github.com/users/${username}/repos`;
    
    // Open a new connection, using a GET request via URL endpoint
    // Providing 3 arguments (GET/POST, The URL, Async True/False)
    xhr.open('GET', url, true);
    
}

STEP 5: Send Request & Parse Returned Data into JSON

- Once, we've opened our connection to the GitHub API, we can specify what we want to do with our data using the .onload method.
Most importantly, we also need to make sure we actually send our request to GitHub's server using the .send() method.
So just to recap - we're opening our connection to GitHub's server (xhr.open(...)), we're then sending our request to GitHub (xhr.send()), and once our request has been received (xhr.onload), we will run a function that will parse the data. Let's see what the code looks like:



function requestUserRepos(username){
    

    // Create new XMLHttpRequest object
    const xhr = new XMLHttpRequest();
    
    // GitHub endpoint, dynamically passing in specified username
    const url = `https://api.github.com/users/${username}/repos`;
    
    // Open a new connection, using a GET request via URL endpoint
    // Providing 3 arguments (GET/POST, The URL, Async True/False)
    xhr.open('GET', url, true);
    
    // When request is received
    // Process it here
    xhr.onload = function() {
    
        // Parse API data into JSON
        const data = JSON.parse(this.response);
        
        // Log the response
        console.log(data);
    
    }
    
    // Send the request to the server
    xhr.send();
    
}

// Call function passing in 'facebook' as GitHub username
requestUserRepos('facebook');



STEP 6: Accessing the API Data

- You'll notice that if you expand the individual objects from the API response, they'll contain all of the information that we're looking for. In our case, we'll want to grab the name, description, and html_url keys from each object within the data array.
- To get that information, we'll just need to run a simple loop over the data object that's being returned to us in the response, then we can console.log it.

function requestUserRepos(username){

    

    // Create new XMLHttpRequest object
    const xhr = new XMLHttpRequest();
    
    // GitHub endpoint, dynamically passing in specified username
    const url = `https://api.github.com/users/${username}/repos`;
    
    // Open a new connection, using a GET request via URL endpoint
    // Providing 3 arguments (GET/POST, The URL, Async True/False)
    xhr.open('GET', url, true);
    
    // When request is received
    // Process it here
    xhr.onload = function() {
    
        // Parse API data into JSON
        const data = JSON.parse(this.response);
        
        // Log the response
        console.log(data);
        
        // Loop over each object in data array
        for (let i in data) {
        
            // Log the repo name
            console.log('Repo:', data[i].name);
            
            // Log the repo description
            console.log('Description:', data[i].description);
            
            // Log the repo url
            console.log('URL:', data[i].html_url);
            
            // Add a separator between each repo
            console.log('=========================')
        
        }

    }
    
    // Send the request to the server
    xhr.send();
    
}

// Call function passing in 'facebook' as GitHub username
requestUserRepos('facebook');


STEP 7: Creating directory.
- Create a directory called Github_api.
-On this directory create a file named index.html - This file will contain our HTML mark up for the our application 
- Within the Github_api directory create a file named app.js - This file will contain our JavaScript code.


STEP 8: Run the app.
-
