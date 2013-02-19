### Products

#### Get a list of products from the store

<pre>
    require 'vendor/autoload.php';
    use Bigcommerce\Api\Client as Bigcommerce;
    $products = Bigcommerce::getProducts();

        foreach($products as $product) {
            echo $product->name;
            echo $product->price;
        }
</pre>
By default, the getProducts() request returns only 50 products. If you want to return all the products from the store, you have to use filters. Look at the example below.

#### Get all products from the store

Use the "limit" and "page" filter parameters to get a data beyond what the default query returns. Note that, per page, 200 products is the max returned.

<pre>
    require 'vendor/autoload.php';
    use Bigcommerce\Api\Client as Bigcommerce;

    filter = array('limit' => 200, 'page' => 1)
    $products = Bigcommerce::getProducts(filter);

        foreach($products as $product) {
            echo $product->name;
            echo $product->price;
        }
</pre>

In cases, when you have more than 200 products in your store, you can use a counter to update the page, while controlling the limit parameter. You can do something like below.

<pre>
    require 'vendor/autoload.php';
    use Bigcommerce\Api\Client as Bigcommerce;

    $count = Bigcommerce::getProductsCount()/200;
    for ($i = 1; $i <= $count+1; $i++) {
        $filter = array('limit' => 200, 'page' => $i);
        $products = Bigcommerce_Api::getProducts($filter);
        foreach($products as $product) {
            echo $product->name;
            echo $product->price;
        }
     }
    
</pre>

#### Create a product

Products have many fields. You can check out <a href="http://developer.bigcommerce.com/api/products#post-productsjson">this docs page</a> for information on the product fields allowed as part of a POST request.

Let us say, we want to create a product using just the mandatory fields needed for a POST request. Note that price needs to specified as a string, while the weight is a decimal. Note that if the is_visible flag, though not mandatory is not set to true, the product by default would not be visible -

<pre>
    require 'vendor/autoload.php';
    use Bigcommerce\Api\Client as Bigcommerce;

    $product = array('name' => 'ABC Blocks', 'type' => 'physical', 'price' => '19.99', 'weight' => 2.3, 'categories' => array(34), 'availability' => 'available', 'is_visible' => true);
    echo Bigcommerce::createProduct($product);
    
</pre>

#### Update a product
If we want to update the product created above, we would do it as -

<pre>
    require 'vendor/autoload.php';
    use Bigcommerce\Api\Client as Bigcommerce;

    $product = array('name' => 'ABC Blocks', 'type' => 'physical', 'price' => '9.99', 'weight' => 2.3, 'categories' => array(34), 'availability' => 'available');
    echo Bigcommerce::updateProduct(46, $product);
    
</pre>

#### Search a product by SKU
If we want to search by a product SKU, we can use the following code. Remember that when a product has optionset/variations defined, and if the individual options have SKUs defined, then the product SKU is overriden by the option SKUs. Currently, there are two ways to search for SKUs - GET /products?sku="something" or GET /products/skus?sku="something". The first call only returns product level SKU and not option level SKUs. 

<pre>
    require 'vendor/autoload.php';
    use Bigcommerce\Api\Client as Bigcommerce;

    $filter = array('sku' => 'abc-blocks-1-wood');
    $skus = Bigcommerce::getSkus($filter);
    print_r($skus);
</pre>


