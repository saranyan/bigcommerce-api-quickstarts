### Coupons

#### Get a list of coupons from the store

<pre>
    require 'bigcommerce'
    api = Bigcommerce::Api.new({
      :store_url => 'https://store-xxxx.mybigcommerce.com',
      :username  => 'admin',
      :api_key   => 'key'
    })
    coupons = api.get_coupons
</pre>


Coupons can be filtered through code, type, name, min_id and max_id. Without these filters, the call returns all the coupons in the store.For instance, if we want to return a list of coupons that are of type "percentage_discount", we can request the results by

<pre>
    require 'bigcommerce'
    api = Bigcommerce::Api.new({
      :store_url => 'https://store-xxxx.mybigcommerce.com',
      :username  => 'admin',
      :api_key   => 'key'
    })
    filter = {"type" => "percentage_discount"}
    coupons = api.get_coupons(filter)
</pre>

Refer to the developer portal documentation for <a href="http://developer.bigcommerce.com/api/coupons#get-couponsjson">the filtering fields</a> on the coupons endpoint.

#### Create a coupon
Coupons can be created by a POST request on the coupons endpoint. For example, if we want to create a coupon to take 50% off an order, then our coupon will have "percentage_discount" as the type. The "applies_to" field is optional and can be used to restrict the coupon to a set of products or categories. In the example shown below, the coupon is being restricted to a set of products.

<pre>
    require 'bigcommerce'
    api = Bigcommerce::Api.new({
      :store_url => 'https://store-xxxx.mybigcommerce.com',
      :username  => 'admin',
      :api_key   => 'key'
    })
    coupon = {'name' => 'somecoupon', 'type' => 'percentage_discount', 'amount' => '50.0', 'code' => '50off', 'enabled' => true, 'applies_to' => {'entity' => 'products', 'ids' => [32]}};
     api.create_coupon(coupon);
</pre>

#### Update a coupon
Updating a coupon is almost similar to above, except that we work off an ID via a PUT request. For example, if we want to change the above coupon to 30% discount instead of 50, and say, the coupon ID is 15, we can update the coupon by 

<pre>
     require 'bigcommerce'
    api = Bigcommerce::Api.new({
      :store_url => 'https://store-xxxx.mybigcommerce.com',
      :username  => 'admin',
      :api_key   => 'key'
    })
    coupon = {'type' => 'percentage_discount', 'amount' => '30.0', 'code' => '50off'};
     api.update_coupon(15,coupon);
</pre>
