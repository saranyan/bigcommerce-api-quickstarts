### Authentication 

#### Connecting with a store


Using the Bigcommerce Ruby library, you can establish a connection with a store in the following way.

You can checkout the official Bigcommerce library <a href="https://github.com/bigcommerce/bigcommerce-api-ruby"> here </a>.

<pre>
    require 'bigcommerce'
    api = Bigcommerce::Api.new({
      :store_url => 'https://store-xxxx.mybigcommerce.com',
      :username  => 'admin',
      :api_key   => 'key'
    })
    
</pre>