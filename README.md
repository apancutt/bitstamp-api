Bitstamp API (PHP)
==================

A PHP implementation for accessing the [Bitstamp API](https://www.bitstamp.net/api/).

Requirements
------------

 * PHP >= 5.4
 * php-curl
 * php-json (PHP >= 5.5)

Installation
------------

### Composer ###

Add the following dependency to your `composer.json` file:

    "require": {
        "apancutt/bitstamp-api": "1.0.*"
    }

Note that this library is currently under development so you will also need to add:

    "minimum-stability": "dev"

### Alternative Installation ###

[Download](https://github.com/apancutt/bitstamp-api/archive/master.zip) or [clone the repository](https://github.com/apancutt/bitstamp-api/)
into your project. You will need to implement your own autoloader.

Example Usage
-------------

    <?php

    $client_id = 0; // Your Bitstamp client/customer ID

    // You will need to generate API keys with the required access level using your
    // account control panel: https://www.bitstamp.net/account/security/api/
    $api_secret = "";
    $api_key = "";

    try {

        $client = new \Bitstamp\Api\Client($client_id, $api_secret, $api_key);

        echo "Loading account balance..." . PHP_EOL;
        print_r((new \Bitstamp\Api\Endpoint\Balance($client))->execute());

    } catch (\Exception $exception) {

        echo "[ERROR] {$exception->getMessage()}" . PHP_EOL;
        exit(1);

    }

More information can be found at: https://www.bitstamp.net/api/