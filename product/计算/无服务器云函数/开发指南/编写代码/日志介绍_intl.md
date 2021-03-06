The log statement provides the function with the necessary information in the execution process, which is necessary for developers to troubleshoot the code. The SCF platform writes all the logs generated by the log statement in your code to the logging system. If you use the console to call the function, the console will display the same logs.

You can generate log entries using the following statements:

- print
- Logger function in the logging module

## Writing Logs Using the logging Statement

```
import logging
logger = logging.getLogger()
def my_logging_handler(event):
    logger.info('got event{}'.format(event))
    logger.error('something went wrong')
    return 'Hello World!'  
```

The code above uses the logging module to write information to the log. You can go to the log tab in the console or use the API for getting function execution logs to view the log information in the code. The log level identifies the type of log, such as `INFO`, `ERROR`, and `DEBUG`.

## Writing Logs Using the print Statement
You can also use the print statement in your code, as shown in the example below:

```
def print_handler(event):
    print('this will show up in logging')
    return 'Hello World!' 
```   

When you call this function synchronously using the **Test** button in the console, the console will display the print statement and return value.


## Getting a Log

You can get a function execution log by the following methods:

- If you are calling the function synchronously using the **Test** button in the console
 - After the execution is completed, the log of this call will be displayed directly in the console
- If the function is called by a trigger
 - The log tab of the function will display the logs generated by every function call
 - Function logs can also be obtained via the GetFunctionLogs API
- If the function is called synchronously by the Invoke API
 - The log of this call can be obtained in the logMsg field of the return value
