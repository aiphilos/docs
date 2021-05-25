==================
Plugin Development
==================

It's easy to develop a working plugin for aiPhilos and it requires only three steps to actually get started.

This guide assumes that you have at least created an aiPhilos account and that you have created an user so you can test your plugin against our API.

Apart from that your plugin needs to do the following things:

Create a database and sync items
================================

 You can create a database by synching your items via a **POST-Request** against our batch-endpoint

 the url for the batch-endpoint is: 

 .. literalinclude:: ../shared/endpoints/POST_batch.txt


 Because for the time being, aiPhilos is only available in german, you will need to **replace {langauge} with 'de-de' (without the quotes) and {db} with the database name of your choice**.

 Database names do not need to be unique across users.

 Send the items that should be synchronized in json-format like this:

 .. code-block:: javascript

    { items : 
        [
            {
                "_id": "0",
                "_action": "POST",
                "additional_property1" : "additional_information",
                "additional_property2" : "additional_information"
            },
            {
                "_id": "1",
                "_action": "POST",
                "additional_property1" : "additional_information",
                "additional_property2" : "additional_information"
            }
        ]
    }

 
 
 **Two important points:**

 .. note :: *The properties '_id' and '_action' are mandatory. the _id property for every item needs to be unique and _action needs to be set to POST so the item gets indexed by aiPhilos**

 .. note :: **Please be aware that the batch-endpoint has a limit of 1000 items per request. Please make sure to send the items that should be indexed in chunks of no more than 1000.**

 The full documentation for the batch endpoint is available at:
 
 .. include:: ../shared/docLinks/batchEndpointLink.txt

Set an appropriate scheme
=========================

 Setting a scheme means telling aiPhilos how the data contained in the sent items is structured. To be precise: What fields it should analyze and what kind of data they hold.

 Have a look at the following example:

 .. code-block:: javascript

    { items : 
        [
            {
                "_id": "0",
                "_action": "POST",
                "custom_prop": 4.3                
            },
            {
                "_id": "1",
                "_action": "POST",
                "custom_prop": 50
            }
        ]
    }

 Here *custom_prop* could mean several things. It could be a price, a rating or even a measurement.

 By setting a scheme you can make sure that your data is interpreted as expected. Depending on the search query this could mean that that prices or ratings are used to order items appropriately, that manufacturers are recognized as such and that gtins or that the frequency of an item being ordered is being taken into account when searching with aiPhilos
  
 To set a scheme you will need to send a **POST-Request** against our scheme-endpoint.

 The url of the endpoint is: 

 .. literalinclude:: ../shared/endpoints/PUT_scheme.txt


 as before, **replace {language} with 'de-de'(without the quotes) and {db} with the name of the database that you created earlier**.

 Again, the payload needs to be sent in json format, similar to this example:

 .. code-block:: javascript

    {
        "custom_prop1": "general.auto",
        "custom_prop2": "product.price",
        "custom_prop3": "product.rating"
    }


 the following scheme-types are available:

 .. literalinclude:: ../shared/scheme_types.txt


 For more information about schemes have a look at :ref:`terminology_scheme`.

 The full documentation for the scheme endpoint is available at:

 .. include:: ../shared/docLinks/schemeEndpointLink.txt


Search
======

 You can now use one of our search endpoints to get search your search results

 The url for both endpoints is: 

 .. literalinclude:: ../shared/endpoints/POST_GET_search.txt

 As before, **replace {language} with 'de-de' (without quotes) and {db} with the name of you database**.

 The search can be initiated either by **POST- or by GET-Request**

 the following parameters can be submitted:

 - **query** : the actual query string
 - **from** : the number of found items that should be omitted when returning the result
 - **size** : Max number of returned items
 - **size** : the field by which to sort the results
 - **order** : Sort direction
 - **unsorted** : switch sorting on or off. false by default
 - **nlp_mode** : Natural-Language-Processing (NLP) Mode

 .. note :: **Only the query parameter is required. All others are optional**

 depending on how you send the request, these parameters need to be sent **either as query-paramerts (GET-Request) or as part of a json payload (POST-Request)**.

 example GET-Request: 

 .. literalinclude:: ../shared/requests/GET_search.txt

 example POST-Request:

 .. literalinclude:: ../shared/requests/POST_search.json
    :language: json


.. _Important-Configuration-Options:

Important Configuration Options
===============================
 Your plugin will need to provide the following settings. The names are suggestions.

 **active**
 
 This setting should determine whether or not the AI search is active. Since aiPhilos needs to analyze and interpret the data before delivering reliable results, in addition to 
 **on** or **off** a third option should be made available: **preparation**. This mode syncs the products to the aiPhilos-Cloud, but still retain the native search behaviour. After 
 a certain period of time the setting can be switched to **on** at which point the search requests and results should be made via the aiPhilos api. 

 see Important-Information_


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



.. _Important-Information:

Important Information
=====================

 After synchronizing items with aiPhilos and after setting a scheme, aiPhilos needs to analyze and interpret the data contained in the synchronized items. Depending on the complexity of the data and the amount of the items this may **take between three days and a week**. During this time search results are **not reflective of the final result**. It is important that you include an option to prepare the synchronized data (see Important-Configuration-Options_), which, as long as activated, does not replace the original search and only syncs the data to the aiPhilos-Cloud. It is also important to inform the user that enabling this mode is recommended as long as the synchronized data is not yet fully analyzed.
 **Disabling this mode, after the analysis and interpretation of the synchronized items is finished, should then switch to the actual aiPhilos search via the search-endpoint.**

 It would be advisable to implement additional parameters like "forceAi" to be able to test search results without setting the plugin to fully active.

 The full documentation for both endpoints can be looked up here:

 .. include:: ../shared/docLinks/searchEndpointLinks.txt

 
Further documentation
=====================

 For more detailed information regarding the API have a look at our API-Documentation:

 .. include:: ../shared/docLinks/swaggerLink.txt