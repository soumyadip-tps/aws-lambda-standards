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
    [click here](https://github.com/shuvojit-tps/lambda_docs/blob/master/notes/running_locally.md)

- Add individual Layer in Aws to use any 3rd party packages, if required.( which are not preinstalled in aws).

    Append the python compatible version name with it.
    ex: pymysql_python_3-6
    ( where pymysql is the name of the package and it is compatible with python 3.6x version ) 

    to make the package follow the instruction:
    [click here](https://github.com/shuvojit-tps/lambda_docs/blob/master/notes/layers.md#1-using-layers-to-seperate-code-and-dependencies)

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

## Note
Don't implement all logics under main handler function , rather keep it seperate and call the function in main handler accordingly.

## Optional 
- Use Lambdapack   ( to zip the function for deployment)
- Use AWS cli ( to save the time )
