### Coupons

#### Get a list of coupons from the store

<pre>
    require 'vendor/autoload.php';
    use Bigcommerce\Api\Client as Bigcommerce;
    $coupons = Bigcommerce::getCoupons();

        foreach($coupons as $coupon) {
            echo $coupon->name;
            echo $coupon->type;
        }
</pre>


Coupons can be filtered through code, type, name, min_id and max_id. Without these filters, the call returns all the coupons in the store.For instance, if we want to return a list of coupons that are of type "percentage_discount", we can request the results by

<pre>
    require 'vendor/autoload.php';
    use Bigcommerce\Api\Client as Bigcommerce;
    $filter = array('type' => 'percentage_discount')
    $coupons = Bigcommerce::getCoupons($filter);
    
        foreach($coupons as $coupon) {
            echo $coupon->name;
            echo $coupon->type;
        }
</pre>

Refer to the developer portal documentation for <a href="http://developer.bigcommerce.com/api/coupons#get-couponsjson">the filtering fields</a> on the coupons endpoint.

#### Create a coupon
Coupons can be created by a POST request on the coupons endpoint. For example, if we want to create a coupon to take 50% off an order, then our coupon will have "percentage_discount" as the type. The "applies_to" field is optional and can be used to restrict the coupon to a set of products or categories. In the example shown below, the coupon is being restricted to a set of products.

<pre>
    require 'vendor/autoload.php';
    use Bigcommerce\Api\Client as Bigcommerce;

    $coupon = array('name' => 'somecoupon', 'type' => 'percentage_discount', 'amount' => '50.0', 'code' => '50off', 'enabled' => true, 'applies_to' => array('entity' => 'products', 'ids' => array(32)));
    echo Bigcommerce::createCoupon($coupon);
</pre>

#### Update a coupon
Updating a coupon is almost similar to above, except that we work off an ID via a PUT request. For example, if we want to change the above coupon to 30% discount instead of 50, and say, the coupon ID is 15, we can update the coupon by 

<pre>
     require 'vendor/autoload.php';
    use Bigcommerce\Api\Client as Bigcommerce;

    $coupon = array('type' => 'percentage_discount', 'amount' => '30.0', 'code' => '50off');
    echo Bigcommerce::createCoupon(15,$coupon);
</pre>
