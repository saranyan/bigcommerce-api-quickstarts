### Connecting with a store

Using the Bigcommerce PHP library, you can establish a connection with a store in the following way.
<pre>
     
    require_once "Bigcommerce/Api.php"
    Bigcommerce_Api::configure(array(
    'store_url' => 'https://store-xxx.mybigcommerce.com',
    'username' => 'admin',
    'api_key' => 'xxxxxx'
    ));
    Bigcommerce_Api::setCipher('RC4-SHA');
    Bigcommerce_Api::verifyPeer(false);
    
</pre>