### Products

#### Get a list of products from the store

<pre>
    curl --request GET \
    -u "admin:key" \
    https://store/api/v2/products.json
</pre>
By default, the API request returns only 50 products. If you want to return all the products from the store, you have to use filters. Look at the example below.

#### Get all products from the store

Use the "limit" and "page" filter parameters to get a data beyond what the default query returns. Note that, per page, 200 products is the max returned.

<pre>
    curl --request GET \
    -u "admin:key" \
    https://store/api/v2/products.json?limit=200&page=1
</pre>

#### Create a product

Products have many fields. You can check out <a href="http://developer.bigcommerce.com/api/products#post-productsjson">this docs page</a> for information on the product fields allowed as part of a POST request.

Let us say, we want to create a product using just the mandatory fields needed for a POST request. Note that price needs to specified as a string, while the weight is a decimal. Note that if the is_visible flag, though not mandatory is not set to true, the product by default would not be visible -

<pre>
    curl --request POST \
    -H "Content-Type: application/json" \
    -u "username:apikey" \
    -d '{"name":"startrek","price":19.99,"categories":[2],"type":"physical","availability":"available", "weight":0}' \
    https://store/api/v2/products.json
</pre>

#### Update a product
If we want to update the product created above, we would do it as -

<pre>
    curl --request PUT \
    -H "Content-Type: application/json" \
    -u "username:apikey" \
    -d '{"name":"startrek","sku":"STREK-DVD","categories":[2,3],"inventory_tracking":"simple","inventory_level":"500", "inventory_warning":100}' \
    https://store/api/v2/products/id.json
</pre>


#### Search a product by SKU
If we want to search by a product SKU, we can use the following code. Remember that when a product has optionset/variations defined, and if the individual options have SKUs defined, then the product SKU is overriden by the option SKUs. Currently, there are two ways to search for SKUs - GET /products?sku="something" or GET /products/skus?sku="something". The first call only returns product level SKU and not option level SKUs. 

<pre>
    curl --request GET \
    -u "admin:key" \
    https://store/api/v2/products/skus.json?sku="abcd"
</pre>


