# NAIT ASP Project creation

` NAIT has a highly specfic project setup when making ASP .net framework project
this is becauase of a highly deprecated nature of the software they are using.`

## Steps

- Create a new ASP.NET Web Application (.Net Framework)
- - The name will be the view scope of a MVC setup
- - Use the Web Forms preset
- - If your doing **athentication** set it during this step
- - Click Create

- Create Project (Class Library) for Controller scope with name `Foo`System and Project (Class Library) `Foo`System.Data (Model scope)
- - Create folder BLL (Buiness Layer Logic) in system
- - Create folder DAL (Data Access Layer) in system
- - Reference Model scope from System scope
- - EntityFramework references in system
- - If generating models from database let wizard create Content class in DAL otherwise create it now

- - In Model project Get Foldders DTO(Classes with collections), Entities(Models), POCOS(Classes with no collections(structs))
- - Reference EntityFramework
- - Create Database connection can be done using the server explorer and adding a new SQL database
- - Then you can use the code first create entities wizard to make a context class and your entities. 
- - Move context class to DAL 
- - Add any error messages or fix entities that did not get created well. 

`This should cover the creation of a base project at NAIT if changes are needed later they will be added.`