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
    const sandboxApi = axios.create({
        baseURL: "https://sandbox.codeworksacademy.com",   //this is our base url we then append the API's to this URL
        timeout: 8000  // if this takes longer than 8 seconds throw an error
    
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

12. Now create our Form in index.html

    BootStrap Collapse has 2 parts:
    data-bs-toggle = "collapse" // what the component is doing
    data-bs-target = "name of ID that matches the div that its collapsing"
    tie create button to app.CarsController.createCar()

13. Now make a createCar() in CarsController in a try/catch
   
   
    createCar(){
    try {
        window.event.preventDefault()
        const form = window.event.target
        const formData = getFormData(form)
        await carsService.createCar(formdata)
        console.log('creating car')
    }catch{

}

    }

14. in class carsService make a createCar(formData){

}

    async createCar(formData){
        // Note any time we do a POST request, we will be supplying some kind of body
        // Note the 'body' is what we are trying to insert into the API
        const res = await _sandboxApi.post('api/cars', formData)   //res is short for response
        console.log (res.data)

    }

15. in env.js

supply the domain, audience and client id info

16. in env.js edit the baseURL

17. in async CreateCar in CarsService 

   - change await _sandboxApi.post to api.post
    
   - const res = await api.post('api/cars', formData)

   -then add  const newCar = new Car(res.data)  //this adds the newly added car to the AppState

18. UPDATE / Edits are tricky

move Form to the model

    use static instead of get

    static CreateCarForm (){
    return `
        paste form here

    `
}

19. add onclick = "app.drawCarsController" to the create listing button

20. in CarsController add drawCreateForm

    drawCreateForm(){

        setHTML('carFormCollapse', Car.CreateCarForm()) //have to invoke

    }


21. add button to edit in the CardTemplate

22. create a get ComputeEditButton so that only the correct logged account can edit the car

    get ComputeEditButton(){
    if (!AppState.account == null || AppState.account.id != this.creatorID) return ''

        if (AppState.account.id == this.creatorId){
            return ` <button> </button>

            `
        }
    }


23. add AppState.on('account' , _drawCars) in CarsController

24. add drawEditForm(){  //in cars controller
    console.log('edit car')
}

    drawEditForm(carID){
        console.log"('edit car', CarId)
        carService.setActive(carId)

    }


25. in get ComputedCarForm pass down this.id from car to know which car you are editing. shown in step above and in our button


26. 
    setActive(carId){

}

*  set active = null in AppState

27. create a function _drawEditForm(){ in carsController

}

28. create Appstate.on ('activeCar' _)

29. copy static and make it a getEditCarForm

    add value = (this.make)

30. change drawEditForm to let active = AppState.activeCar and SetHTML
    drawEditForm(carID){
        console.log"('edit car', CarId)
        let active = AppState.activeCar
        setHTML...
    }

in edit car form. need to change the get button


now create and 
    editCar(){
    try {
        window.event.preventDefault()
        const form = window.event.target
        const formData = getFormData(form)
        carService.editCar(formData)

        form.rest()
        bootstrap.Collapse.etc etc.
        console.log ('edit car')

    }catch{

    }
}


async editCar (carId)  //pass the editing car id

in carsService add put to editCar

    async editCar(formData, carID){
        console.log(formData, carId)

        const res = await api.put('api/cars/$(carId)', formData)

        const updatedCar = new Car(res.data)
        let originalCarIndex = AppState.cars.findIndex(car => car.id == carId)

        AppState.cars.splice(originalCarIntex, 1, updatedCar)
        AppState.emit('cars')
    }

    gregslist is the CRUD manual

* DELETE


Make a delete button only the person who created the listing can delete. go to your model page and make a getComputeDeleteButton

    get ComputeDeleteButton(){
        if (AppState.account == null || AppState.account.id != this.creatorId) return ''
        return `<button onclick = app.CarsController.deleteCar(${this.id}) > 
    }

in CarsController create async deleteCar(carId){}

    async deleteCar(carId){

        if(await Pop.Confirm)
    }

add button to template

in CarsService create deleteCar(carId)

    async deleteCar(carId){
        const res = await api.delete('api/cars.$(carId)')

        const filteredArray = AppState.cars.filter(car => car.id != carId)
        AppState.cars = filteredArray

    }

    WEEK 4 DAY 3

update the bootstrap css

_variable.css can change their values

1. make new service, DndSpellsService -add axios at top

    const dndapi = axios.create({
        baseURL: 'https://www.dnd5eapi.co/api/'
        timeout:5000
    })
    
    
    class DndSpellsService {

        async getSpells (){
            const res = await dndapi.get('spells')   //this is where you append to the baseURL
            console.log('got spells', res.data)    //res.data is what axios creates, always look at res.data
        }

    }

    export const dndSpellsService = new DndSpellsService

2. make new controller

    add the getSpells() in here

3. make your model
    - look at the sandbox and see what the model looks like

4. in AppState

    SpellList = []

5. in Service 

    add AppState.spellList = res.data...

6. in controller draw spell list

7. in router create your view section for the spells

8. add AppState.on in the controller

9. in Spell.js create a static SpellListTemplate

10. in controller create a get oneSpell and in Spell.js add the onclick for the function

11. in AppState add activeSpell = null

12. draw spellList

13. new controller and new service to talk to sandbox


pokemon?limit=151 for original 

image is like damage

Week 4 Day 4

Queries of APIS

* queries start with ?
* then the parameter
* then your search term
* join parameters with '&'

NASA APOD

1. make a nasaService
2. make a controller
3. tie it to the router
4. in controller getApod() with try catch
5. in services create axios instance
    - new way to create axios instance
    - added params:{
        'api_key': 'whatever_the_key_is'
        'date' : 2012-12-13  // you only really want things that you want hard coded into your baseURL
    }
    
6. add in controller constructor add this.getApod() //this runs the function on page load
7. check the sandbox model to see what you want your model to look like
8. create your class constructor model in Apod.js
9. in AppState activeApod = null  //this allows us to save the data to the AppState
10. in service class NasaService add AppState.activeApod = new Apod()   then console.log it
11. in controller draw it by function _drawApod()
    - in class constructor AppState.on('activeApod', _drawApod)
12. added the nasa img as the background in the function _drawApod
13. add sandbox keys to the env.js so you can get it off the page
14. draw the page the way you like it in the index
15. *** Add the id = ' ' to the section
16. copy the html you drew and put it in the model as get ActiveTemplate()
17. in the controller in our function _drawApod added the setHTML and setText for the copyright
18. adding class="apod-header" and class"apod-body" and creating them in CSS
19. create input type="date" and add an onchange and have it go to new getApodByDate() function in the controller
20. pass date to the service by adding nasaService.getApodByDate 
21. in service async getDataApodByDate(dateValue) pull data from api then pass data through the model to redraw the page
22. login to save the data to the sandbox
    add user in AppState
23. create a button to post to the sandbox to save
24. create a sandbox controller to tie the button to
25. add onclick to the save button to addFavoriteApod()
26. in sandbox controller create the addFavoriteApod() method
27. OFF CANVAS, for the saved list
28. create a button for the saved list <button data-bs-toggle> make sure to add the off canvas id in it
29. figure out what the favorite apods will look like and draw it inside the Off Canvas 
    and then move it to the model in get FavoriteTemplate. and string interpolate it
30. add the id = sandboxApods in the OffCanvas
31. in SandboxApodService in the addFavoriteApod add letApod = new Apod
32. in sandboxController draw the sandboxApods we want to draw when we ever add new ones
33. add AppState.on()
34. in sandboxService add AppState.emit()
35. in controller drawSandboxApods let apods - AppState.sandboxApods, let content = '' apods.forEach(apod => content += apod.   
    FavoriteTemplate.)
36. in our Sandbox
