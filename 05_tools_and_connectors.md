

- WebUI
    - Snowsight
- Command Line
    - SnowSQL

Can use command line to install snow sql on our local machine

Drivers
- Go 
- JDBC 
- .NET 
- Node.js 
- ODBC 
- PHP PDO

Connectors
- Python
- Kafka
- Spark

Partner COnnect as well

## Scripting

Used in stored procedures

Can also be used in procedural code

Scripting
- Declare
- Begin
- Exception
- End

SPROC
```
CREATE PROCEDURE calc_area()  
    returns float
    LANGUAGE SQL  
    AS  
DECLARE 
length_a float;
area flaot;
BEGIN
length_a := 4;
area := lengtha_a ** 2;
return area
end
```


INTERFACE
```
CREATE PROCEDURE calc_area()  
    returns float
    LANGUAGE SQL  
    AS  
$$    
DECLARE 
length_a float;
area flaot;
BEGIN TRANSACTION
length_a := 4;
area := lengtha_a ** 2;
return area
end TRANSACTION;
$$
```

## Snowpark

Build app and query outside the system, no need to move data

- Python
- Java
- Scala

Benefits
- Lazy Eval
    - Expression is not evaluated until it is needed
- Pushdown
    - Code is pushed down to Snowflake and executed there
- UDFs inline
    - Created function can be execute ind UDFs