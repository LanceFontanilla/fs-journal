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

step 10 