# MVC

MVC DAY ONE (Week 3 Day 1)

Design pattern:

bcw create 

//capital C in Character to signify class model
//class creates a blueprint for a data object

class Character {

    name

    role

    health

    maxHealth

    constructor(newName, newRole, newHealth) {
        this.name = newName
        this.role = newRole
    }
}


Character then hit Tab

what order do I build in

1. Make the Model and properties 
2. create data using that model in the appstate
3. make the controller, and have the controller draw the data to the page (either with html templates or just string con-cat) 
4. add interactions to page elements
5. the rest of it.....


Day 2 MVC (week 3 day 2)

step 1, create Gachamon.js in Models
step 2, 

export class Gachamon {
add simple getter here too
    constructor (name, icon, picture, rarity){
        this.name = name
        this.icon = icon
        this.picture = picture
        this.rarity = rarity
    }
 
    get ListTemplate(){
    return `<p>$this.icon</p>`
    }
}

step 3, in AppState.js make an array of Gachamons

gachamons = [
new Gachamon ('Oslo',  'icon', '', 'common')
new Gachamon ('Benjamin',  'icon', '', 'common')
new Gachamon ('x',  'icon', '', 'common')
new Gachamon ('Oslo',  'icon', '', 'common')
]

step 4, in Controllers create GachamonsControllers.js

export class GachamonsController{

    constructor(0{
        console.log ('Time to Gachamon')
        //step 6.5 this.drawGachamons.list
       
    })
}

step 5, in router.js add GachamonController 

export const router = [
{
path ''
controller: (HomeController, GatchamonController)
view: /*HTML */

"add rows and classes or what you want in VIEW"

}

step 6, in GachamonController.js

drawGachamonList(){
const gachamons = AppState.gachamons
let listContent = ''
gachamons.forEach(g => listContent += g.ListTemplate)

//step 6.6 add below
setHTML ('gachaman-list', listContent)

}

//6.5 in GachamonsController.js draw it

]

step 7 in Gachamon.js return style your get ListTemplate to the way you want it to look

get ListTemplate() [{
    return ` <button class="btn col-1 fs-3 etc. etc. etc." title= $(this.name) $(this.icon) `
}

step 9 in here create a get for style
get ComputeRarityStyle() {
    switch (this.rarity)
    etc.
    etc.
}
]

step 8 in style.css create your class styles to the way you want it to look

step 9 above

step 10 fix button onclick in Gachamon.js  `<button onclick = "app.GachamonsController.selectGachamon('$(this.name etc. etc.)')"  `

step 11 in GachamonController.js pass the name in the selectGachamon(gachaname) function


step 12 in services create GachamonService.js

in GachamonService.js

class GachamonService{
    console.log ( this is the gachamon service)
}
export const gachamonService = new GachamonsService()


step 13 in GachamonService.js  in selectGachamon function add 

gachamonService.selectGachamon(gatchaName)
const AppState.gachamons.find(gacha => gacha.name == gachaName)   

step 14 in AppState create to make a bigger one you selected
add activeGachamon = null

step 15 in GachamonService 

AppState.activeGachamon = selected Gachamon

step 16 in Gachamon.js create new Get

get ActiveTemplate (){
    return ` etc etc 
    `

}

step 17 in router.js

create a new section in view to add the ActiveTemplate
<section class="row" id="gachamon-activity ect etc.

step 18 in GatchamonController.js
drawActiveGachamon (){
    const gachamon = AppState.activeGachamon
    let activeContent = gachamon.ActiveTemplate
}

step 19 in AppState add below above activeGachamon = null

/** @type {Gachamon}  this is the gachamon selected, by the user*/

step 20 in drawActiveGachamon()

add setHTML('gachamon-active',activeContent)

step 21 call drawActiveGachamon when it is selected in GachamonController.js
in constructor add

AppState.on('activeGachamon',this.drawActiveGachamon)

step 22 in index.html change main and add
//private viewport
<div id='router-view' class="container">
</div>
add buttons / knob stuff
<section class="etc etc."

step 23 in selectGachamon in GachamonController.js

gachaAchaMon() {
    getGachamonService.getRandomGachamon()
}

