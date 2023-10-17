# CSharp

Day 1 C#

* For server language

Console.WriteLine("Hello, World");

* variables

can use var x = 10; //this is inefficient because there is no data type

// the new best practice is to declare everything STRICTLY with data types
use int y = 10;
float z = 4.5f;
double a = 5.55l;
decimal b = 6.80912m;

string greeting = "hello";  //must use " "
char g = 'g';  //single characters must use ' '

bool ok = true;
bool no = false;

// Array<int>[3] = new Array<int>{1,2,3}; Arrays are not cool. They have fixed length that can't be modified.

// Lists work like Arrays do in JavaScript
List<string> cats = new List<string>(){"Iron Man", "Georgie"};
cats.Add("Gopher");
cats.Add("Bean");
cats.Add("Garfield");
cats.Add("11");
Console.WriteLine(cats.Count);
string catToRemove = cats.Find(c => c == "11")
cats.Remove(catToRemove);
cats.ForEach()

"data types" can take in "arguments".  this "List" is taking in "strings"
This class needs to be instantiated like in JS  new List<string>(){}

Errors stay in code until the server is re-spun because it needs to be recompiled.

Dictionary<> //requires (key value pairs) 2 type arguments TKey and TValue T=type

Dictionary<string, int> codeWorksCats = new Dictionary<string, int>();
codeworksCats.Add("jeremy", 7);
codeworksCats.Add("Sam, 1");
codeworksCats.Add("Savannah, 3");

Dictionary<List<string>, string> actualCats = new Dictionary<List<string>, string>();
actualCats.Add(cats, "jeremy's babies")
actualCats.Remove(cats);


//NOTE - Members are created with CAPITAL letters. variables and parameters are lowercase
class Cat{
    string Name;
    string Color;
    int Age;

    public Cat(string name, int age, string color)
    {
        Age = age;
        Name = name;
        Color = color;

    }
    <!-- public Cat(string name, int age, string color)
    {
        this.Age = age;
        Name = name;
        Color = color;
    } -->
}

List<Cat> catsTheMovie = new List<Cat>();



dotnet-auth

appsettings.json is like our .env file

in .Net we are responsible for the repositories

* in Models create Cat.cs
    class Cat{
        public int Id {get; set;}
        public string Name {get; set;}
        public string Color {get; set;}        //can right-click and add parameter to the constructor
        public readonly int Age {get; set;}
        private bool Feisty {get; private set;}
    

    public Cat(){
        Id = id;
        Name = name;
        Color = color;
        Age = age;
        Feisty = feisty;
    }
}

accessors can be used in our class definition 
public
public readonly
private

* create CatsController
    //NOTE - data decorators/attributes effect the next definition, making our class an API CONTROLLER with the route ".../api/cats"
    [Api Controller]
    [Route("api/cats")]
    public class CatsController : ControllerBase{

    }

    [HttpGet]
    public GetTest(){
        try
        {

        }
        catch (Exception e)
        {

        }
    }

now must strictly define our functions calling them public and defining what we're returning

public string GetTest("test"){  //NOTE - test appends to the Route of api/cats
    return "hey it worked";
}

https://localhost:7045 is the default .Net starting page

in run and debug click add config server

[HttpGet]

public List<Cat> GetCats(){
    try
    {

    }
    catch (Exception e)
    {

    }
}

* create CatsService

    public class CatsService{

    }

we want to bring CatsService into CatsController but we don't have imports and exports like we do in JavaScript, we use namespace

* in cats Model we add 

namespace catRoundUp.Models;


* in catsController at top add

using catRoundUp.Models;

* in CatsService

private readonly CatsService _catService;
public CatsController {CatsService.cs}{
    _catsService = cs;
}

Global.cs has: 
global using catRoundup.Repositories;
global using catRoundup.service
global using catRoundup.


