# API-Testing with Postman
## Testing the Restful-booker API
### Setting up
To start testing the API on Postman, create a workspace and a collection in postman:
- Create a workspace
![Screenshot of workspace creation section on Postman](https://github.com/LenaBett/Postman-scripting/blob/main/images/Workspace.png)

- Create a collection
![Screenshot of Collection creation section on Postman](https://github.com/LenaBett/Postman-scripting/blob/main/images/Create%20collection.png)

###Starting to test
Once the workspace and collection are set, we can create requests. 

- Click on the '+' sign on the center bar below the search box.
- Enter the API url in the input field and select the request method to be tested
![Screenshot of Collection creation section on Postman](https://github.com/LenaBett/Postman-scripting/blob/main/images/Create%20collection.png)

- API url [Restful Booker](https://restful-booker.herokuapp.com/apidoc/index.html)

###Generate an auth token
- Create a request and enter the url with the 'AUTH' endpoint
- Type in the request body in the 'Body' tab and click on the send button 
- This request will return a token in the response section. This token will be used for authentication for the 'Put' request.
![Screenshot of Collection creation section on Postman](https://github.com/LenaBett/Postman-scripting/blob/main/images/Create%20collection.png)

###Setting up the 'Update' request
- Create a request and enter the url with the 'Update' endpoint
- In the Authorization tab, create an 'API Key' auth and enter the token returned in the 'Auth' request.
![Screenshot of Collection creation section on Postman](https://github.com/LenaBett/Postman-scripting/blob/main/images/Create%20collection.png)
- In the 'Body' tab, enter the data to be updated and send the request.
![Screenshot of Collection creation section on Postman](https://github.com/LenaBett/Postman-scripting/blob/main/images/Create%20collection.png)

