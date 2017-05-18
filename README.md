# Config Management System

## Introduction
Config Management System will consist of two libraries Config Management Core and Config Management Server.
Config Management Core is an independent library that can work with json documents stored in redis. It will
provide read, search and update features on json documents stored in redis.
Config Management Server will be open sourced soon. It is expected to provide server-side APIs for all the operations.
 
### Examples:
```
  {"a": 
    {
      "b": [
        {"c": "v1"}, 
        {"c": "v2"}
      ]  
    }
  }
```
 
is stored against key "K" in CM System, the redis will contain following entries:
```
"K" = {"a": {"b" : [{"c": "v1"}, {"c": "v2"}]}}
"K/a" = {"b" : [{"c": "v1"}, {"c": "v2"}]}
"K/a/b" = [{"c": "v1"}, {"c": "v2"}]
```

To read "K/a" redis will directly return the value and the library will just return  that value. 
To read the value for key "K/a/b[0]/c" which is not directly present, the library reads value for "K/a/b" 
then it applies the JSONPath library to extract the value for exact key.

## Getting Started

  * Prerequisites: Java 8, sbt, redis
  * Installation: 
    1. Do a git clone of this project
    2. cd config-management-core  
    3. sbt clean test:compile publish (builds your project and creates the jar)
    4. sbt eclipse (If you want to import the project to eclipse)
    
## How to use
    Please read the "How to use section" of Config Management Core
 
## License 
  * [Apache License Version 2.0] (http://www.apache.org/licenses/LICENSE-2.0)
  
## References
  * [jedis](https://github.com/xetorthio/jedis)
  * [json4s](https://github.com/json4s/json4s)
  * [JsonPath](https://github.com/jayway/JsonPath)