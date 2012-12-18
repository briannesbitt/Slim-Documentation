---
title: Error Handling Output
layout: default
---

The Slim application's environment will always contain a key **slim.errors** with a value that is a writable
resource to which log and error messages may be written. The Slim application's log object will write log messages
to **slim.errors** whenever an Exception is caught or the log object is manually invoked.

If you want to redirect error output to a different location, you can define your own writable resource by
modifying the Slim application's environment settings. The log is setup in the Slim constructor so you must configure the environment variable before the creation of the Slim instance:

    <?php
    $env = \Slim\Environment::getInstance();
    $env['slim.errors'] = fopen( '/path/to/output/error.log', 'a' );

    $app = new \Slim\Slim();   // <== reads the 'slim.errors' environment variable

Remember, **slim.errors** does not have to point to a file; it can point to any valid writable resource.
