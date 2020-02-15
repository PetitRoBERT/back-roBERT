# Mongo DataBase :leaves:

## 1. Why using MongoDB ? :thinking: 

Reasons why we choosed MongoDB: :woman_teacher: 
* Documents database: the data structure is close to the objects we need in the code.
* Polymorphic Schema: Mongo makes it easy to update schema without doing any migration scripts.
* If the project grows well, mongoDB have great reading performances (we do not need writing to be lighting fast).
* Great community.

## 2. Schema definition

### 2.1 **Authors** collection :writing_hand: 


```js
{
  _id: MONGOID,
  firstName: String,
  lastName: String,
  birth: Date,
  death: Date,
  nationality: String,
  biography: Text,
  movements: [movementsMongoIds],
  works: [worksMongoIds]
}
```

### 2.2 **Works** collection :book:

```js
{
  _id: MONGOID,
  authorId: MONGOID,
  title: String,
  parutionDate: Date,
  language: String,
  publisher: String,
  rawFormat: String, // epub, mobi, csv 
  type: String,      // poem, historical story, novel..
  extracted: {},     // ML stuff extracted
  content: Text
}
```

### 2.3 **Movements** collection :star2:

```js
{
  _id: MONGOID,
  name: String,
  dateStart: Date,
  dateEnd: Date,
  authorsIds: [authorsMongoIds]
}
```

## 3. Setup

* Install docker

* **Get lastest Mongo docker Image**
```sh
docker pull mongo
```

* Run image inside docker container to start your `mongodb-petitrobert` instance
```sh
docker run -d -p 27017-27019:27017-27019 --name mongodb-petitrobert mongo
```

* Connect to your container terminal:
```sh
docker exec -it mongodb bash
```

* Launch the mongo shell client:
```sh
mongo
```

* Check running containers:
```sh
docker ps
```

* Stop container
```sh
docker container rm --force <container-name>
```

* Container logs
```sh
docker logs <container-name>
```