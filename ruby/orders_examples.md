### Orders

#### Get a list of orders from the store

<pre>
    require 'bigcommerce'
    api = Bigcommerce::Api.new({
      :store_url => 'https://store-xxxx.mybigcommerce.com',
      :username  => 'admin',
      :api_key   => 'key'
    })
    orders = api.get_orders
    
</pre>
By default, the get_orders request returns only 50 orders. If you want to return all the orders from the store, you have to use filters. Look at the example below.

#### Get all orders from the store

Use the "limit" and "page" filter parameters to get a data beyond what the default query returns. Note that, per page, 200 orders is the max returned.

<pre>
    require 'bigcommerce'
    api = Bigcommerce::Api.new({
      :store_url => 'https://store-xxxx.mybigcommerce.com',
      :username  => 'admin',
      :api_key   => 'key'
    })
    orders = api.get_orders
</pre>

In cases, when you have more than 200 orders in your store, you can use a counter to update the page, while controlling the limit parameter. You can do something like below.

<pre>
    require 'bigcommerce'
    api = Bigcommerce::Api.new({
      :store_url => 'https://store-xxxx.mybigcommerce.com',
      :username  => 'admin',
      :api_key   => 'key'
    })
    count = api.get_orders_count/200 + 1
    orders = []
    count.times do |i|
        orders << api.get_orders({:page => i, :limit => 200})
    end
    
</pre>

#### Update an order
Order takes many fields on the update requests. Refer to the documentation at http://developer.bigcommerce.com/api/orders#put-ordersidjson. Here, we update an order using just the mandatory fields.

<pre>
    require 'bigcommerce'
    api = Bigcommerce::Api.new({
      :store_url => 'https://store-xxxx.mybigcommerce.com',
      :username  => 'admin',
      :api_key   => 'key'
    })
    order = {'status_id' => 1};
    api.update_order(110, order);

    
</pre>


