# LogicAppsStandardStoredProc

Logic Apps Standard has a built-in connector for SQL Server/Azure SQL. This has the benefit of being able to communicate over a private VNET, and as the connector is built-in, also has performance gains as it is not subject to the throttling limits the cloud connector has. At the time of writing, the built-in connector has the ability to execute a SQL statement, so how do you call a stored procedure and pass pramaters? The following snippet in Code View shows how to do this. For the query, simply exec the stored proc and pass the parameters required:

"SQL": {
                "type": "ServiceProvider",
                "inputs": {
                    "parameters": {
                        "query": "exec [ParamTest] 'testval', '@{triggerBody()?['address']}'"
                    },
