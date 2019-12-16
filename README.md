# JSON Command Line Tool Exercise

Using Ruby, create a command line tool for querying JSON structures. The tool should accept a URI that points to the location it can load the JSON data from (either an online source or a local file), and offer a way to query this data.


The tool should expect its input to be any array of uniform JSON objects, like the example below.
​
```
[
  {
    "id": 1,
    "name": "Leanne Graham",
    "username": "Bret",
    "email": "Sincere@april.biz",
    "address": {
      "street": "Kulas Light",
      "suite": "Apt. 556",
      "city": "Tokyo",
      "zipcode": "92998-3874",
      "geo": {
        "lat": "-37.3159",
        "lng": "81.1496"
      }
    },
    "phone": "1-770-736-8031"
  },
  {
    "id": 2,
    "name": "Ervin Howell",
    "username": "Antonette",
    "email": "Shanna@melissa.tv",
    "address": {
      "street": "Victor Plains",
      "suite": null,
      "city": "Tokyo",
      "zipcode": "90566-7771",
      "geo": {
        "lat": "-43.9509",
        "lng": "-34.4618"
      }
    },
    "phone": "010-692-6593"
  },
  {
    "id": 3,
    "name": "Clementine Bauch",
    "username": "Samantha",
    "email": "Nathan@yesenia.net",
    "address": {
      "street": "Douglas Extension",
      "suite": "Suite 847",
      "city": "Osaka",
      "zipcode": "59590-4157",
      "geo": {
        "lat": "-68.6102",
        "lng": "-47.0653"
      }
    },
    "phone": "1-463-123-4447"
  }
]
```
​
The tool should implement the following commands:
​
- A `help` command that outputs an explanation of the available commands and how to use them. The output for this command is static.
​
- A `query` command that allows the user to query the JSON data by keys and returns all matching JSON objects.
​

Here's a happy path use case example for using the tool:
​
```
jsonq --source https://jsonplaceholder.typicode.com/users
​
Data was loaded successfully!
​
> help
​
The following commands are available:
​
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Morbi scelerisque cursus scelerisque. Sed maximus magna ac mauris semper, in sodales nibh ultrices.
​
> query(id: 3)
​
[
  {
    "id": 3,
    "name": "Clementine Bauch",
    "username": "Samantha",
    "email": "Nathan@yesenia.net",
    "address": {
      "street": "Douglas Extension",
      "suite": "Suite 847",
      "city": "Osaka",
      "zipcode": "59590-4157",
      "geo": {
        "lat": "-68.6102",
        "lng": "-47.0653"
      }
    },
    "phone": "1-463-123-4447"
  }
]
​
> query(address: { city: "Tokyo" })
​
[
  {
    "id": 1,
    "name": "Leanne Graham",
    "username": "Bret",
    "email": "Sincere@april.biz",
    "address": {
      "street": "Kulas Light",
      "suite": "Apt. 556",
      "city": "Tokyo",
      "zipcode": "92998-3874",
      "geo": {
        "lat": "-37.3159",
        "lng": "81.1496"
      }
    },
    "phone": "1-770-736-8031"
  },
  {
    "id": 2,
    "name": "Ervin Howell",
    "username": "Antonette",
    "email": "Shanna@melissa.tv",
    "address": {
      "street": "Victor Plains",
      "suite": null,
      "city": "Tokyo",
      "zipcode": "90566-7771",
      "geo": {
        "lat": "-43.9509",
        "lng": "-34.4618"
      }
    },
    "phone": "010-692-6593"
  }
]
​
> query(name: "Leanne Graham", address: { city: "Tokyo" })
​
[
  {
    "id": 1,
    "name": "Leanne Graham",
    "username": "Bret",
    "email": "Sincere@april.biz",
    "address": {
      "street": "Kulas Light",
      "suite": "Apt. 556",
      "city": "Tokyo",
      "zipcode": "92998-3874",
      "geo": {
        "lat": "-37.3159",
        "lng": "81.1496"
      }
    },
    "phone": "1-770-736-8031"
  }
]
​
> query(id: 14)
​
[]
​
> query(name: "Leanne Graham", address: { city: "Sapporo" })
​
[]
```
​
Please provide unit tests that cover the most common success and error cases, using an appropriaty Ruby testing framework of your choice.
