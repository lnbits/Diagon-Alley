# Diagon Alley: Decentralised Market-Stall Protocol
Diagon Alley is a decentralised market-stall protocol, that shifts emphasis from the frontend market to the merchants stall.
Best served over TOR!

## Indexers
An indexer is a simple frontend that routes product, payment and shipping information between merchant and seller. Each merchant has products in a "stall". The stall chooses what products to list with the indexer. An indexer has one endpoint.  

* `/register/<indexer-ID>` **GET** The `<indexer-ID>` is gennerated by the stall. the endpoint is for stalls to fetch rating data (0-100%), register products and check the indexer is online. 

  Returns 200 OKAY (application/json)<br/>
  ```{"shopstatus": <boolean>, "rating": <int>}```

## Stalls
A stall can choose to list some/all products with an "indexer". A stall is a small server that has three endpoints.

* `/products/<indexer-ID>` **GET** for fetching all products associated with an indexer ID
  
  Returns 200 OKAY (application/json)<br/>
  ```[{"product-id":<string>, "product-name":<string>, "categories":<list>, "description":<string>,  "image":<string>, "price":<int>, "quantity":<int>}, {"product-id":<string>, "product-name":<string>, "categories":<list>, "description":<string>,  "image":<string>, "price":<int>, "quantity":<int>}]```


* `/order/<indexer-ID>` **POST** for placing an order and sending shipping data, returns a lightning-network invoice and checking/order ID

  Body (application/json)<br/>
  ```{"product-id": <string>, "address": <string>, "shippingzone": <integer>, "email": <string>, "quantity": <integer>}```
  
  Returns 201 CREATED (application/json)<br/>
  ```{"payment_request": <string>, "checking_id": <string>}```
  
* `/checkshipped/<checking_id>` **GET** for checking if an order has been shipped

  Returns 200 OKAY (application/json)<br/>
  ```{"shipped": <boolean>}```



