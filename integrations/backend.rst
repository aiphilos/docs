==================
Backend
==================


Important Configuration Options
===============================



 Your integration will need to provide the following settings. The names are suggestions.

 **active**
 
 This setting should determine whether or not the AI search is active. Since aiPhilos needs to analyze and interpret the data before delivering reliable results, in addition to 
 **on** or **off** a third option should be made available: **preparation**. This mode syncs the products to the aiPhilos-Cloud, but still retain the native search behaviour. After 
 a certain period of time the setting can be switched to **on** at which point the search requests and results should be made via the aiPhilos api. 

 **username**

 Similar to developers, users will need to create an account with aiPhilos to authorize with our cloud services. This is where they enter their username.

 **password**

 Similar to developers, users will need to create an account with aiPhilos to authorize with our cloud services. This is where they enter their password.

 **database name**

 The name of the aiPhilos database used by the shop. This must be a unique name comprised of only upper and lower case letters from the English alphabet numbers and underscores.

 **fallback**

 This option should let the user configure if and under what conditions the search should fall back to systems default search.

 * errors and no results (default)

 Fall back to the default search when either no results are found by aiPhilos or an error occurs. This should be the default setting.

 * Only on errors (minimal recommendation)

 Only fall back when an error occurs during the attempted aiPhilos search. This is the recommended minimum setting and especially useful once aiPhilos has fully learned your article data and the results have become good enough that you can be certain that if aiPhilos finds nothing, nothing is the correct result.

 * Only when no results are returned

 Only fall back if aiPhilos returns no results. This option should exist mostly for the sake of completeness.


Store system Configuration Options
==================================

Main Website
^^^^^^^^^^^^

Possible configurations. Accessible after unchecking "use default option":

 * Activate aiPhilos search: yes/no
 * Change username
 * Change password
 * Database: Development/test environment/production environment
 * Activate aiPhilos logs: yes/no

Store Website
^^^^^^^^^^^^^

Possible configuration options for the store website backend you may implenet in your plugins:

**General settings:**

 Dynamic search: yes/no
    * Activates/Deactivates the dynamic search for a very fast display of search results.

 Waiting time 
    * Sets the optimal waiting time in milliseconds

 Activation Autocomplete from
    * For entering the number of letters from which Autocomplete should be played (at least 3).

 URL for no-results page
    * Sets the URL of the no-results page in case no search results are found

**Appearance for no-result page:**

 Display top search results: yes/no
    * Activates/Deactivates top search results of your store shown on the no-results page.

 Number of top search results
    * Defines the number of top search results to be displayed on the no-results page.

 Displayed attributes: article name, article picture, article price
    * Selection of attributes that should be displayed during autosuggest.

**Suggestions for search terms:**

 Activate autosuggest: yes/no
    * Activates/Deactivates the display of search suggestions (top search results).


Feature Configuration Options
=============================

Some features of aiPhios can be configured individually.


**Autosuggest**

You can choose weather you want to show variations of the same product or similar products to the search request. You can also make the items in the list apear in a small or wide shape.


**Categories**

While context search works automatically, you can also manually add data to the products of your shop to sort them into categories.
Visitors can search for categories and browse through different items of a specific categorie.
The categories work by using the search function. They can also be displayed on the shop website itself.