step 24 in index.html add onclick = 'app.GachamonController gachaGachamon() role=button'

step 25 in GachamonService  add getRandomGachamon() then draw it with AppState.Active 
class GachamonService {

    getRandomGachamon () 
    etc. etc.

}

step 25 AppState.js add 
/** @type (Gachamon []) */
myGachamons = []

step 26 in GatchamanController.js create drawGachamon function

drawGachamon (){
    const myGachamon 
    etc etc
}

step 27 in index.html add a place to collect the gachamon

section.row etc etc

step 28 in gachamonController.js add listener

step 29 in GachamanService add AppState.myGachamons.push(randomGachamon)

also have to add AppState.emit('myGachamons')

step 30 in GachamonService add stuff to make rares harder to get

getRandomIndex() {
    let rarities = 'common', rare. ultra-rare 
    let roll = 0
    for let = 1 etc etc.

}

add getRandomIndex to getRandomGachamon function

add to local storage

in utils folder there is a Store.js

in GachamonService create a saveMyGachamon()

saveMyGachamon(){
    saveState('myCachamon',AppState.myGachamons)
}

add this.saveMyGachamon() to GetRandomGachamon()

in AppState in init()

add this.Gachamon = loadState ('myGachamon', [Gachamon])

fixed classes with data objects (we should just start with data object)

MVC Day 3 (Week 3 day 3)
//SECTION - Gregs List
Greg's List

1. Make Model (what the info looks like)
    export class Car {
        contstructor(data){ 
            this.make = data.make
            this.model = data.model
            this.year = data.year
        }
    }

2. In AppState create the instances with dummy data to draw to the page

    cars=[
    new Car{
    make:
    model:
}
    ]

3. console log to see if things are working, where do you do it?  in controller 
// controller is responsible for user inputs and what they see

    create CarsController

export class CarsController{
    constructor () {
        console.log ('this is the cars Controller')
    }
}

4. CarsController, is run off of the router.  so in the router you add the CarsController as controller
5. now you can see in the console, the CarsController's console.log

NEW THING!!

6. create a new route object to change to the Cars Section of Greg's List
in router at the bottom is the about page path, 

path:'#/cars'
controller: CarsController,
view: 'hello from the cars page'  //this is a test to see if things are routed properly

//need a place in index.html to load the path for the cars page. using the about page as an example

NAVLINKS
add a href = #/cars  //this will add a place to click to bring up the cars page

in CarsController.js, console.log (AppState.cars) will bring up the array of cars in the console

7. in CarsController.js drawCars()

* NEW THING!!
* moving function _drawCars() outside of the class makes it private.  putting the '_' is the visual that the function is private.  //it runs in the background

function _drawCars(){
    console.log ('drawing cars')
  
}

* as soon as the cars page loads you want to draw the cars.  so, put it in class CarsController's constructor

export class CarsController {
    constructor(){
        console.log ('hello from the cars controller')
        console.log ('we got cars', AppState.cars)
        _drawCars()
    }
}

* add more to the function _drawCars to make it the way you want the page to look  


