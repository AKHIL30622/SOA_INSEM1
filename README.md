# Order Validation App

A Spring Boot REST API lab project that validates customer order requests.

## Requirements
- Java 21
- Maven (or use the included Maven wrapper if you add one)
- Spring Boot 3.5.6

## Run
Open this folder in Spring Tool Suite / IntelliJ / VS Code as a Maven project, wait for Maven dependencies to download, then run `OrderAppApplication.java`.

Or from a terminal in this folder:
```bash
mvn spring-boot:run
```

## Endpoint
`POST http://localhost:8080/api/orders`

In Postman choose **Body → raw → JSON** and send:
```json
{
  "customerName": "Akhil",
  "customerEmail": "akhil@example.com",
  "productName": "Laptop",
  "quantity": 2,
  "price": 55000
}
```

Valid request: HTTP 200 OK.
Invalid or missing fields: HTTP 400 Bad Request due to `@Valid`.

Try invalid cases:
- `"customerName": "   "` → rejected by `@NotBlank`
- `"quantity": -2` → rejected by `@Positive`
- `"price": -500` → rejected by `@Positive`
- `"quantity": null` or omitted → rejected by `@NotNull`

Note: This lab example validates and returns the order; it does not persist it to a database.
