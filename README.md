[![AOE](aoe-logo.png)](http://www.aoe.com)

# Aoe_LazyCatalogImages Magento Module

This module (LCI) is meant to provide URLs for images that contain enough information to render the image at a later point in time.
The current system pre-renders images and front-loads that overhead into the initial page render process.
Additionally, if the image cache is flushed and a page is cached with the old URL, then images will be broken.
LCI changes all URLs generated by the catalog/image helper to contain the full set of parameters to build an image and signs the 
parameters with a SHA265 hash to prevent tampering by end-users.

The actual rendering of the images is handled via the /lci.php and /media/catalog/product/LCI/.htaccess combo.
The .htaccess file will rewrite requests for non-existent files to be serviced by /lci.php.
The entrypoint, lci.php, checks if the requested file is actually a token that should be processed.
At the early stage of token decoding a failure results in a 404 response.
At later stages, after the token is decoded, a failure results in a redirect to a placeholder image.

## License
[OSL v3.0](http://opensource.org/licenses/OSL-3.0)

## Contributors
* [Lee Saferite](https://github.com/LeeSaferite) (AOE)
* Pull requests are welcome

## Compatability
* Helper Rewrites
    * catalog/image
* Module Dependencies
    * Mage_Core
    * Mage_Catalog

## TODO
* Add unit tests
* Change to locally cached image filename to match the URL filename so Apache (or whatever) can directly serve the image on future requests
* Add admin config for cache age and enable/disable

## Disclaimer
This module is experimental and not guaranteed to work.
