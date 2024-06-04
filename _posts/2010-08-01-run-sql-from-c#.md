---
layout: post
title:  "Execute and Run SQL script from C#"
date:   2010-08-01 07:40:05 +0100
---

I work in a project that used an integration testing that need to check
for a specific data in the DB so as the best practice I just want to
insert my test data into the DB and then run my test and at the end of
the test remove this data to restate the DB to the original state so I
search for a way to execute SQL script or run SQL script quickly and
efficiency that may need DDL and DML so I use the following code

```C#

using System.Data.SqlClient;
using System.IO;
using Microsoft.SqlServer.Management.Common;
using Microsoft.SqlServer.Management.Smo;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            string connectionString = "Data Source=.;Initial Catalog=MyDB;Integrated Security=True";
            FileInfo file = new FileInfo("D:\\myscript.sql");
            string script = file.OpenText().ReadToEnd();
            SqlConnection sqlConnection = new SqlConnection(connectionString);
            Server server = new Server(new ServerConnection(sqlConnection));
            server.ConnectionContext.ExecuteNonQuery(script);
        }
    }
}

```

Note you have to reference the following DLLs

- Microsoft.SqlServer.ConnectionInfo and
- Microsoft.SqlServer.Management.Sdk.Sfc 

My first problem was where is the Microsoft.SqlServer.Management.Smo? and where is the
Microsoft.SqlServer.Management.Common? you will find them 

`\"C:Program Files (x86)Microsoft SQL Server100SDKAssemblies\" `

and if you can\'t find them you can go to the following link so you can download them and it\'s
related DLLs [click here](http://www.microsoft.com/downloads/en/details.aspx?FamilyId=C6C3E9EF-BA29-4A43-8D69-A2BED18FE73C&displaylang=en)

The second problem was that I have the following error 

```
\"Mixed mode assembly is built against version \'v2.0.50727\' of the runtime and
cannot be loaded in the 4.0 runtime without additional configuration
information\" 

```

So you have to add the following underline text in the
app.config so it will look like the following 

```c#

<?xml version=\"1.0\"?\> 
<configuration\>
<startup\><supportedRuntime version=\"v4.0\" sku=\".NETFramework,Version=v4.0\"/\></startup\> 
<startup useLegacyV2RuntimeActivationPolicy=\"true\"\> <supportedRuntime version=\"v4.0\" sku=\".NETFramework,Version=v4.0\"/\></startup\>
</configuration\>

```

That\'s it
