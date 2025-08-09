// middlewares/app.js
const express = require('express');
const app = express();
const port = 3000;

app.use(middleware2);
app.use(middleware1);


function standardexpresscallback(req,res,next){
  console.log("hello from express")
  res.send("Hello from express");
  
}

function middleware1(req,res,next){
  if (req.path === '/favicon.ico') return next();
  if (req.path === "/") {
    console.log("i am middleware1");
  }
  next();
  
  
}

function middleware2(req,res,next){
  if (req.path === '/favicon.ico') return next();
  if (req.path === "/") {
    console.log("i am middleware2");
  }
  next();

}
// either u can pass ur middleare1 function here or  can declare it globally
// using app.use()
// app.get("/",middleware1,standardexpresscallback);
app.get("/",standardexpresscallback);

// app.get("/", (req, res, next) => {
//   res.send("Hello from express");
// });

app.listen(port, () => {
  console.log(`Server running at http://localhost:${port}`);
});
