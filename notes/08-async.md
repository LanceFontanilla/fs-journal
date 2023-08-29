# Async


WEEK 4 DAY 1

Asynchronous code!

* Allows for a pause before moving to the next line of code.

* uses promises to execute this

* 3 states of Promise, pending, resolve and reject

* rejection is an error

*   try {

    }catch{

    }

* can only await a promise

- promise is a class that takes in a function

**SECTION - APIs

* Create a MonstersController, MonstersService and a Monster Model

* Inside MonstersController create a getMonsters

* getMonsters(){
    monsterService.getMonsters
}

        **must have an async when using an await
* create async getMonsters class in service

NEW*** 

const response = await fetch (URL)
console.log (response)

class MonsterService{
    
    async getMonsters(){

    const response - await fetch (URL)
    const data = await response.json()

    let newMonsters = data.data.map(monster => new Monster(monster))
    }

}


* new way to get data, AXIOS

- need new script tag axios

const response = axios.get(SAME URL)

WEEK 4 DAY 2
CRUD METHOD

GregsList Async

* sandbox.codeworksacademy.com/api
    - add whichever api you need after api

1. Create all files, verify everything is working with console.logs
    - CarsController.js
        - export class CarsController{
            constructor(){
                console.log('hello from the cars controller'
                )
            }
        }

    - CarsService.js
        -  class CarsService{

            getCars(){
                throw new Error('Method not implemented')
            }
        }

    - Link Router to CarsController

    - create router Path for cars
    path:#/cars 
    controller: CarsController
    view: 'hello from the cars page'

2. in CarsController - create a get to get data from the Sandbox API
    create a try/catch, in the class CarsController add this.getCars()


    - getCars() {
        try{
            await.getGars

        }catch(error{
            Pop.error(error.message)
        })
    }

3. use AxiosService by creating an Axios instance in CarsService.
    const sandboxApi = axios.create{(
        baseURL: "https://sandbox.codeworksacademy.com"   //this is our base url we then append the API's to this URL
        timeout: 8000  // if this takes longer than 8 seconds throw and error
    
    )}

4. in class CarsService {  fix the async getCars() to go to the API
        
     async getCars(){
            const response = await _sandboxApi.get('api/cars')  
                                                  //this is where we append the api/endpoint we are going to from the base URL
            
            console.log(response.data)  //the .data is drilled down to what we really want
        }
}

    * go to Network folder and look whats responding
    * axios is better than fetch because it handles the fetching and JSON formatting

5. need to get data from server onto the page. draw data to the page  

    make our Cars.js model

    export class Car{
        constructor(data){
            this.id = data.id
            this.make = data.make
            etc. etc.
            this.creator = data.creator
            this.creatorID = data.creator.id  // adapt method is making it easier for you by 
                                              //drilling down into an object and naming it yourself
            //this is also known as flattening the database
        }

    }

can copy the object from the console by right-clicking and copying.  then you can paste and know the data for the constructor  

6. in CarsService

     async getCars(){
            const response = await _sandboxApi.get('api/cars')  
                                                  //this is where we append the api/endpoint we are going to from the base URL
            
            console.log(response.data)  //the .data is drilled down to what we really want

        *  const mappedCars = response.data.map(dataObj => newCar(dataObj))  //this passes data obj from api thru car constructor
        *  console.log('mapped', mappedCars)
        }

7. in AppState make a place to save data

    /** @type {import('.moodels.Car.js').Car[]} */
    cars = []

8. in carService

    add 
        AppState.cars = mappedCars

     async getCars(){
            const response = await _sandboxApi.get('api/cars')  
                                                  //this is where we append the api/endpoint we are going to from the base URL
            
            console.log(response.data)  //the .data is drilled down to what we really want

          const mappedCars = response.data.map(dataObj => newCar(dataObj))  //this passes data obj from api thru car constructor
          console.log('mapped', mappedCars)
       *  AppState.cars = mappedCars
        }

9. in CarsController create a _drawCars{}

    function _drawCars(){
        console.log('drawing cars')
    }

        add AppState.on('cars', _drawCars) //in the constructor class... 'cars' is what you called the array in AppState

10. Build your template of what you want your draw to look like

    in Cars.js add your get

    get CardTemplate(){
        return `
        
        paste what you drew here and string interpolate the ${this.data}
        
        `
    }

11. in CarsController add to function _drawCars to inject the car template

    function _drawCars(){

        let template = ''
        AppState.cars.ForEach(car => template += cars.drawCars)
    }

12. Now create our Form

    BootStrap Collapse has 2 parts:
    data-bs-toggle = "collapse" // what the component is doing
    data-bs-target = "name of ID that matches the div that its collapsing"

    