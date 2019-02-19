# Web-Api-with-Asp.Net-Core
Sample Web API built with Asp.Net core, configured with entity framework core and DB set up in Azure

### Create SQL Server DB on Azure
	1. Create a resource of type <SQL Server(logical server)>
	2. Create a storage account
       1. All Services > Storage Accounts > add a new storage account
   ##### (You need to have backup files from existing tables that are created in SQL Server for the following step)
	3. Create a container for backpack files (backup files)
       1. Open the SQL server > Import Database
       2. Select Storage account
       3. Add or select a Container to hold the backpack file
       4. Upload the backpack file and select it 
       5. Storage Set is ready for Import database
       6. Copy connection string
   ##### (Security issues in Azure will not allow outside access to database) 
	4. Set Firewall settings to allow outside access     
	   1. Set Firewall settings > Add Client IP (Sets a rule based on current IP address)
    
### Configuring Entity Framework Core in Web Api
##### Create tables as given in the DB by scaffolding with the following command in NuGet Package Manager Console

`Scaffold-DbContext "Server=<server> Catalog=H_Plus_Sports;Persist Security Info=False;User ID=<userid>;Password=<password>;MultipleActiveResultSets=False;Encrypt=True;TrustServerCertificate=False;Connection Timeout=30;" Microsoft.EntityFrameworkCore.SqlServer -OutputDir Models`

### Model Binding :- Get information from the routes and from the HTTP call into actions
##### Attributes for model binding

	1. [BindRequired] - required; if not found in the route or HTTP request, an error will be logged in the model state
	2. [BindNever] - never bind the associated parameter
	3. [FromHeader] - specify the exact binding to apply
	4. [FromRoute] - binding to a variable is sent across the route
	5. [FromServices] - bind objects injected inside the project through startup
	6. [FromBody] -  bind content located inside request body


