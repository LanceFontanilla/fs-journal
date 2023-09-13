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

1. Create Model in Movie.js
2. Create Service in MoviesService.js
3. In Homepage, create Get Movies button
    * in return create getMovies()
    lifecycle hooks are used to allow functions to be called 
    onMounted() // when component is 'mounted' to the DOM (added)
    onUpdated() // when component data is updated
    onUnmounted() // when component is 'unmounted' from the DOM (removed)

    * user used function it needs to be in the returned
    * code used function needs to be out of the returned and needs 'function' in front

    * can add the definition of the function into the return after its made outside so its used by both code and user

4. in axios create new movieApi
5. in services create getMovie service
6. in AppState 
    /**@type movie[] */
    movies:[]
7. in HomePage.vue in return add movies : computed(() => AppState.movies)
8. in Movie.js create template 
    <div v-for="movie in movies" :key="movie.id" class = "col-md-3"
    {{movie.title}}
    </div>

9. Abstract out the template into its own component
    * MovieCard.vue 
    <MovieCard :movie="movie"/> in homepage

    copy and paste template into MovieCard.vue
    
    create props: {movie: (type: Movie, required:true)}, // this sets up the component to TAKE in data

10. in Movie.js create new section row for more pages at the top
11. in HomePage new functions changePage(number) 
12. in MoviesService new changePage()   
13. in HomePage pageNumber computed
14. disable previous button when page is less than or equal to 1
15. create Modal.vue
    copy and paste modal from bootstrap

    create Template

16. in MoviesService create getMovieById()
17. in MovieCard add @click="getMovieDetails()" in div
    * in 
        setup(props)
        return{
        async getMovieDetails(){
            try{
            } catch (error)
            Pop.error(error)
        }
    }
18. add to GetMovieById for activeMovie
19. add activeMovie to AppState
20. Create SearchBar component
    * create Template


21. change changePage to URL 
    * add AppState searchTerm

22. create changePage with search
    add to buttons



Week 6 Day 3 Start of lecture
Greg's List Again!

1. fill out env.js info pulled from sandbox like normal
2. try logging in. verify token userinfo account in network tab 
3. HomePage, and NavBar, and AppVue change footer fix things for the page
4. Difference in pages and components, pages get registered in router.js
5. in router.js create path: '/cars'
6. Create CarsPage.vue in pages
7. in HomePage create router-link for cars
8. create button cars link via code 
    * create function goToCarsPage()
    - const router = useRouter()
        return{
            goToCarsPage()
            //NOTE - router push should be used only for automatically navigating the user when certain code processes are done
            router.push({name:'Cars'})
        }
9. create car model in Car.js
10. create CarsService.js  //no difference from Vanilla JavaScript
11. in CarsPage.vue create getCars with onMounted
        in setup(){
            onMounted(()=> {
                getCars()
            })
        }
        async function getCars(){
            try
        }
12. in CarsService create getCars api.get  
13. in AppState create cars[]  // puts cars into our AppState
    * when mapping make sure to check your array 
14. in CarsPage  //pulls cars from our AppState to put on page
    return{
        cars:computed(()=> AppState.cars)
    }

    build out some template in CarsPage for cars to be displayed
    then use v-for="car in cars" :key="car.id" to iterate over the array to display
    {{car.make}} {{car.model}} //makes sure data is accessible and usable
    <carCard
15. make CarCard.vue component and move template from CarsPage
    after pasting template in template you need to setup props

16. in CarCard.vue component in 
    export default{
        props: {car: {type: Car, required: true}
    }
17. in CarsPage pass the prop down in the CarsCard. 
    need the object car (not the whole array) by binding :car ="car" from the v-for loop
    <CarsCard :car="car"/>
18. in CarCard complete the template and make it look nice
19. 