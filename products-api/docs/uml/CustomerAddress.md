# Customer and Address — UML Class Diagram

![Customer and Address class diagram](CustomerAddress.png)

```mermaid
classDiagram
    direction LR
    class Customer {
        -id : Long
        -name : String
        -email : String
        -address : Address
        -tags : String[]
        -customerCount : int$
        +Customer()
        +Customer(id : Long, name : String, email : String, address : Address)
        +getId() Long
        +getName() String
        +getEmail() String
        +getAddress() Address
        +getTags() String[]
        +setTags(tags : String[]) void
        +getCustomerCount()$ int
    }
    class Address {
        -street : String
        -city : String
        -postcode : String
        +Address()
        +Address(street : String, city : String, postcode : String)
        +getStreet() String
        +getCity() String
        +getPostcode() String
    }
    Customer --> Address
```

The solid line with an open arrowhead is an **association**: a Customer *has an* Address.
The arrow points at Address because Customer holds a reference to Address, not the other way round.

Underlined members (`customerCount`, `getCustomerCount()`) are **static**: one shared copy for the class, not one per object.
