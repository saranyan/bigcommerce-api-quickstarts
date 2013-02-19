### Products

#### Get a list of products from the store

<pre>
    require 'bigcommerce'
    api = Bigcommerce::Api.new({
      :store_url => 'https://store-xxxx.mybigcommerce.com',
      :username  => 'admin',
      :api_key   => 'key'
    })
    products = api.get_products
    
</pre>
By default, the get_products request returns only 50 products. If you want to return all the products from the store, you have to use filters. Look at the example below.

#### Get all products from the store

Use the "limit" and "page" filter parameters to get a data beyond what the default query returns. Note that, per page, 200 products is the max returned.

<pre>
    require 'bigcommerce'
    api = Bigcommerce::Api.new({
      :store_url => 'https://store-xxxx.mybigcommerce.com',
      :username  => 'admin',
      :api_key   => 'key'
    })
    products = api.get_products
</pre>

In cases, when you have more than 200 products in your store, you can use a counter to update the page, while controlling the limit parameter. You can do something like below.

<pre>
    require 'bigcommerce'
    api = Bigcommerce::Api.new({
      :store_url => 'https://store-xxxx.mybigcommerce.com',
      :username  => 'admin',
      :api_key   => 'key'
    })
    count = api.get_products_count/200 + 1
    products = []
    count.times do |i|
        products << api.get_products({:page => i, :limit => 200})
    end
    
</pre>

#### Create a product
Product takes many fields on the update requests. Refer to the documentation <a href="http://developer.bigcommerce.com/api/products#post-productsjson"> here </a>. Here, we create a product using just the mandatory fields.

<pre>
    require 'bigcommerce'
    api = Bigcommerce::Api.new({
      :store_url => 'https://store-xxxx.mybigcommerce.com',
      :username  => 'admin',
      :api_key   => 'key'
    })
    product = {:name => "Spiderman - The best return",:price => 9.99,:categories => [17],:type =>"physical",:availability => "available", :weight => 1}

    api.create_products(product)
    
</pre>


#### Update a product
Product takes many fields on the update requests. Refer to the documentation <a href="http://developer.bigcommerce.com/api/products#put-productsidjson"> here </a>. Here, we update a product using just the mandatory fields.

<pre>
    require 'bigcommerce'
    api = Bigcommerce::Api.new({
      :store_url => 'https://store-xxxx.mybigcommerce.com',
      :username  => 'admin',
      :api_key   => 'key'
    })
    product = {'status_id' => 1};
    api.update_product(110, product);

    
</pre>


