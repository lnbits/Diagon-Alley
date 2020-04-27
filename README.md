# Diagon Alley: Decentralised Market-Stall Protocol
Diagon Alley is a decentralised market-stall protocol, that shifts emphasis on the frontend market to the merchants backend.

## Indexers
An indexer is a simple frontend middle-man that routes product, payment and shipping information between merchant and seller. Each merchant has products in a "stall" they allow an indexer to list.

## Stalls
A stall can choose to list some/all products with an "indexer". A stall is a small server that has three endpoints.

* /products/<indexer-ID> GET for fetching all products associated with an indexer ID
  
  Returns 201 CREATED (application/json)
  Product JSON list

* /order/<indexer-ID> POST for placing an order and sending shipping data, returns a lightning-network invoice and checking(order) ID)

  Body (application/json)
  {"id": <string>, "address": <string>, "shippingzone": <integer>, "email": <string>, "quantity": <integer>}
  Returns 201 CREATED (application/json)
  {"checking_id": <string>,"payment_request": <string>}



