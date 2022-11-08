# Animal Shelter API
---

#### By Skylan Lew

Epicodus Project 12


## Technologies Used
---

- C#
- .NET5.0
- Entity Framework Core
- Swagger
- Identity
- JWT

## Description
---

An API for tracking Animals at an animal shelter. It has models for Animals (of any type), and for active shelter Branches. It has a one to many relationship between shelter Branches and Animals (an animal may only be assigned to one branch).

The user may use the API to Read a list of Animals and Branches, and is able to query those lists. They also may login and Create, Update, and Delete Branches and Animals.

When being created, Animals require their sex, name, species and branch to be input. Branches require both name and address.

## Setup/Installation Requirements
---


- Create a file named `appsettings.json` in the project folder `/CandyShop/`
- Put the following code inside `appsettings.json`, making sure to set your uid and pwd:

```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Server=localhost;Port=3306;database=candyshop;uid=YOURUSERNAME;pwd=YOURPASSWORD;"
  }
}
```

### Requires

- [.NET 5](https://dotnet.microsoft.com/en-us/download/dotnet/5.0) - <https://dotnet.microsoft.com/en-us/download/dotnet/5.0>
- MySQL - Recommend [MySQL Workbench](https://dev.mysql.com/downloads/workbench/)
- API Platform - Recommended [Postman](https://www.postman.com/)

### Download/Run Instructions (git)

- clone: `$ git clone https://github.com/doublespoiler/animal-shelter-api.git` or Code>Download ZIP
- navigate to project folder: `$ cd /AnimalShelterAPI`
- restore: `$ dotnet restore`
- build: `$ dotnet build`
- Apply migrations: `$ dotnet ef database update`
- run: `$ dotnet run`
- Access the API using `http://localhost:3000`

## Endpoints

---
* `POST`, `PUT`, `DELETE` for all branches require JWT Bearer Token
* All queries are case agnostic, and those labelled with a `?` can be partial. Put `&` between multiple queries.

* GET `api/animals`
	* Returns all animals
	* Query `api/animals/?name=Titan&color=wh`
		* string sex (male or female)
		* string species? (feline, canine, etc.)
		* string breed? (pit bull, shorthair, etc.)
		* string color? (red, white, wh, etc.)
		* bool isFixed (true, false)
		* string name?
		* int olderThan
		* int youngerThan
		* int branchId (search by branch)
* GET `api/animals/{id}`
	* Gets an animal's information by Id
* GET `api/branches`
	* Returns all branches
	* Query `api/branches/?name=f&address=flag`
		* string name?
		* string address?
* GET `api/branches/{id}`
	* Get's a branches' information by Id
* GET `api/branches/{id}/animals`
	* Returns all animals for the specific branch
	* Same queries as GET `api/animals` (except branchId, that would be silly)
* POST `api/animals` && `api/branches` 
	* Requires JWT Bearer Token
	* Creates a new branch or animal
* PUT  `api/animals/{id} ` && `api/branches/{id}` 
	* Requires JWT Bearer Token
	* Update branch/animal of id {id}
* DELETE  `api/animals/{id}` && `api/branches/{id}`
	* Requires JWT Bearer Token
	* Deletes the animal or branch of id {id}

### JWT/User Endpoints
* GET `api/users`
	* Requires JWT Bearer Token
	* Returns a list of all users
* POST `api/users/authenticate`
	* Allows the user to authenticate with JWT and recieve a bearer token
	* Body format `{"Name":"USERNAME","Password":"PASSWORD"}`

### Full payloads
* Animals
```json 
{
	"sex": "male",
	"name": "Bond Forger",
	"age": 5,
	"species": "canine",
	"breed": "great pyrenees",
	"color": "White",
	"isFixed": true,
	"branchId": 1
}
```

* Branches
```json
{
	"name":"Flagstaff Humane Society",
	"address":"1800 S. Milton Road, Flagstaff, AZ 86442"
}
```

## Authentication with JWT
---

* IMPORTANT: To use `POST`, `PUT`, and `DELETE` actions, the user must authenticate with JWT, and load the resulting token as a Bearer Token.
1. Open Postman, and start a `POST` action to `localhost:3000/api/user/authenticate`
![[Postman_QlhRlxVkRC.png]]
2. In the JSON body, put the Name and Username of the user logging in. Default is `"Name":"admin`, `"Password":"admin"`.
4. Copy the resulting token, without quotation marks.
5. Start a new `POST`, `PUT`, or `DELETE` action.
6. Click the "Auth" tab, change the Type to "Bearer Token", and paste the token from Step 4 into the Token area.
![[Pasted image 20221029113347.png]]
7. You can now send the `POST`, `PUT`, or `DELETE` action as normal.
8. Try sending without the Bearer Token to see the action returns 401 Unauthorized.
9. The user may add new users by adding Dictionary entries in `Repository/JWTManagerRepository.cs`, in the format `{"name","password"}`, and adding the `"name"` to the list in `Controllers/UserController.cs`
![[Pasted image 20221029114033.png]]![[Pasted image 20221029114007.png]]

## Swagger
---
* The user can use Swagger to view and test API calls.
* To access Swagger, go to `localhost:3001/swagger`
* Here, the user can see all API endpoints
 ![[Pasted image 20221029114310.png]]
* Clicking on the endpoint allows the user to try it, by clicking "Try it out", then they may input query parameters.
![[Pasted image 20221029114404.png]]

* When the user clicks "Execute," the response is shown.
![[Pasted image 20221029114414.png]]

### Swagger Authentication
* To use `POST`, `PUT`, and `DELETE` actions, the user must authenticate using JWT Bearer token.
* The user may get their Bearer token using `api/user/authenticate` in Swagger (see Authentication with JWT above), or use the one they got using Postman or another API Platform
* Click the "Authorization" button on Swagger
*![[Pasted image 20221029124159.png]]
* Enter `Bearer YOUR KEY HERE` into the Value field and click "Authorize". The user will be logged in if Swagger asks them to log out ![[Pasted image 20221029124315.png]] ![[Pasted image 20221029124324.png]]
## Known Bugs
---

- User logins currently saved as rawtext in JWTManagerRepository.cs
- Swagger shows a 

## License
---

[MIT](https://choosealicense.com/licenses/mit/) `[MIT](https://choosealicense.com/licenses/mit/)`

Copyright (c) 2022 Skylan Lew

