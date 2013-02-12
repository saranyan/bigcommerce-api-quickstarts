### Products

1. Get a list of orders from the store
<pre>
    require_once 'Bigcommerce/Api.php'
    $products = Bigcommerce::getProducts();

        foreach($products as $product) {
            echo $product->name;
            echo $product->price;
        }
</pre>