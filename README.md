# Atlas for Apache Superset

## Atlas SQL Interface

Atlas SQL Interface supports SQL Query using JDBC driver, refer https://github.com/fk-mongodb-demo/19_atlas_sql/blob/main/README.md for details.

However Apache Superset currently requires a Python DB-API database driver and a SQLAlchemy dialect to be installed for each database engine you want to connect to, refer https://superset.apache.org/docs/configuration/databases for details.

We may not be able to directly query MongoDB from Apache Superset.

However it is possible to develop custom JDBC Connector, as shown below.

## Apache Superset JDBC Integration Guide - October 2024
Explore the seamless integration of Apache Superset with JDBC for efficient data analysis and visualization.

## Understanding JDBC in Apache Superset
Apache Superset offers a variety of methods to connect to databases, one of which is JDBC (Java Database Connectivity). While Superset primarily uses SQLAlchemy for database connections, it's possible to extend Superset to use JDBC for databases that may not have a SQLAlchemy dialect.

## JDBC Connection Overview
To establish a JDBC connection in Superset, you would typically need to:

* Ensure the JDBC driver for your database is available.
* Write a custom connector if one doesn't already exist, similar to the Druid connector.

## Writing a Custom JDBC Connector
Here's a high-level guide on writing a custom JDBC connector:

1. Implement a new DB engine spec that extends the BaseEngineSpec.
2. Define connection methods, query execution, and result fetching logic.
3. Register the new connector with Superset.
   
## Considerations for JDBC in Superset

* JDBC connections can be more complex to set up compared to SQLAlchemy.
* The database should support OLAP-type queries and typical SQL operations like aggregation and filtering.
* Ensure that the JDBC driver is performant and stable for production use.

## Example: Connecting to Apache Drill via JDBC
```
// Example JDBC URL for Apache Drill
String drillJdbcUrl = "jdbc:drill:drillbit=<host>:<port>";
// Establishing a JDBC connection
Connection connection = DriverManager.getConnection(drillJdbcUrl);
```

## Best Practices

* Use JDBC only when necessary and prefer SQLAlchemy when available.
* Test the custom connector thoroughly before deploying to production.
* Monitor performance and stability of the JDBC connection.

## Reference

* https://www.restack.io/docs/superset-knowledge-apache-superset-jdbc-integration
