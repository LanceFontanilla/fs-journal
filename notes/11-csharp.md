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




