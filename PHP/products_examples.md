### Products

#### Get a list of products from the store.

<pre>
    require_once 'Bigcommerce/Api.php'
    $products = Bigcommerce::getProducts();

        foreach($products as $product) {
            echo $product->name;
            echo $product->price;
        }
</pre>
By default, the getProducts() request returns only 50 products. If you want to return all the products from the store, you have to use filters. Look at the example below.

#### Get all products from the store.
 
Use the "limit" and "page" filter parameters to get a data beyond what the default query returns. Note that, per page, 200 products is the max returned.

<pre>
    require_once 'Bigcommerce/Api.php'
    filter = array('limit' => 200, 'page' => 1)
    $products = Bigcommerce::getProducts(filter);

        foreach($products as $product) {
            echo $product->name;
            echo $product->price;
        }
</pre>

In cases, when you have more than 200 products in your store, you can use a counter to update the page, while controlling the limit parameter. You can do something like below.

<pre>
    require_once 'Bigcommerce/Api.php'
    $count = Bigcommerce::getProductsCount()/200;
    for ($i = 1; $i <= $count; $i++) {
        $filter = array('limit' => 200, 'page' => $i)
        $products = Bigcommerce::getProducts($filter);
        foreach($products as $product) {
            echo $product->name;
            echo $product->price;
        }
     }
    
</pre>

