# aws-lambda-standards
Aws Lambda coding standards (Local to Server)

- Install Python 3x ( 3.6 recommended )
- After installing pip install Virtualenv
- Activate Virtualenv and install the following package
    ```bash
    $ pip install python-lambda-local
    ```
    (for running aws lambda function locally)

    to get more info :
    <a href="https://github.com/shuvojit-tps/lambda_docs/blob/master/notes/running_locally.md" target="_blank">Click here</a>

- Add individual Layer in Aws to use any 3rd party packages, if required.( which are not preinstalled in aws).

    Append the python compatible version name with it.
    ex: pymysql_python_3-6
    ( where pymysql is the name of the package and it is compatible with python 3.6x version ) 

    to make the package follow the instruction:
    <a href="https://github.com/shuvojit-tps/lambda_docs/blob/master/notes/layers.md#1-using-layers-to-seperate-code-and-dependencies" target="_blank">Click here</a>

- Use Db connection from parameter ( from Aws console , System Manager > Parameter Store ) , which is already defined    
- Naming convention ( always use snake case )
  1. lambda function name
  2. request variable name
  3. response variable name

- use Tag in lambda function accordingly ( api, page, module )
  ```
  eg: 
  api = bm ,
  page = dashboard ,
  module = team ( if required )
  ```      
- Always escape the data
  Since we're not using any ORM's, none of the data is escaped thus opening a window for mysql injections, to prevent this we   have to escape all the data before generating our queries.
  
  ```python
  >>> import pymysql
  >>> data_str = "It's a string with 'unescaped' quotes."
  >>> data_str_escaped = pymysql.escape_string(data_str)
  >>> data_str_escaped
  "It\\'s a string with \\'unescaped\\' quotes."
  >>> data_dict = {"message" : "Unescaped 'quotes' in this message"}
  >>> data_dict_escaped = pymysql.escape_dict(data_dict, charset='utf-8')
  >>> data_dict_escaped
  {'message': "'Unescaped \\'quotes\\' in this message'"}
  ```

## Note
Don't implement all logics under main handler function , rather keep it seperate and call the function in main handler accordingly.

## Optional 
- Use Lambdapack   ( to zip the function for deployment)
- Use AWS cli ( to save the time )
