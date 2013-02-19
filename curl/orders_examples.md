### Orders

#### Get a list of orders from the store

<pre>
    curl --request GET \
    -u "admin:key" \
    https://store/api/v2/orders.json
</pre>
By default, the api request returns only 50 orders. If you want to return all the orders from the store, you have to use filters. Look at the example below.

#### Get all orders from the store

Use the "limit" and "page" filter parameters to get a data beyond what the default query returns. Note that, per page, 200 orders is the max returned.

<pre>
     curl --request GET \
    -u "admin:key" \
    https://store/api/v2/orders.json?limit=200&page=1
</pre>



#### Update an order
Order takes many fields on the update requests. Refer to the documentation <a href="http://developer.bigcommerce.com/api/orders#put-ordersidjson">here</a>. Here, we update an order using just the mandatory fields.

<pre>
     curl --request PUT \
    -u "admin:key" \
    -H "Content-Type: application/json" \
    --data-binary '{"status_id":1}' \
    https://store/api/v2/orders/101
</pre>

#### Get orders created since a date
You can use the 'If-Modified-Since' header to request orders that have been created after a date.

<pre>
    curl -I --request GET \
    -u "admin:key" \
    -H "Content-Type: application/json" \
    -H "If-Modified-Since: Tue, 4 Dec 2012 00:00:00 GMT" \
    https://store/api/v2/orders.json
</pre>

#### Get coupons associated with an order
An order can contain coupons applied to it. This might provide discounts to the customer. You can look at all the available coupons in an order by -

<pre>
    curl --request GET \
    -u "admin:key"\
    https://store-bwvr466.mybigcommerce.com/api/v2/orders/115/coupons.json
</pre>

#### Create a shipment for an order
One can create a shipment for an order via the orders/shipment endpoint. As an example, third-party shipping services can query orders from a store when they are created and create shipments for those.

<pre>
    curl --request POST \
    -u "admin:key" \
    -H "Content-Type: application/json" \
    -d '{"order_address_id":15,"tracking_number":"123-123-123","items":[{"order_product_id":15,"quantity":1}]}' \
    https://store/api/v2/orders/114/shipments.json
</pre>




