https://garywoodfine.com/redis-inmemory-cache-asp-net-mvc-core/

https://dotnetcoretutorials.com/2017/01/06/using-redis-cache-net-core/

Download redis desktop manager:
	https://redisdesktop.com/download

docker run -p 6379:6379 --name rds -d redis:5.0.5

docker logs rds

docker exec -it rds bash

redis-cli

KEYS *

You can query any KEY as follows:
	EXISTS localhostChihuahua

dotnet new globaljson --sdk-version 2.2.104
dotnet new mvc

    dotnet add package Microsoft.Extensions.Caching.Redis@2.0.2
    dotnet add package Microsoft.AspNetCore.Session@2.1.0-preview1-final

Add to appsettings.json:

    "redis": {
        "host": "127.0.0.1",
        "port": 6379,
        "name": "localhost"
    },

Add to startup ConfigureServices():

	loggerFactory.AddConsole(Configuration.GetSection("Logging"));
    loggerFactory.AddDebug();

    services.AddDistributedRedisCache(options =>
    {
        options.InstanceName = Configuration.GetValue<string>("redis:name");
        options.Configuration = Configuration.GetValue<string>("redis:host");
    });

    services.AddSession();

Add to startup Configure():
	loggerFactory.AddConsole(Configuration.GetSection("Logging"));
	loggerFactory.AddDebug();
	...
	app.UseSession();
		
Create a .NET Core class library and add this package to it:

	dotnet add package StackExchange.Redis

