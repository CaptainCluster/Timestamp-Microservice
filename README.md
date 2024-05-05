# Timestamp Microservice

![Express.js](https://img.shields.io/badge/express.js-%23404d59.svg?style=for-the-badge&logo=express&logoColor=%2361DAFB)

Timestamp Microservice is a simple **ExpressJS** project for the FreeCodeCamp course **Back End Development and APIs**. The user gives a date as a parameter in a request and receives a JSON file with the date in **unix** and **utc** formats. 

🙏 Credits
---
![FreeCodeCamp](https://img.shields.io/badge/Freecodecamp-%23123.svg?&style=for-the-badge&logo=freecodecamp&logoColor=green)

Everything not written by me has been cloned from [this GitHub repository](https://github.com/freeCodeCamp/boilerplate-project-timestamp/).

Here is the solution I wrote for this project:
```
app.get("/api/:date", function(req, res)
{
  let date = req.params.date;
  //Unix type can be recognized as' a number
  if(!isNaN(Number(date)))
  {
    return res.json({
      unix: Number(date),
      utc: new Date(Number(date)).toUTCString()
    });
  }

  // If the date is not in numeric form, it is expected to be of
  // type string. Checking whether it is valid or not...
  if(new Date(date).toUTCString() == "Invalid Date")
  {
    return res.json({
      error: "Invalid Date"
    });
  }

  // A valid string date will be handled now, as an invalid one
  // would have triggered a return command.
  return res.json({
    unix: new Date(date).getTime(),
    utc: new Date(date).toUTCString()
  });

});
```
