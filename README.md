Bitstamp API (PHP)
==================

A PHP implementation for accessing the [Bitstamp API](https://www.bitstamp.net/api/).

WARNING: The Bitstamp API allows you to perform live transactions. This library is provided as-is, to use free of
charge, and I will aim to keep it up-to-date with API changes. However, please remember that I will take no
responsibility for the integrity or reliability of this library and will not be responsible for any damage or loss of
earnings caused by the use of this library. Use at your own will.

Requirements
------------

 * PHP >= 5.4
 * ext-curl
 * ext-json (PHP >= 5.5)
 * ext-mcrypt

Installation
------------

### Composer ###

Add the following dependency to your `composer.json` file:

    "require": {
        "apancutt/bitstamp-api": "1.0.*"
    }

Note that **this library is currently under development** so you will also need to add:

    "minimum-stability": "dev"

Example Usage
-------------

    <?php
    // Path to the autoloader generated by Composer
    require_once __DIR__ . "/../vendor/autoload.php";

    // The HTTP request client, provided by panadas/module-httpclient
    $request = new \Panadas\Module\HttpClient\Request();

    /*
    // Alternatively, you can provide an instance of Panadas\Module\LoggerAbstract for log messages
    $logger = new \Panadas\Module\Logger\Unbuffered();
    $request = new \Panadas\Module\HttpClient\Request($logger);
    */

    // Your Bitstamp client/customer ID
    $client_id = 0;

    // You will need to generate API keys with the required access level using your
    // account control panel: https://www.bitstamp.net/account/security/api/
    $api_secret = "";
    $api_key = "";

    try {

        $client = new \Bitstamp\Api\Client($request, $client_id, $api_secret, $api_key);

        $balance = new \Bitstamp\Api\Endpoint\Balance($client))->execute();

        echo "You have {$balance->getBtcBalance()}BTC in your account\n";

    } catch (\Exception $exception) {

        echo "{$exception->getMessage()} in {$exception->getFile()}:{$exception->getLine()}\n";
        exit(1);

    }

More information regarding the available endpoints can be found at: https://www.bitstamp.net/api/

Donations
---------

If you would like to support this project, you are welcome to send a donation to 3Q4YPjpz7qbhaewdfCzHbry1v47wX5pWiX - your support and generosity is greatly appreciated.