* create CatsRepositories
    namespace catRoundups.Repositories;

    public class CatsRepository{
        private List<Cat> _FakeDb;
    }

    public CatsRepository()
    {
        _FakeDB = new List<Cat>{
        _FakeDB.add(new Cat(1, "Georgie", "Orange", 5, false))
        _FakeDB.add(new Cat(2, "Bean", "Black", 5, true))
        _FakeDB.add(new Cat(3, "Garfield", "Orange", 27, true))
        }
    }
        internal List<Cat> GetAllCats()



* in catsService bring in CatsRepository

List<Cat> is replacing const because C# is strict and needs to know what the data type is

- not all code paths return a value

in errors look at the word before the < and the last word inside the < > and it'll give you a hint of what is happening

* in CatController add ActionResult to the ActionResult<List<Cat>> GetCats(){
    return Ok(cats);

    catch Exception e

    return BadRequest(e)

}

* in Startup.cs we need to create a dependency

services.AddScoped<CatsRepository>();  //order does matter
services.AddScoped<CatsService>();


passing id's * look at getCatById

[HttpGet("{catId}")]


controller to service to repository

function that doesn't return a value you use void




C# Lecture Day 2

dbSetup.sql 

Tables are now what schemas used to be

* create table
in dbSetup.sql
* INSERT INTO hotdogs
* SELECT * FROM hotdogs; //all columns from hotdogs

can SELECT name, price FROM hotdogs, //only name and price from hotdogs
can SELECT name, price FROM hotdogs, WHERE 'hasKetchup' = true; //only name and price of hotdogs that has ketchup
can SELECT name, price FROM hotdogs, WHERE 'hasKetchup' = true AND price < 6; //only name price of hotdogs that has ketchup and < $6
SELECT name, description FROM hotdogs, WHERE description LIKE '%jalapeno%';


mysqltutorial.org for reference guide 

id INT AUTO_INCREMENT PRIMARY KEY, 

SELECT * FROM hotdogs WHERE id = 1;

DELETE FROM hotdogs;



default charset utf8mb4 COMMENT '';

* GregsLIst

* CREATE TABLE cars
* INSERT INTO cars

appsetting.Development.json

* fill out connection string that Mick slacks out with our info
* Models
* Controller - right-click New C# Controller 
* Services - right-click New C# Class
* Repository -right-click New C# Class

* startup create dependencies
services.AddScoped<CarsRepository>();
services.AddScoped<CarsServices>();

* in CarsRepository.cs we have to write SQL to call to our database

    internal List<Car> GetAllCars()
    {
        string sql = "SELECT * FROM cars;";
        List<Car> cars = _db.Query<Car>(sql).ToList();
        return cars;
    }

can test/debug SQL statements in dbsetup to make sure it all works

in internal string RemoveCar look at //THIS IS where we WOULD check for ownership


strings are nullable by default
you can make int a null by putting a ? after it in models
?? is the null coalescence verifier 

Day 3 C# POST IT with AUTH

* Add your Connection String in appsetting.Development.json
* add the Auth0 info also into appsetting.Development
* add Auth0 in env.js base url https://localhost:7045

* dbSetup "schema" to pull info from different tables
* in dbSetup execute account table then log in to populate the account table
* create table for albums
    - TINYINT is a BOOLEAN alternative
    - creatorId relies on another table so you use FOREIGN KEY
    - FOREIGN KEY(creatorId) REFERENCES accounts(id) ON DELETE CASCADE //ON DELETE CASCADE deletes all albums with that creatorId

* JOINS 
    * SELECT * FROM albums JOIN accounts; //pulls all info from albums and accounts tables
    * SELECT * FROM albums alb JOIN accounts act ON id act.id = alb.creatorId;
    * SELECT alb.*, act.name FROM albums alb JOIN accounts act ON act.id = alb.creatorId;
    * SELECT * 
      FROM accounts act
        JOIN albums alb ON alb.creatorId = act.id
        WHERE act.id = 'idString'

* create model
    - prop is a snippet
* create repository, then service, then controller so dependencies are already made
* Startup.cs add services.AddScoped<AlbumRepository> and <AlbumServices>

