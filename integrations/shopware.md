# Shopware V5

## First steps 

To get started with our Shopware plugin you will need to:

1. create an account on our [website](https://www.aiphilos.com/registrierung).

2. log into our [customer-backend](https://account.aiphilos.com).

3. navigate to "Administration", and then choose "Benutzerverwaltung" and "hinzufügen".

4. Create your fist user by giving them an Username(Benutzername) and Password(Passwort). Then click "Absenden" to save your data.

5. As long as we are waiting for certification by Shopware, download our Shopware plugin from the [Shopware store](https://store.shopware.com/aiphi88293318735f/aiphilos-suche.html).

6. The downloaded zip-file contains a Readme.md. Follow its instructions to install and configure the Shopware plugin for your shop. **Please make sure you set up a cronjob (Shopware < 5.2.15) and that you configure it appropriately.**


## Contributing
Feel free to contribute to our [Github repo](https://github.com/aiphilos/plugin-shopware)!

## Changelog
Version 1.1.9
- Bug fix for attribute usage
- Removed limits when fetching search results (Now more than 1000 results are possible)
- Improved synchronization with aiPhilos database

Version 1.1.8
- Optimized API search call
- Might improve performance due to shorter response times

Version 1.1.7
- Added help text for database name field
- Improved handling of incomplete article translations
- Implemented translations for filter properties

Version 1.1.6
- Improvements for aiPhilos database synchronization

Version 1.1.5
- Improved article data structure for aiPhilos database

Version 1.1.4
- Live search delay can now be configured (Default: 750ms)

Version 1.1.3
- Ajax live search is now delayed by one second to save requests

Version 1.1.2
- Bugfix for sub-shop capability
- Improvements when handling large amounts of data

Version 1.1.1
- Bugfix for excluded categories
- Bugfix for sub-shop handling

Version 1.1.0
- Initial release
