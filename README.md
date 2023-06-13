# GraphQL-Restaurant-Data
# GraphQL Restaurant API

This is a simple GraphQL API for managing restaurants and their dishes. It allows you to perform CRUD operations (Create, Read, Update, Delete) on restaurants.

## Prerequisites

- Node.js and npm installed on your machine

## Getting Started

1. Clone the repository or download the code.
2. Install the dependencies by running the following command:

   ```shell
   npm install
   ```

3. Start the GraphQL server by running the following command:

   ```shell
   node server.js
   ```

4. The GraphQL server will start running on `http://localhost:5500/graphql`.

## API Endpoints

The following API endpoints are available:

- `GET /graphql` - GraphQL API endpoint for executing queries and mutations.

## GraphQL Schema

The GraphQL schema defines the available types and operations supported by the API. Here is an overview of the schema used in this API:

```graphql
type Query {
  restaurant(id: Int): restaurant
  restaurants: [restaurant]
}

type restaurant {
  id: Int
  name: String
  description: String
  dishes: [Dish]
}

type Dish {
  name: String
  price: Int
}

input restaurantInput {
  name: String
  description: String
}

type DeleteResponse {
  ok: Boolean!
}

type Mutation {
  setrestaurant(input: restaurantInput): restaurant
  deleterestaurant(id: Int!): DeleteResponse
  editrestaurant(id: Int!, name: String!): restaurant
}
```

## Query Examples

You can use the following queries and mutations to interact with the API:

### Get a restaurant by ID

```graphql
query {
  restaurant(id: 1) {
    id
    name
    description
    dishes {
      name
      price
    }
  }
}
```

### Get all restaurants

```graphql
query {
  restaurants {
    id
    name
    description
    dishes {
      name
      price
    }
  }
}
```

### Create a new restaurant

```graphql
mutation {
  setrestaurant(input: { name: "New Restaurant", description: "A new restaurant" }) {
    id
    name
    description
  }
}
```

### Delete a restaurant

```graphql
mutation {
  deleterestaurant(id: 1) {
    ok
  }
}
```

### Update a restaurant

```graphql
mutation {
  editrestaurant(id: 1, name: "Updated Restaurant") {
    id
    name
    description
  }
}
```

## Credits

This code was developed by Ruben Gallardo Jr.