* Apps Controller [HttpGet]
* update model to join account
    - public Account Creator { get; set; }
        - Account is the model that gets joined to the Creator line
    - In Repo
        - add JOIN accounts act ON act.id = alb.creatorId // account id matches the creator id
        - change SELECT alb.*, act.*
        - List<Album> albums = _dbQuery<Album, Account, Album>(sql, (album,account)=>
        {
        album.Creator = account;
        }).ToList(); //order of <Album, Account matters and it matches the SELECT order.


* [AUTHORIZE]//how to make sure the user is authorized before creating
* [HttpPost]
    -   need to use Auth0 to assign the creator
    -   private readonly Auth0Provider _auth0; // add to top
    -   Auth0Provider auth0 // add to constructor

    - in the [HttpPost]
        - add async Task<ActionResult<ActionResult<Album>> Create....
        - add Account userInfo = await _auth0.GetUserInfoAsync<Account>(HttpContext);
        - albumData.CreatorId = userInfo.id;
        - need to join account to album in our sql SELECT
    
* [HttpGet("{albumId}")]
    public ActionResult<Album> GetById(int albumId)

* 

recipe CRUDs
Don't bring laptop to ask questions. 

Day 4 Notes

Creating POST IT pictures

* Create Table for pictures
    - make sure all references are setup properly and all have the correct Data Types
    - need to have ON DELETE CASCADE on FOREIGN KEYs



* newPicture.Creator= userInfo; //use with collaborator

* endpoints in postman show where the CRUD routes need to go

* get pictures in album will be in the albums controller

* [HttpGet("{albumId}/pictures")]
* bring in picturesService into the albumController

* in repository sql SELECT, have to decide how to query the database for just the pictures in the albumId

* create Collaborator TABLE Many to Many

* services can talk to services but services shouldn't talk to another services repository

* Collaborator repo 
    - just SELECT LAST_INSERT_ID()

This is special for the Collaborator Get
* in Account.cs
public class AccountCollaboratorViewModel : Account 
{
    public int CollaboratorId { get; set; }
}

Album Controller
[HttpGet ("{albumId}/collaborators")]


REVIEW WEEK BEFORE FINAL!!

INSTACULT 

Enter env.js file and dbDevelopment infoString
Spin everything up to make sure it all works!
SERVER SIDE:
* create model cult
* create controller, service and repo
* in Startup add Scoped for dependencies
* create Table for cults
* enter data for table

* create get cults

* add Account Leader to Model
* add JOIN accounts ON accounts.id = cults.leaderId

* Tid adds a generic type  
* can extend Profile to Account to pull off info like email and CC#s 

* create getbyId
* get all and get by id is very similar

* create POST aka createCult
* [HTTPPost] 
[ AUTHORIZE ]

* get Cults, change where you see only cults that are invitation false

* cultsService filter info with FIND ALL and return filtered
* modify getCults to use HTTPContext to pass down userId
LIST<Cult> filtered = cults.FINDALL (cult => )

Object reference not set to an instance of an object. //This means you said something was going to be an object but it's not an object.

userInfo?.id = using the elvis operator now passes null down 

*NOTE - make sure to have account before requesting info

* account middleware

beforeEnter:AuthGuard //blocks non logged in users from accessing page, will prompt to log in
beforeEnter:AuthSettled //waits for the automatic login 

if getting errors with Auth0 wait like a minute

* index body can make it bg-dark to make whole page dark

*NOTE - picture background where it changes one from another is important for the final

* components that don't have a lot of complex code can remove setup and return 

DAY 2 CULT continued

* create CultMember
    * has special join to add account info
    * has memberCount
    * in CultMemberService CreateCultMember, call to the _cultService to update MemberCount



* make sure dependencies go in order by NOT having them point at each other. Find the most direct route to where one can go before the other

* cult member delete LOOK FOR REFERENCE FOR FINAL

can't leave the cult, leader can only exile you... so only the person who created the cult can do this action
need to get CultMemberById. just want the one ID for this info. 
used the updateMember count to decrease the memberCount

FRONT END

in Models changed Account to extend newly created Profile then extended to add Cultist 
not it closely matches the model from the backend

Need to make cultId an object { }
const cultID

Cultist smaller template
shows how to get props to the v-for


