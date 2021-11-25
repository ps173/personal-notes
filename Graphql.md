# Understanding Graphql

GraphQL is a query language for your API, and **a server-side runtime** for executing queries using a **type system you define for your data**. GraphQL isn't tied to any **specific database or storage engine** and is instead backed by your existing code and data.

At its core, GraphQL enables declarative data fetching where a client can specify exactly what data it needs from an API. Instead of multiple endpoints that return fixed data structures, a GraphQL server only exposes a single endpoint and responds with precisely the data a client asked for.

GraphQL is often confused with being a database technology. This is a misconception, GraphQL is a query language for APIs - not databases. In that sense it’s database agnostic and effectively can be used in any context where an API is used.


query to get pinned repos from github
run at [github explorer](https://docs.github.com/en/graphql/overview/explorer)

```graphql

query {
    user(login:"ps173") {
        pinnedItems(first: 5, types: [REPOSITORY, GIST]) {
            totalCount
            edges {
                node {
                    ... on Repository {
                    name
                    }
                }
            }
        }
    }
}


```


## Resources for learning-graphql
- [Graphql Faqs](https://graphql.org/faq/)
- [Introduction](https://graphql.org/learn/)
- [How to graphql](https://www.howtographql.com/basics/0-introduction/)
- [Communities](https://graphql.org/community/)
- [Specifications Document](https://spec.graphql.org/June2018/)
