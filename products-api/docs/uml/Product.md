# Product, ProductService and ProductController — UML Class Diagram (Tutorial 3)

![Product, ProductService and ProductController class diagram](Product.png)

PlantUML source: [Product.puml](Product.puml)

```mermaid
classDiagram
    direction LR
    class ProductController {
        -productService : ProductService
        +getAllProducts() List~Product~
        +getProductById(id : Long) Product
        +addProduct(product : Product) Product
        +search(name : String) List~Product~
        +cheaperThan(price : double) List~Product~
        +deleteProduct(id : Long) void
    }
    class ProductService {
        -products : List~Product~
        -nextId : Long
        +getAllProducts() List~Product~
        +getProductById(id : Long) Optional~Product~
        +addProduct(product : Product) Product
        +deleteProduct(id : Long) void
        +findByName(name : String) List~Product~
        +findCheaperThan(price : double) List~Product~
    }
    class Product {
        -id : Long
        -name : String
        -price : double
        +Product()
        +Product(id : Long, name : String, price : double)
        +getId() Long
        +getName() String
        +getPrice() double
        +setId(id : Long) void
        +setName(name : String) void
        +setPrice(price : double) void
    }
    ProductController ..> ProductService
    ProductService --> Product
```

- **Dashed arrow (`..>`) = dependency.** ProductController *uses* ProductService to do its work.
- **Solid arrow (`-->`) = association.** ProductService *holds* Products in its list.
- **Nothing points back at the controller.** The service and Product know nothing about HTTP.
