### Orders

#### Get a list of orders from the store

<pre>
    require 'vendor/autoload.php';
    use Bigcommerce\Api\Client as Bigcommerce;
    $orders = Bigcommerce::getOrders();

        foreach($orders as $order) {
            echo $order->name;
            echo $order->price;
        }
</pre>
By default, the getOrders() request returns only 50 orders. If you want to return all the orders from the store, you have to use filters. Look at the example below.

#### Get all orders from the store

Use the "limit" and "page" filter parameters to get a data beyond what the default query returns. Note that, per page, 200 orders is the max returned.

<pre>
    require 'vendor/autoload.php';
    use Bigcommerce\Api\Client as Bigcommerce;

    filter = array('limit' => 200, 'page' => 1)
    $orders = Bigcommerce::getOrders(filter);

        foreach($orders as $order) {
            echo $order->name;
            echo $order->price;
        }
</pre>

In cases, when you have more than 200 orders in your store, you can use a counter to update the page, while controlling the limit parameter. You can do something like below.

<pre>
    require 'vendor/autoload.php';
    use Bigcommerce\Api\Client as Bigcommerce;

    $count = Bigcommerce::getOrdersCount()/200;
    for ($i = 1; $i <= $count; $i++) {
        $filter = array('limit' => 200, 'page' => $i);
        $orders = Bigcommerce::getOrders($filter);
        foreach($orders as $order) {
            echo $order->name;
            echo $order->price;
        }
     }
    
</pre>

#### Update an order
Order takes many fields on the update requests. Refer to the documentation at http://developer.bigcommerce.com/api/orders#put-ordersidjson. Here, we update an order using just the mandatory fields.

<pre>
    require 'vendor/autoload.php';
    use Bigcommerce\Api\Client as Bigcommerce;

    $order = array('status_id' => 1);
    Bigcommerce::updateOrder(110, $order);
    
</pre>


