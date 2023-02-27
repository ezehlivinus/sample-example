# sample-example

## Installation
- clone the repository
- install the dependencies: using `npm install`
- create a new file named `.env` in root folder of the project.
- Copy and paste the content of `.env.example` into `.env` and filling the value.
- You are advice to use atlas for the `DATABASE_URL` key but local database url is fine
- start the server in development by running: `npm run dev` and read the terminal output to make sure that the server is running and the database is connected properly

## For you
- Some endpoint (routes) and it's controllers and services has been created
- Some was declared and was commented out, ...their controllers and services has NOT been implemented yet. You can try and finish it off.
- Documentation: document the API using postman for your frontend devs to use it. Or you can just use markdown file.

## Documentation
- Room resource (or base endpoint): `localhost:3000/api/v1/rooms`
- RoomType resource: `localhost:3000/api/v1/room-types`
- NB: Your port above may differ from this port

### Sample requests and responses
Note that `status code` and other `headers` information including request and response headers inforation were omitted, you can add these to yours. Example of other headers: `Authorization`, `access-token`, `x-auth-token` etc.

- creating a new room type
- endpoint: `localhost:3000/api/v1/room-types`
- method: `POST`
Sample request
```json
{
  "codeName": "bronze"
}
```

Sample response
```json
{
  "success": true,
  "message": "created room type",
  "data": {
    "codeName": "bronze",
    "_id": "63e730b65b1b9246ae78b330",
    "createdAt": "2023-02-11T06:07:50.995Z",
    "updatedAt": "2023-02-11T06:07:50.995Z"
  }
}
```

#### creating a new room
- endpoint: `localhost:3000/api/v1/rooms`
- method: `POST`

Sample request
```json
{
  "roomType": "63e6c0767734b38b983d5aeb",
  "price": 200,
  "name": "uba-unn"
}
```
// sample response
```json
{
  "success": true,
  "message": "Room created successfully",
  "data": {
    "name": "unn-unn",
    "price": 200,
    "size": "small",
    "roomType": "63e6c05b7734b38b983d5ae7",
    "_id": "63e6c5fc453e89b329bdfb2c",
    "createdAt": "2023-02-10T22:32:28.502Z",
    "updatedAt": "2023-02-10T22:32:28.502Z",
    "__v": 0
  }
}
```

#### making a search
- endpoint: `localhost:3000/api/v1/rooms?search=uba`
- Method: `GET`

sample response
```json
{
  "success": true,
  "message": "Rooms search successfully",
  "data": [
    {
      "_id": "63e6c622453e89b329bdfb2f",
      "name": "uba-unn",
      "price": 200,
      "size": "small",
      "roomType": {
        "_id": "63e6c0767734b38b983d5aeb",
        "codeName": "silver",
        "createdAt": "2023-02-10T22:08:54.738Z",
        "updatedAt": "2023-02-10T22:08:54.738Z",
        "__v": 0
      },
      "createdAt": "2023-02-10T22:33:06.574Z",
      "updatedAt": "2023-02-10T22:33:06.574Z",
      "__v": 0
    }
  ]
}
```

#### Filtering by rooms' name
- Endpoint: `localhost:3000/api/v1/rooms?name=uba-unn`
- Method: `GET`

Server response sample
```json
{
  "success": true,
  "message": "Room found successfully",
  "data": [
    {
      "_id": "63e6c622453e89b329bdfb2f",
      "name": "uba-unn",
      "price": 200,
      "size": "small",
      "roomType": {
        "_id": "63e6c0767734b38b983d5aeb",
        "codeName": "silver"
      },
      "createdAt": "2023-02-10T22:33:06.574Z",
      "updatedAt": "2023-02-10T22:33:06.574Z",
      "__v": 0
    }
  ]
}
```

