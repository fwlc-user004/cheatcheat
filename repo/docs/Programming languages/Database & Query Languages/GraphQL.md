# 🚀 GraphQL Comprehensive Cheatsheet

## 🔹 Install & Setup
```sh
# Install GraphQL for Node.js
npm install graphql express-graphql

# Install Apollo Server (Optional, for GraphQL API)
npm install @apollo/server graphql
```

## 🔹 Basic GraphQL Query Structure
```graphql
type Query {
  hello: String
}
```

## 🔹 Creating a Simple GraphQL Server (Express + GraphQL)
```js
const express = require("express");
const { graphqlHTTP } = require("express-graphql");
const { buildSchema } = require("graphql");

const schema = buildSchema(`
  type Query {
    message: String
  }
`);

const root = {
  message: () => "Hello, GraphQL!"
};

const app = express();
app.use("/graphql", graphqlHTTP({
  schema,
  rootValue: root,
  graphiql: true
}));

app.listen(4000, () => console.log("GraphQL server running on port 4000"));
```

## 🔹 GraphQL Query Example
```graphql
query {
  message
}
```

## 🔹 Defining Types in GraphQL
```graphql
type User {
  id: ID!
  name: String!
  age: Int!
}

type Query {
  user(id: ID!): User
  users: [User]
}
```

## 🔹 Resolvers in GraphQL
```js
const users = [
  { id: "1", name: "Alice", age: 25 },
  { id: "2", name: "Bob", age: 30 }
];

const resolvers = {
  user: ({ id }) => users.find(user => user.id === id),
  users: () => users
};
```

## 🔹 Mutations in GraphQL
```graphql
type Mutation {
  createUser(name: String!, age: Int!): User
}
```

### Resolver for Mutation
```js
const resolvers = {
  createUser: ({ name, age }) => {
    const user = { id: String(users.length + 1), name, age };
    users.push(user);
    return user;
  }
};
```

### Example Mutation Request
```graphql
mutation {
  createUser(name: "Charlie", age: 35) {
    id
    name
  }
}
```

## 🔹 Apollo Server Example
```js
const { ApolloServer, gql } = require("@apollo/server");

const typeDefs = gql`
  type User {
    id: ID!
    name: String!
    age: Int!
  }
  type Query {
    users: [User]
  }
  type Mutation {
    addUser(name: String!, age: Int!): User
  }
`;

const resolvers = {
  Query: {
    users: () => users,
  },
  Mutation: {
    addUser: (_, { name, age }) => {
      const user = { id: users.length + 1, name, age };
      users.push(user);
      return user;
    },
  },
};

const server = new ApolloServer({ typeDefs, resolvers });
server.listen().then(({ url }) => console.log(`🚀 Server ready at ${url}`));
```

## 🔹 GraphQL Fragments
```graphql
fragment UserInfo on User {
  id
  name
  age
}

query {
  users {
    ...UserInfo
  }
}
```

## 🔹 GraphQL Directives
```graphql
query getUser($id: ID!) {
  user(id: $id) @skip(if: false) {
    name
  }
}
```

## 🔹 GraphQL Best Practices
- Use **fragments** to avoid repeated fields in queries.
- Optimize performance with **batch loading** using DataLoader.
- Implement **authentication & authorization** in resolvers.
- Use **pagination** for large data sets.
- Use **GraphQL subscriptions** for real-time updates.

---