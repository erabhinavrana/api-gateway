
# api-gateway

This is an Spring Cloud Api Gateway for the online bookstore application. It provide a simple, yet effective way to route to APIs and provide cross cutting concerns to them such as: security, monitoring/metrics, and resiliency.

## API Reference

#### Get List of Books

```http
  GET /BOOKSTORE-SERVICE/api/v1/books
```

#### listAllBooks()

It returns all the available books.

#### Sample JSON Response

```
[
    {
        "id": 1,
        "name": "War and Peace",
        "description": "About War and Peace",
        "author": "Tolstoy, Leo",
        "type": "HISTORIC",
        "price": 12.7,
        "isbn": "dbb68e1d-69c8-413a-a4cc-80e791001d12"
    },
    {
        "id": 2,
        "name": "Northanger Abbey",
        "description": "About Penguin",
        "author": "Austen, Jane",
        "type": "FICTION",
        "price": 18.2,
        "isbn": "1009496e-610b-4e31-9e80-6a50659e57dc"
    }
]
```

#### Get Book

```http
  GET /BOOKSTORE-SERVICE/api/v1/books/${id}
```

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `id`      | `Long` | **Required**. id of Book to fetch |

#### listBookById(id)

Takes book id and returns the available book Details.

#### Sample JSON Response

```
{
    "id": 1,
    "name": "War and Peace",
    "description": "About War and Peace",
    "author": "Tolstoy, Leo",
    "type": "HISTORIC",
    "price": 12.7,
    "isbn": "dbb68e1d-69c8-413a-a4cc-80e791001d12"
}
```

#### Add Book

```http
  POST /BOOKSTORE-SERVICE/api/v1/books
```

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `book`      | `Book` | **Required**. data to create a Book record|

#### addBook(book)

Takes book data and returns the created Book Details.

#### Sample JSON Request

```
{
    "name": "War and Peace",
    "description": "About War and Peace",
    "author": "Tolstoy, Leo",
    "type": "HISTORIC",
    "price": 12.7
}
```

#### Sample JSON Response

```
{
    "id": 1,
    "name": "War and Peace",
    "description": "About War and Peace",
    "author": "Tolstoy, Leo",
    "type": "HISTORIC",
    "price": 12.7,
    "isbn": "dbb68e1d-69c8-413a-a4cc-80e791001d12"
}
```

#### Update Book

```http
  PUT /BOOKSTORE-SERVICE/api/v1/books
```

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `book`      | `Book` | **Required**. data to create a Book record|

#### updateBook(book)

Takes book data and returns the updated Book Details.

#### Sample JSON Request

```
{
    "id": 1,
    "name": "War and Peace",
    "description": "About War and Peace",
    "author": "Tolstoy, Leo",
    "type": "HISTORIC",
    "price": 12.7,
    "isbn": "dbb68e1d-69c8-413a-a4cc-80e791001d12"
}
```

#### Sample JSON Response

```
{
    "id": 1,
    "name": "War and Peace",
    "description": "About War and Peace",
    "author": "Tolstoy, Leo",
    "type": "HISTORIC",
    "price": 12.7,
    "isbn": "dbb68e1d-69c8-413a-a4cc-80e791001d12"
}
```

#### Delete Book

```http
  DELETE /BOOKSTORE-SERVICE/api/v1/books/${id}
```

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `id`      | `Long` | **Required**. id of Book to delete a book record|

#### removeBook(id)

Takes book id and remove the Book Details.

#### Checkout Books

```http
  POST /BOOKSTORE-SERVICE/api/v1/checkout
```

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `request`      | `CheckoutRequest` | **Required**. books data to checkout the books and provide total amount|

#### checkout(request)

Takes checkout request data and returns the calculated final amount as checkout response.

#### Sample JSON Request

```
{
    "books": [
        {
            "id": 1,
            "name": "War and Peace",
            "description": "About War and Peace",
            "author": "Tolstoy, Leo",
            "type": "HISTORIC",
            "price": 12.7,
            "isbn": "dbb68e1d-69c8-413a-a4cc-80e791001d12"
        },
        {
            "id": 2,
            "name": "Northanger Abbey",
            "description": "About Penguin",
            "author": "Austen, Jane",
            "type": "FICTION",
            "price": 18.2,
            "isbn": "1009496e-610b-4e31-9e80-6a50659e57dc"
        }
    ],
    "promoCode": "FICTION10"
}
```

#### Sample JSON Response

```
{
    "totalAmount": 29.08
}
```
#### Get Promo Details

```http
  GET /PROMO-SERVICE/api/v1/promos/${code}
```

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `code`      | `string` | **Required**. promoCode of Promo to fetch |

#### getPromoDetails(code)

Takes promo code and returns the available Promo Details.

#### Sample JSON Response for Promo Service

```
{
    "id": 111,
    "promoCode": "FICTION10",
    "promoType": "FICTION",
    "promoValue": 10.0,
    "maxDiscount": 100.0,
    "expiry": "2022-04-01T20:00:00.000+00:00"
}
```

## Run Locally

Clone the project

```bash
  git clone https://github.com/erabhinavrana/api-gateway
```

Go to the project directory

```bash
  cd api-gateway
```

Start the server

```bash
  ./mvnw spring-boot:run
```


## Appendix

Docker Image: abhinavrana/bsv1-api-gateway:0.0.1-SNAPSHOT

