# Serverless and Amplify

## [Serverless Architecture](https://hackernoon.com/what-is-serverless-architecture-what-are-its-pros-and-cons-cc4b804022e9)

New insights: serverless - in my current understanding - is that any data/database/tables you have, that data is transported between different stateless, ephemeral lambda functions in order for it to be molded into the desired form (state?) as desired by the developer. Definitely a different way to think about it, and for some purposes the likely route to take, but the benefits need to be weighed against the loss of control and "nearness" to the data, it being in the cloud and all.



## [AWS Amplify Kool-Aid](https://aws.amazon.com/amplify/)
- AWS Amplify is still the awesome-est! oooooYEAH!!! 
- Importantly, it is a gateway to documentation. Extensive, sometimes not updated, documentation.

## [GraphQL @connection - Adding Relationships Between Types](https://docs.amplify.aws/cli/graphql-transformer/connection)
``` Java
directive @connection(keyName: String, fields: [String!]) on FIELD_DEFINITION
```
will work to specify the relationships between ```@model``` types.

### One-to-one
``` Java
type Project @model {
  id: ID!
  name: String
  team: Team @connection
}

type Team @model {
  id: ID!
  name: String!
}
```

## Has Many
``` Java
type Post @model {
  id: ID!
  title: String!
  comments: [Comment] @connection(keyName: "byPost", fields: ["id"])
}

type Comment @model
  @key(name: "byPost", fields: ["postID", "content"]) {
  id: ID!
  postID: ID!
  content: String!
}
```
Note: a one-to-many connection needs an ```@key``` to allow proper querying.
And to enable bi-directional connection:
``` Java
type Post @model {
  id: ID!
  title: String!
  comments: [Comment] @connection(keyName: "byPost", fields: ["id"])
}

type Comment @model
  @key(name: "byPost", fields: ["postID", "content"]) {
  id: ID!
  postID: ID!
  content: String!
  post: Post @connection(fields: ["postID"])
}
```

## Many-to-Many
``` Java
type Post @model {
  id: ID!
  title: String!
  editors: [PostEditor] @connection(keyName: "byPost", fields: ["id"])
}

# Create a join model and disable queries as you don't need them
# and can query through Post.editors and User.posts
type PostEditor
  @model(queries: null)
  @key(name: "byPost", fields: ["postID", "editorID"])
  @key(name: "byEditor", fields: ["editorID", "postID"]) {
  id: ID!
  postID: ID!
  editorID: ID!
  post: Post! @connection(fields: ["postID"])
  editor: User! @connection(fields: ["editorID"])
}

type User @model {
  id: ID!
  username: String!
  posts: [PostEditor] @connection(keyName: "byEditor", fields: ["id"])
}
```
Many-to-many requiresa two 1-M @connections, an @key, and a joining @model. It is bi-directional to begin with hence the two 1-M @connections by default.

> Note: After you have pushed a @connection directive you should not try to change it. If you try to change it, the DynamoDB UpdateTable operation will fail. Should you need to change a @connection, you should add a new @connection that implements the new access pattern, update your application to use the new @connection, and then delete the old @connection when it’s no longer needed.