function _drawCars(){
    console.log ('drawing cars')
    let cars = AppState.cars  //aliasing AppState.cars to just cars
    let content = ''

    cars.forEach(car => content += `$(car.make))  //the $(car.make) gets changed to carsTemplate see further below
}

still need to inject some HTML to the page.  where our id = '' goes

* in router.js draw out the html

view: 

/*html*// this tag allows the colors to look like it's html
`<section>
<div> </div>
</section>
`

in index.html, draw out the cars page then put it into the get

get CardTemplate ()
return /*html*/ `copied the template from the index.html` but put it in the view in router.js

change function _drawCars to change the car.CardTemplate //the get CardTemplate in Cars.js


NEW THING!! 

FORMS!!

hard code form in index.html

<form > 

name = "make" //this matches the 

</form>

move form into car view in router.js

forms have onsubmit = "app.CarsController.createCar()"//we want it to go to CarsController.js because its in our cars page

in CarsController have a new function that creates a car 

createCar (){
    window.event.preventDefault()
const form = window.event.target // this brings in the form 
console.log ('creating car', form)
const formData = {
    make: form.make.value     //these are the key value pairs that directly reflect our models data
}

}

const formData = getFormData(formEvent)


need a service now to pass the info to

create a CarsService.js

class CarsService {
createCar (formData){
    let newCar = new Car(formData)  //need to run the form data through the constructor to have it show correctly
    AppState.cars.push(newCar)

    console.log (AppState.cars)
}
}

export const carsService = new CarsService ()

set AppState.on in CarsCOntroller.js

AppState.on ('cars', _drawCars) //this is the listener to when a car gets created in the form.


in createCar(formData) function  in CarsService.js create an emit so new cars are drawn to the page 


in CarsController create a reset of form

formEvent.reset

have car save to local storage...  we do this in CarsService.js with a private function
carsService.js deals with our data manipulation.

function _saveCars(){
    saveState('cars', AppState.cars)
}

* call this function in the: class CarsService function

* after it gets saved in local storage we have to pull it out of the local storage and load it to the page.
we do this in the AppState.js

cars = loadState ('cars', [Car])

* when we want to delete a car we have to know which specific car we want to delete 
we do this by having an id property.

we add this.id = generateId() in our export class Car{ } constructor (data) in Car.js 

* now we create a deleteCar() function that passes it to the CarsService.js

deleteCar(''){

}

in our Car.js we add a button that calls the deleteCar function


class CarsService{

    deleteCar(carId){
        let foundCar = AppState.cars.find(car => car.id == carId)

        let filteredCarArr = AppState.cars.filter(car => car.id != carId)

        AppState.cars = filteredCarArr    // see notes in the lecture web build
        _saveCars() // needs to be called here so it updates the local storage
    }
}


* in CarsController we want to have a popup to have user verify that they want to delete the car
    deleteCar(carId){
        if (await Pop.confirm("Are you sure you want to remove this car")) {
            console.log ('deleting', carId)
            carsService.deleteCar(carId)
        }
    }
//SECTION -  Redacted Started
Day 4 MVC (week 3 day 4)

Redacted

1. start in model and instantiate in "appState", 

* create "Case.js"

export class Case{
    constructor(data){
        this.id = generateId()
        this.reportBody = data.report Body
        this.reportedDate = data.reportedData ? new Date(data.reportedDate) : new Date()
        
         //need to massage line above for the case if they don't provide a date. should have a default value. we use a ternary that basically says, did they provide a date? pass the data, or create a new Date()
                                                         
        this.agency = data.agency
        this.unlocked = data.unlocked
    }
}

2. in "appState.js" instantiate a Case

Copy / *@type {import('./modes.Values.js').Value[]} */ and make it relative to Case

/** @type {import('import('./models/Case.js').Case[])} */

* build some cases for examples in "AppState"
cases = [
    new Case {
        reportBody:"Bigfoot was spotted"
        agency:'tree emoji'
    },
    new Case {
        reportBody:"Aliens made contact"
        agency:'emoji '
    }
]

3. create a "CasesController" and console.log in "CasesController"

export class CasesController{
    constructor(){
        console.log('cases controller',AppState.cases)
    }
}

4. need to mount Controller in the "router"
- in router can create a new page or replace the HomeController, here we replaced the HomeController

controller:CasesController,

5. create a "CasesService" as a placeholder for now

class CasesService {

}

export const casesService = new CasesService ()

5. create a private draw function in CasesController and add the function in the CasesController

function _drawCases(){
    console.log('drawing cases')
}

export class CasesController{
    constructor(){
        console.log('cases controller',AppState.cases)
        _drawCases() //add the _drawCases here
    }
}

6. in index.html "draw out what it looks like"

- under <main> is a good place to draw
* in case-list section added and id="case-list"

7. in "Case.js" create a getter

get ListTemplate(){
    return /*html*/ `

    //paste what you drew in index.html here and change to add 
    ${this.agency}
    ${this.reportBody}
    etc. etc.
    `
}

8. in "CasesController" under _drawCases()  create the content '' and forEach to inject the list

function _drawCases(){
    console.log('drawing cases')
    let cases = AppState.cases
    let content = ''
    cases.forEach(caseObj => content += caseObj.ListTemplate)
    setHTML('case-list', content)
}

export class CasesController{
    constructor(){
        console.log('cases controller',AppState.cases)
        _drawCases() //add the _drawCases here
    }
}

9. create new getter in "Case.js" to Compute Report title, 

* NEW! slice feature
- in Case.js

get ComputeReportTitle(){   //slice.(starting index, ending index)
    return this.reportBody.slice(0,15) + '...'
}

10. in getListTemplate adding selectable and an OnClick

<div class = "d-flex justify-content-between" onclick=""

11. in "CasesController"

create setActive(caseId){
    console.log
    casesService.setActive(caseId)
}

12. in "CaseService" 

pass the caseId to Case Service

class CasesService {
    setActive[caseId]{
        let foundCase = appState.cases.find(caseObj => caseObj.id == caseId)
        console.log('setting active', foundCase)
    }
}

13. in AppState save the active case by making:
- also copy type and make it null

/**@type .......... Case|null */
activeCase = null

14. in "CaseService"
- add AppState.activeCase = foundCase

class CasesService {
    setActive[caseId]{
        let foundCase = appState.cases.find(caseObj => caseObj.id == caseId)
        console.log('setting active', foundCase)
        AppState.activeCase = foundCase
    }
}

15. in "CasesController"
- create function _drawActive

function _drawActive(){
    console.log('drawing active')
}

- then add AppState.on('activeCase',_drawActive)

create setActive(caseId){
    console.log
    casesService.setActive(caseId)
    AppState.on('activeCase', _drawActive)
}

16. in index.html draw active case view

17. put activeCaseTemplate to a new get in "Case.js"

get ActiveCaseTemplate(){
return /* html */ `

* paste what you made in index.html here and string interpolate the ${this.reportedDate} etc.

`
}

18. in "CasesController" do more to the function _drawActive

function _drawActive(){
    console.log('drawing active')
    let active = AppState.activeCase
    setHTML('active-case',active.ActiveCaseTemplate)
}

19. in "Case.js" create a new get for the reported date view

get ComputeReportDateView(){
    let date = this.reportedDate
    return date.toLocaleDateString("en-us", {weekday: long etc.etc.})

}

20. in "Case.js" create a new array for classified words

const _classifiedWords = ["aliens", "IHOP", "people", "lizard", "rat"]

21. in "Case.js" create a new get ComputeRedactedReportBody()

get ComputeRedactedReportBody(){
    let reportArr = this.reportBody.split(' ')

    let redacedArr = reportArr.map(word=>{
        if(_classifiedWords.includes(word.toLowerCase())){
            return 'black boxes'
        }
        return word 
    })
    return redactedArr.join(' ')
}

22. changing CaseTemplate to redactedCaseTemplate and copying it and have and unredactedCaseTemplate

23. in our caseController and create and if statement to handle the drawing of the redacted or unredacted version

function _drawActive(){
    console.log('drawing active')
    let active = AppState.activeCase

    if(active.unlocked == true){
    setHTML('active-case',active.ActiveCaseTemplate)

    }

}
24. create a button in getRedactedCaseTemplate to unlock/lock case

25. in "CasesController" create an unlockCase() function that calls to our CaseService 

unlockCase(){
    caseService.unlockCase()
}



26. and in "CasesService" create unlockCase() function

unlockCase() {
    console.log('unlocking',AppState.activeCase)
    let active = AppState.activeCase
    active.unlocked = true
    AppState.emit('activeCase')
}

27. Create new Save button in getTemplate with an onclick

28. make a saveCase function in "CaseController" 

29. in services make the SaveCase function also
30. made changes to the lock and unlock and redacted/unredacted versions
31. now we save to local storage in CaseService make a function _saveCases()
    _saveCases(){

    }
32. have to recall from local storage by commenting out the hardcoded data and 

cases = loadState('cases')

33. create form in index.html
NEW!!! SELECT with OPTIONS  it's a dropdown menu!!

34. make new cases and save to local storage

in createCase we can set it as active case so be shown

newCase.unlocked = true //make new case as unlocked
AppState.activeCase = newCase  //makes it so new case made is the active case


