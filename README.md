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
