# GitHub_API
How to use GitHub API

To use GitHub API you must know the github API endpoints.

This is an API endpoint that GitHub has provided that allows us to return the repos for a specified user in JSON format. 



<h4> DEPENDENCIES </h4>


<h5>GitHub API</h5>


<h4>STEP 1:</h4>


- We will set up an <b>XMLHttpRequest</b> which will allow us to create a connection with GitHub's API server and request data from it.


<h4>STEP 2:</h4>


- Let's wrap our entire GitHub API call into a function so that we can dynamically pass in the GitHub username that we'd like to request info for.

<code>
function requestUserRepos(username){

}

</code>

<h4>STEP 3: Define Our GitHub API Endpoint</h4>



- Let's take the username argument that we're passing into to our function and use that dynamically within the GitHub API endpoint like so:


<code>
function requestUserRepos(username){

    
    // create new XMLHttpRequest object
    const xhr = new XMLHttpRequest();
    
    // GitHub endpoint, dynamically passing in specified username
    const url = `https://api.github.com/users/${username}/repos`;
    
}
</code>
<b>N/B: </b>

<p>Make sure you use back-ticks and not single or double quotes for the url variable.</p>



<h4> STEP 4: Establishing the Connection to GitHub's Server</h4>


<p>Since we will be requesting data from GitHub, we will need to specify open our connection and specify that we will be using a
<b>GET request</b>, as opposed to a<b>POST request </b>which would mean we would be sending data.</p>


<code>
function requestUserRepos(username){

    
    // create new XMLHttpRequest object
    const xhr = new XMLHttpRequest();
    
    // GitHub endpoint, dynamically passing in specified username
    const url = `https://api.github.com/users/${username}/repos`;
    
    // Open a new connection, using a GET request via URL endpoint
    // Providing 3 arguments (GET/POST, The URL, Async True/False)
    xhr.open('GET', url, true);
    
}

</code>


<h4>STEP 5: Send Request & Parse Returned Data into JSON</h4>



<p>Once, we've opened our connection to the <b>GitHub API</b>, we can specify what we want to do with our data using the <i>.onload method.</i><br>
Most importantly, we also need to make sure we actually send our request to GitHub's server using the <b>.send()</b> method.
So just to recap - we're opening our connection to GitHub's server<i> (xhr.open(...))</i>, we're then sending our request to GitHub (xhr.send()), and once our request has been received <b>(xhr.onload)</b>, we will run a function that will parse the data. Let's see what the code looks like:


<code>
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

</code>


<h4>STEP 6: Accessing the API Data</h4>



<p>You'll notice that if you expand the individual objects from the API response, they'll contain all of the information that we're looking for. In our case, we'll want to grab the name, description, and html_url keys from each object within the data array.<br>
- To get that information, we'll just need to run a simple loop over the data object that's being returned to us in the response, then we can console.log it.</p>


<code>
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

</code>

<h4>STEP 7: Creating directory.</h4>


<p>- Create a directory called Github_api.<br>
-On this directory create a file named index.html <br>- This file will contain our HTML mark up for the our application <br>
- Within the Github_api directory create a file named app.js - This file will contain our JavaScript code.</p>

<h4>STEP 8: Run the app.</h4>



