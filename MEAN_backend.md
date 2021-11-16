# Initial setup
1. install VS code
2. install prettier extension
3. execute => npm init
4. install prettier => npm install prettier
5. udpate the config file [https://prettier.io/docs/en/configuration.html]
6. Use Shift +Optn+F to format
7. Install nodejs 

# Configure DB(Mongo Altas)
1. https://account.mongodb.com/account/login - use this link to create an account
2. Create a project(Development -> create project)
3. Create a cluster
# Install and configure postman for RESTful api test

# Creating backend server with express

1.npm init
2. provide all basis info like project name and version

3. install nodemon for continues deployment
4. install express => npm install express

5. Initialize the server with express
    const express = require('express')
    const app = express();
    
    app.listen(3000, ()=>{console.log('server started')});
    
6. Create default get API
    app.get('/', (req, res)=>{res.send('Hello API');})
    
7. Create a env file to keep the constant in common place and access
8. In order to access this, we need to install doenv => npm install dotenv
9. accessing env by 
    require('dotenv/config)

    const api = process.env.API_URL
    
    
10. When we send the post request express should understand the body of the content,, for we need to use middleware => app.use(express.json())

# Logging API request.

1. install morgan => npm install morgan
2. use morgan
    const morgan = require('morgan')
    
    
    //Middleware
    app.use(morgan('tiny'));
    
# Installing mongoose and connecting to mongodb

1. install mongoose => npm install mongoose => responsible for connecting mongodb
2. Copy the connecting string from mongodb
    Database => Connect => Choose a connection methood => Connect your application
    mongodb+srv://<username>:<password>@cluster0.xkcal.mongodb.net/myFirstDatabase?retryWrites=true&w=majority
3. For connecting, need username, password
    Database access => Add new Database User
4. Create a database
        Collection and create new database
        Add ip into Network access to access application from local machine
        Update the connection url(username password and database) and placed it under env to access globally
5. Intall mongo compass (DB IDE tool)
    
# Installing CORS to allow request from frontend
    npm install cors

# Configuring data model and schema
     In order to conenct mongo db we need to define schema and and model
    
  models:
    
    const mongoose = require('mongoose');
```
const categorySchema = mongoose.Schema({
    name: String,
    image: String,
    countInStock: {
        type: Number,
        required: true,
    },
});

exports.Category = mongoose.model('Category', categorySchema);
    ```
    
    routers:
    
    ```
    const express = require('express')
const router = express.Router();
const Category = require('../models/categories')

router.get('/', async (req, res) => {
    const categoryList = await Category.find()

    if (!categoryList) {
        res.status(500).json({ success: false })
    }

    res.send(categoryList)
})
    ```
    
 # Hasing password
    
    1. install bcrypt => npm install bcryptjs
    
    
