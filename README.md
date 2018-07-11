

// Import dependencies
const mongoose = require('mongoose');
const express = require('express');
const router = express.Router();


var Product=  {
    productname: {type: String},
    productassetid: {type: String},
    productweight: {type: String},
    productmanufacturer: {type: String}
};

const dbHost = 'mongodb+srv://mongodbtestuser2:Termina_3@cluster0-0zlxa.mongodb.net/directtestdb1?retryWrites=true';

// Connect to mongodb
//mongoose.connect(dbHost);


const MongoClient = require('mongodb').MongoClient;

// replace the uri string with your connection string.
//const uri = "mongodb+srv://shahid:<PASSWORD>@cluster0-1q7ty.mongodb.net/test"

var url = "mongodb+srv://mongodbtestuser2:Termina_3@cluster0-0zlxa.mongodb.net/";
MongoClient.connect(url, function(err, db) {   //here db is the client obj
    if (err) throw err;
    var dbase = db.db("directtestdb1"); //here
   
    Product = dbase.createCollection('Product',function(err, res) {
        if (err) throw err;
        console.log("Collection created!");

        db.close();   //close method has also been moved to client obj
    });
});
module.exports={Product:Product};
