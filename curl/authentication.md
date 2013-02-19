### Connecting with a store

Currently, Bigcommerce stores can be connected via basic auth. 
<pre>
    curl --request GET \
    -H "Authorization: Basic key" \
    https://store/api/v2/orders.json
</pre>

The api key is obtained from a store. As admin, you can either use your admin API credentials (which you can enable under user settings) or create a user account and use the generated API key. If the request is made using Authorization header, you need to generate the key by encoding admin:key as base64. Or a simple way to do the same thing as above is -

<pre>
    curl --request GET \
    -u "admin:key" \
    https://store/api/v2/orders.json
</pre>

