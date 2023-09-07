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
        const cars = await dbContext.Cars.find() //this "mongo" find returns all cars not just one 
        return cars
    }
6. remove Car
    

Week 5 Day 3 Lecture
Data Relationships

1:1
1:Many
Many:Many

1. put in your Connection String in env.js
* MongoDB Collections are where are data goes
2. Lines 22-26 comment out in Startup.js
3. create Schema in Exhibit.js //new "model"
4. create Exhibits controller
    * start with .post
    * createExhibit(request, response, next)
5. register the schema in DbContext.js
    * Exhibits = mongoose.model('Exhibit', ExhibitSchema)
6. create Exhibits service
    async CreateExhibit()
7. open up Postman
    * in Postman, New Collection
    * Zookeeper NODE
    * POST Create Exhibit
    * Click Body, then select RAW change text to JSON
8. create Get request in Controller and Services
    * get
9. in Postman add collection for get Exhibits
10. in async getExhibits in controller add const query = req.query 
11. pass query into getExhibits in services
12. can use debugger to see properties of elements
13. create Animal Schema in Animal.js
14. create Animal Controller and Service
15. in Animal Schema setup a virtual which allows us to populate additional property to the schema
    
    * in Animal schema add
    {timestamps: true, toJSON: {virtuals: true}}

    * in Animal Schema
        AnimalSchema. virtual('exhibit')
        localField: 'exhibitId',
        ref:'Exhibit',
        foreignField: '_id'
        justOne: true

16. in animal service in getAnimals
    add populate('exhibit', 'biome emoji') to the const animals = await dbContext

17. in createAnimal add await newAnimal populate('exhibit')

* restful api conventions 
* Best Naming conventions for APIs

18. another get request in Exhibits controller
    .get('/:exhibitId/animals', this.getAnimalsByExhibitId(query))
    //this is for best practice naming convention

    *getAnimalsByExhibitID(req, res, next){  //create in AnimalsService also

    }

19. create .put in exhibits controller
    and edit exhibits in services

    * Null Check
    If(!originalExhibit) throw new Error(`Unable ot find exhibit at ${exhibitId})

20. 

//query syntax

?galaxyId=64f8e232bc7597aac3b9080c


?biome=tropical&biome=desert <--- this syntax will give us all of our animals in the tropic AND desert biomes


Week 5 Day 4 
* open projects as workspace

* in server env.js enter Auth_Domain: Auth_Audience and Auth_Client_Id

* copy and paste in client folder env.js

* start server
* start client


* login then in network tab in developer tools
    should have:
    token
    userinfo
    account



