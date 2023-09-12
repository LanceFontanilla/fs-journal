# Vue

Week 6 Day 1

Vue - front end framework

package.json is for dependencies like Auth0, mdi font, axios etc.
.config files are for the intellisense 

npm-i installs dependencies if you ever fork a project

the play button runs vite so don't have to use bcw serve

main.js is the entry point to all the javaScript

Components are like a controller and view in one
in vue we write single file components 

v- is an attribute

: is short hand for bind
@ is another short hand that binds to event

router-link Vue's way to navigate

generally 150 lines of code for that one component

computed is like AppState.on

Vue handles our draw function

App.vue has the header and footer and main router .view

Reactivity in Vue is opt-in, you have to opt-in

3-4 different ways to make it reactive

1. let health = ref(100) //make health a reference which makes it an object.  Not recommended because we don't mess with data in the controller.  
    
    
    * property, "_____" was accessed during render but is not defined on instance, NOT IN AppState
    * only objects can be reactive
    * console doesn't clear errors, only on refresh it clears

2. const health = computed(() => AppState.health) //computed is the Get

ctrl space bar to import files

* FoodItem v-for="item in ____"


fork vue-playground
npm i


Week 6 Day 2 Lecture

