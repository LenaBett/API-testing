# API-Testing with Postman
## Testing the Restful-booker API
### Setting up
To start testing the API on Postman, create a workspace and a collection in postman:
- Create a workspace
![Screenshot of workspace creation section on Postman](https://github.com/LenaBett/Postman-scripting/blob/main/images/Workspace.png)

- Create a collection
![Screenshot of Collection creation section on Postman](https://github.com/LenaBett/Postman-scripting/blob/main/images/Create%20collection.png)

### Starting to test
Once the workspace and collection are set, we can create requests. 

- Click on the '+' sign on the center bar below the search box.
- Enter the API url in the input field and select the request method to be tested
![Screenshot of Request creation section on Postman](https://github.com/LenaBett/Postman-scripting/blob/main/images/Create%20collection.png?raw=true)

- API url [Restful Booker](https://restful-booker.herokuapp.com/apidoc/index.html)

### Generate an auth token
- Create a request and enter the url with the 'AUTH' endpoint
- Type in the request body in the 'Body' tab and click on the send button 
- This request will return a token in the response section. This token will be used for authentication for the 'Put' request.
![Screenshot of Auth token generation request on Postman](https://github.com/LenaBett/Postman-scripting/blob/main/images/AuthRequest.png?raw=true)

### Setting up the 'Update' request
- Create a request and enter the url with the 'Update' endpoint
- In the Authorization tab, create an 'API Key' auth and enter the token returned in the 'Auth' request.
![Screenshot of Auth token setup on Postman](https://github.com/LenaBett/Postman-scripting/blob/main/images/TokenSetup.png?raw=true)
- In the 'Body' tab, enter the data to be updated and send the request.
![Screenshot of Update request on Postman](https://github.com/LenaBett/Postman-scripting/blob/main/images/UpdateData.png?raw=true)

## Test scripts
To write tests, navigate to the 'Tests' tab of the 'Update' request

### Test scenarios written in Javascript
1. Test to validate that the API returns a valid response
```
pm.test('Response must be valid and have a body', function () {
    pm.response.to.be.ok;
    pm.response.to.be.withBody;
    pm.response.to.be.json;
})
```

2. Test to validate the response status
```
pm.test('Update with valid data: status=200', function () {
    pm.response.to.have.status(200);
})
```
3. Test to validate the Firstname data type
```
pm.test('Validate firstname type', function () {
    pm.expect(jsonData.firstname).to.be.a('string');
    pm.expect(jsonData.firstname).to.equal("John");
})
```
4. Test to validate the Lastname data type
```
pm.test('Validate lastname type', function () {
    pm.expect(jsonData.lastname).to.be.a('string');
    pm.expect(jsonData.lastname).to.equal("Njeri");
})

```
5. Test to validate the totalprice data type
```
pm.test('Validate totalprice type', function () {
    pm.expect(jsonData.totalprice).to.be.a('number');
    pm.expect(jsonData.totalprice).to.equal(15);
})
```
6. Test to validate the Deposit Paid input data type
```
pm.test('Validate deposit paid type', function () {
    pm.expect(jsonData.depositpaid).to.be.a('boolean');
    pm.expect(jsonData.depositpaid).to.equal("true");
})

```
7. Test to validate the checkin date input 
```
pm.test('Validate checkin date type', function () {
    pm.expect(jsonData.bookingdates.checkin).to.be.a('date');
})
```
8. Test to validate the checkout date input 
```
pm.test('Validate checkout date type', function () {
    pm.expect(jsonData.bookingdates.checkout).to.be.a('date');
})
```
9. Test to validate the Additional details input
```
pm.test('Validate additional details type', function () {
    pm.expect(jsonData.additionalneeds).to.be.a('string');
    pm.expect(jsonData.additionalneeds).to.equal("Dinner");
})
```
The tests will be run each time the request is sent.
When testing, change the data as needed and view the results of the test in the 'Test Results' tab of the response section.

- Example;
Test results for a test with invalid Firstname, 'DepositPaid' status and invalid 'Booking dates' entries
![Screenshot of Test scripts on Postman](https://github.com/LenaBett/Postman-scripting/blob/main/images/UpdateData.png?raw=true)
