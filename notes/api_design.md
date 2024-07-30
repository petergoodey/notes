# API Design and Management

## Designing APIs

APIs should be RESTFul and Stateless

### Use Nouns

```cmd
/users: A collection of users
/users/username1: A resource about a collection of users.
```

### Idempotency

Idempotency essentially means that the effect of a successfully performed request on a server resource is independent of the number of times it is executed.

### Use HTTP Method Verbs Correctly

* GET
  * Get a resource and sub-resources.
  * Idempotent.
* POST
  * Create a new resource and sub-resources.
  * Not idempotent.
* PUT
  * Update existing resource state
  * Idempotent
* PATCH
  * Used to make partial updates to an existing resources
  * Not idempotent
* DELETE
  * Used to delete existing resources
  * Idempotent

### Identifiers

#### Generation

* Auto-generation
  * Can happen at the DB level
    * Issues
      * Synchronous
  * Consider generating at an API level
    * Advantages:
      * Asynchonous

#### Meaningful identifiers

* Add information
  * Consider adding meaningful information
    * E.g. WEB-\<GUID\> or API-\<GUID\>

### Add Actions That Can Be Performed Dependent on Resource State

The API will know what actions can be performed based on the resource state. So we can return this with the response:

```json
{
  "order": {
    "orderID" : "WEB-5354b169-933e-49b6-976e-3a5714543879",
    "timePlaced" : "2024-07-02T17:25:55Z",
    "status" : "pending",
    "customer" : {
      "customerID": "1307a5e1-cc61-4e2c-86fa-b1f6cf391fd7"
    },
    "actions": [{
      "name": "CancelOrder",
      "uri": "https://my.app/orders/WEB-5354b169-933e-49b6-976e-3a5714543879/cancel",
      "method": "PUT"
      }
    ]
  }
}
```

If ``CancelOrder`` exists in the response then the client knows that the order is cancellable.

Now routes can change over time aslong as the ``CancelOrder`` key is present we can change the route.

### Don't Handcuff Yourself in You Response

Allow room to make changes that are backward compatible.

```json
{
  "statuses": {
    "pending",
    "cancelled",
    "shipped"
  },
  "orders": [
    {
      "orderID" : "WEB-5354b169-933e-49b6-976e-3a5714543879",
      "timePlaced" : "2024-07-02T17:25:55Z",
      "total" : 320.22,
      "status" : "pending"
    },
    {
      "orderID" : "API-14419e74-eb2e-4e41-806a-83e0a88ba78b",
      "timePlaced" : "2024-08-30T02:32:00Z",
      "total" : 21.22,
      "status" : "cancelled"      
    }
  ]
}
```

#### Use domain Language Where Possible

See cancel order above. It's obvious what this action is to non techies.

