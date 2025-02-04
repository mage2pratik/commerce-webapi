---
title: deleteCompanyRole mutation
contributor_name: Atwix
contributor_link: https://www.atwix.com/
edition: b2b
---

# deleteCompanyRole mutation

Use the `deleteCompanyRole` mutation to delete a company role by ID.

You can get the role ID with the [`company`](../queries/company.md) query.

## Syntax

```graphql
mutation {
    deleteCompanyRole(
        id: ID!
    ) {
        DeleteCompanyRoleOutput
    }
}
```

## Example usage

The following example deletes the specified company role.

**Request:**

```graphql
mutation {
  deleteCompanyRole(
    id: "Mg=="
  ) {
    success
  }
}
```

**Response:**

```json
{
  "data": {
    "deleteCompanyRole": {
      "success": true
    }
  }
}
```

## Input attributes

The `deleteCompanyRole` mutation requires the following input:

Attribute |  Data Type | Description
--- | --- | ---
`id` | ID! | The encoded role ID to delete

## Output attributes

The `deleteCompanyRole` mutation returns a Boolean value that indicates whether the operation was successful.

Attribute |  Data Type | Description
--- | --- | ---
`success` | Boolean | Indicates whether the company role has been deleted successfully (`true` or `false`)
