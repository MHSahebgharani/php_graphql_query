# PHP GraphQL Query Builder
This code provides a simple utility class, graphql, that helps in building GraphQL queries dynamically. It allows you to construct complex GraphQL queries using an array-based syntax.

## Usage
To use this code, follow these steps:
1. Define your query structure as an associative array, $query.
2.Specify the desired fields and arguments within the $query array.
3.Call the buildGraphQLQuery method of the graphql class, passing the $query array as the parameter.
4.The method will return the generated GraphQL query as a string.

Here's an example of how to use the code:
```
// fields you want
$selects = ['id','name','lastname];
// user ids you want to get
$ids = [1,2,3]
$query = [
    'users' => [
        'fields' => $selects,
        'arguments' => [
            'ids' => $ids
        ]
    ]
];
$query = ['query' => graphql::buildGraphQLQuery($query)];
```
output:

```
query{
    users(ids = [1,2,3]){
        id
        name
        lastname
    }
}
```

## Code Explanation
The graphql class contains a static method, buildGraphQLQuery, that constructs the GraphQL query based on the provided $operations array. Here's an overview of how the code works:

1. Initialize an empty string variable, $query, to store the generated query.
2. Iterate over each operation within the $operations array.
3. Extract the fields and arguments for the current operation.
4. Build the operation query string by appending the operation name and its arguments (if any).
5. Iterate over the fields of the current operation and add them to the query string.
6. If a field has nested fields, include them within the corresponding braces.
7. Append the closing brace for the current operation.
8. Add the operation query string to the overall query string.
9. Return the final query string.

## Contributing

If you encounter any issues or have suggestions for improvements, feel free to open an issue or submit a pull request on GitHub. We appreciate your contributions!

## License

This package is open-source software licensed under the [MIT license](https://opensource.org/license/mit/).
