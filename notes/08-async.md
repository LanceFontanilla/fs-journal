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



