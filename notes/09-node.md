# Node

Week 5 day "2" Monday lecture

node.js and express this week

node-server-auth0 is just backend, no front end

still using, controllers,service and models
we will be using express.js formatting

router is different with express

controllers is user input still but any user
services still business logic but without an AppState. no data is held, just sent to the user

models are defined by schemas, using MongoDB
structure to be saved to the database

debug and run, start server

startup.js comment out the part that doesn't use the auth0

localhost:300

1. make a new controller for cats
    * export class CatsController extends BaseController{
        constructor(){
            super'(api/cats')
            this.router
            .get('', this.getCats)
        }

        get Cats(request, response, next){
            console.log('they be getting cats')
            logger.log (request)  //use instead of console.log
            response.send('you got cats')
        }
    }

* have to restart the server to see changes made in code, just like refreshing the page
* in server we see console.logs in the debug console

2. catsService is pretty much the same

//LINK - 

mongodb+srv://lancefontanilla:<password>@cluster0.n07edxt.mongodb.net/?retryWrites=true&w=majority

password:  M1P4TkGzyRWPf1Rg

Week 5 day 2 Lecture, real day 2 lecture

1. Make CarsController
2. createCar
3. use postman to test instead of building a front end to test servers
4. create model
    * exporting schema 
    * register schema with database in DbContext.js
    
5. create CarsService
    mongo is our ORM

    getCars() {
        const cars = await dbContext.Cars.find() //this "mongo" Sfind returns all cars not just one 
        return cars
    }
6. remove Car
    

Week 5 Day 3 Lecture
