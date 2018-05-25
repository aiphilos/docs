==================
Plugin Development
==================

A working plugin for aiPhilos is easy to develop and it requires only 3 steps to actually get started.

This guide assumes that you have at least created an aiPhilos account and that you have created a user so you can actually test your plugin against our api.
If you are unsure how to do this, have a look at :ref:`third_party_integrations`.

Apart from that your plugin needs to do the following things:

Create a database and sync items
================================

 You can create a database by synching your items via a **POST**-Request against our batch-endpoint

 the url for the batch-endpoint is: 

 .. literalinclude:: ../shared/endpoints/POST_batch.txt


 Because of the time being, aiPhilos is only available in german, you will need to **replace {langauge} with 'de' (without the quotes)** and **{db} with the database name of your choice**.

 Database names do not need to be unique across users.

 Send the items that should be synchronize in json-format like this:

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

 **1. The properties '_id' and '_action' are mandatory. the _id property for every item needs to be unique and _action needs to be set to POST so the item gets indexed by aiPhilos**

 **2. Please be aware that the batch-endpoint has a limit of 1000 items per request. Please make sure to send the items that should be indexed in chunks of no more than 1000 items.**

 The full documentation for the batch endpoint is available at:
 
 .. include:: ../shared/docLinks/batchEndpointLink.txt

Set an appropriate scheme
=========================

 Setting a scheme means telling aiPhilos how the data contained in your sent items is structured. To be precise: What fields it should analyze and what data kind of they hold.

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

 In this example custom_prop could mean different things. It could be a price, a rating or even a measurement.

 By setting a scheme you can make sure that your data is interpreted as expected. E. G. Making sure that prices or ratings are used to order items by price or rating, when needed. That manufacturers are recognized as such and that gtins or the frequency of an item bein ordered are taken into account when searching with aiPhilos
  
 To set a scheme you will need to send a **POST**-request against our scheme-endpoint.

 The url of the endpoint is: 

 .. literalinclude:: ../shared/endpoints/PUT_scheme.txt


 as before, **replace {language} with 'de'** (without the quotes) and **{db} with the name of the database that you created earlier**.

 Again, the payload needs to be sent in json format, similar to this example:

 .. code-block:: javascript

    {
        "custom_prop1": "general.auto",
        "custom_prop2": "general.price",
        "custom_prop3": "general.rating"
    }


 the following scheme-types are available:

 .. literalinclude:: ../shared/scheme_types.txt


 For more information have a look at :ref:`terminology_scheme`.

 The full documentation for the scheme endpoint is available at:

 .. include:: ../shared/docLinks/schemeEndpointLink.txt

 For more detailed information regarding the API have a look at our API-Documentation:

 .. include:: ../shared/docLinks/swaggerLink.txt

