# Hasura

> The Hasura GraphQL Engine is an extremely lightweight, high performance product that gives you instant realtime GraphQL APIs on a Postgres database. This can be used to quickly build new applications on Postgres or fast-track the move to GraphQL for existing applications on Postgres.

## Example
[Hasura Crash Course by Laith Academy][1]

### Mutation Insert 
```
mutation{
  insert_posts(objects:{
    content:"This is my mutation posts",
    title: "My mutation",
    user_id: 1
  }){
    returning{
      title
      user {
        username
      }
    }
  }
}

```

### Mutation Update

```
mutation{
  update_users_by_pk(pk_columns:{id:1}, _set: {
    age: 99
  }){
    id
    username
  }
}
```

### Mutation Delete

```
mutation{
  delete_users_by_pk(id: 5){
    id
    username
  }
}
```

### Select All

```
query{
  users{
    id
    username
  }
}
```

### Select and Where clase

```
query{
  users(where: {gender:{_eq: false}}) {
    id
    username
  }
}
```


### Search by primary key
```
query{
  users_by_pk(id: 1){
    username
    posts{
      title
      content
      id
    },
    comments{
      content
      id
    }
  }
}
```


```
{
  posts_by_pk(id: 1){
    title
    content
    comments(order_by: {id: desc}){
      id
      content
      user{
        username
      }
    }
  }
}
```

[1]:https://www.youtube.com/watch?v=BNo0WROmij8 

 ----- 
 HackMD Note URL: https://hackmd.io/Wux1wxsPRe2nAWa78tf93g