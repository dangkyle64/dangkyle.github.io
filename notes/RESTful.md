REST is resource-based, meaning that each of the endpoints is mapped in a structure that reflects the resources in the system. An example can be `/books` mapping to the books inside of the system. Using HTTP methods like GET, I can get all the resources inside of the `/books`.

```bash
Resource-Based Endpoints

/books  -> All books
/books/1 -> Book with ID 1
/authors -> All authors
/authors/100/books -> Books by author ID 100
```

RESTful has standardized HTTP methods, making it easier to map what CRUD action does what in comparison to the endpoint. 

```bash
GET -> /books -> Read all books
GET -> /books/1 -> Read book with ID 1
POST -> /books -> Create a book
PUT -> /books/1 -> Update book with ID 1
PATCH -> /books/1 -> Partially update book with ID 1
DELETE -> /books/1 -> Delete book with ID 1
```

PUT VERSUS PATCH - will be written later

RESTful is stateless, meaning that all the resources are sent with every request leading to several benefits.
- The server never has to store anything
- Due to not needing to store anything, it is easier to extend horiztonally
- Does not have to manage sessions 
- Since everything is sent, it has two benefits in particular
- easier to maintain and debug because each request is self contained. Almost l ike a module in code, where unit testing modules is easier if they're defined in their own modules
- Reliability since everything is sent, even if server crashes it can just send to another server. This is almost like the ACID method in databases where even if a request crashes, its all or nothing. If it fails, it goes into another server.
- Cacheability is easier because server isnt storing anything hidden that  might influence the final output

weaknesses of stateless
every request MUST include all the information, so the size of each request may be huge. This would add a network overhead. If compared to a stateful session where less bytes can be sent every single time.

requires sending authentication/authorizoation credentials on every request which poses security risk. JWT, API keys sent repeatedly over network which can be intercepted if  HTTPS not enforced. Need to manage token expiry, revocation, and permissions

if server doesnt remember anything, need to recompute or revalidate data, ex. validate token on every request or looking up user pref every time.

difficult to use in multi-step transcation like shopping cart or multistep form. Must send context in all actions or  storing pa rtial data or client in temp database?

```md
Stateless Example

GET /books/1
Headers:
Authorization: Bearer <token>

Response:
{
    "id": 1,
    "title": My Wandering Spirit Lady,
    "author: "Qing Jun Mo Xiao"
}
```
client-server separation

The reason why this matters is almost like modules in general. We want them to be separated in a way so I can change anything either from the client or server side and the other side can't break. This can be scaled even easier as it can be swapped, replicated, or moved to cloud without touching the client side. Security benefits because everything can be hidden in the backend and secured and the client side  won't see as much.
