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
19. add functionality to click car and go to details page
20. in CarCard add <router-link> to home page for now to test functionality
    <router-link to:{name:} 
21. create CarsDetailsPage
    this is the details for the car page
22. in router create 
    path:'/cars/:carId'
    name:"CarsDetail"
23. fix the router link 
    to="{name:'Car Details', params:{carId: car.id}}"
24. when we click the car it brings us to the page with car.id in url
    we need to draw the car details and pages should handle the getting of data they
    require to show/use and nothing more
25. use onMounted(()=>{
    getCarById
    })
    async function getCarById(){
        try{
            await carsService.getCarById(carId)
        }catch error
    }
    return{
        cars: computed(()=> AppState.cars)
    }

    * add const route = useRoute() above unMounted(())
    we use route to pull the carId so add 
    const carId = route.params.carId  //add this above await carsService.getCarById 

26. create getCarById in CarsService
27. in AppState add activeCar = 
28. in CarDetails Page add
    activeCar: computed(() =>)
29. Add AppState.activeCar = null //to fix the showing of wrong data for a split second
30. fix CarsDetails page to make it pretty
31. had to add v-if='active-car' to fix it trying to load before there is an active car
32. add v-else loading


33. adding form to CarsPage to create a new car
    * create CarForm component
    * add it to CarsPage with <CarForm />
34. in setup() return 
    createNewCar()
35. add v-model = "carData. ____" in the form
    add const carData = ref('')
    add await carsService.create car
36. in CarsService add createCar
    don't forget to push the car through the model to display 
    
    in CarForm add carData.value = null to get form to reset on submit 
    add const router = useRouter()

    in createCar add 
    const newCar = new Car(res.data)  //this is so we can go to the details page
    AppState.cars.push(newCar)        //when we submit but we need the carId
    return newCar

    in CarsPage function we add the
    router.push({Params: })

37. add delete button and create deleteCar function

38. after delete router push back to the Cars page
    * 

39. to the delete button, add v-if so only shows when you own the car
    add account to the return 

Week 6 Day 4

artTerminal

1. drop sandbox auth 0 into env.js
2. baseUrl is in sandbox
3. spin up website and log in and out and see token, userinfo and account
4. in HomePage remove default things in template
    * build skeleton placeholders for projects
5. create model, services, router info in order to "get" projects to page
6. started w/ model
7. create ProjectsService
    async getProjects()
8. in HomePage
    onMounted(( ))
        getProjects
    async function getProjects()
        try
        catch
9. in AppState
    add projects=[]
10. in ProjectsService add
    AppState.projects = res.data.map
11. in Homepage add in return
    projects: computed(()=>)
12. can check Vue developer to make sure everything got ported to AppState properly
    *check array and make sure all data you need is in there
13. in HopePage Template build your template to test data is coming in
    v-for="project in project" :key="project.id"
    {{ project.title }} {{ project.creator.name}}
14. create ProjectCard.vue
    copy and paste your template, or duplicate it in template of ProjectCard
15. add <ProjectCard/> to HomePage Template
16. in ProjectCard add props: (project: {type:project required})
17. add to <ProjectCard :project="project"> to bring in props and see it passed correctly
18. in HomePage Template can now 
    remove/comment out {{ project.title }} {{project.creator.name}}
19. Now it's all tested we can complete styling in the ProjectCard
20. in ProjectCard in return
    // when creating a computed to bind to, it has to have the exact value the style needs
    * coverImg: computed()=> url(${props.project.coverImg}) 
    - make sure props is passed in "setup(props)"
* "scoped" is used for that component only and not globally
21. create ModalWrapper component
    this will allow us to reuse the modal component 
22. in appView add the ModalWrapper in the footer to test
23. in ModalWrapper component add
    <slot name=header>
    can have whatever in here
    </slot>
    <slot name=body>
    can have whatever in here
    </slot>
    <slot name=footer>
    can have whatever in here
    </slot>
     in AppVue.     
    <ModalWrapper>
    can pass whatever you want in between
    </ModalWrapper> 
     in AppVue
    you can add a template and in template pass the id of whichever slot you want
in ModalWrapper
    add prop: showButton

    add id to the modal div 

24. in HopePage add new div at top with ModalWrapper with form and create project

25. in ProjectCard add data-bs-toggle for modal data-bs-target and add @click setActiveProject(
)
26. in ProjectCard create
    setActiveProject
27. in ProjectsService create
    setActiveProject(projectId){
        const project = AppState.projects.find(project => project.id == projectId)
    }
28. in AppState
    create activeProject = null
29. in AppVue
    add activeProject computed in return
30. create ActiveProjectDetails
    add activeProject computed in here instead
31. add <ActiveProjectDetails/> in AppVue template
32. style template for ActiveProjectDetails
33. add v-if activeProject so it doesn't error trying to render nothing
34. create ProfilePage.vue
35. add path for ProfilePage in router
36. add router-link in projectCard 
37. add the router-link in ActiveProjectDetails 
38. add @click=closeModal in ActiveProjectDetails
    in return create closeModal()
    in projectCard add @click.stop 
    removed bs-toggle-modal and data-bs-target
    in SetActiveProject added code to fix the modal opening when clicked
39. ProfilePage.styling
40. in ProjectsService create
    getProjectsByProfileId(profileId)
41. in ProfilePage 
    onMounted()
    async function getProjectsByProfileId
42. add const route = useRoute()
43. create ProfilesService
    async getProfileById(profileId)
44. add function getProfileById in ProfilePage
45. create profile model
46. in AppState add activeProfile
47. in ProfilesService add AppState.activeProfile = new Profile(res.data)
48. on Profile Page add profile computed
49. Profile Page style template
50. do things in Account Page so we can edit account things
    watchEffect(() => {        
    })

create ProjectForm component


in profile page add the <projectForm/>
add computed in return for projectForm

Post Man tests...

express-vue




