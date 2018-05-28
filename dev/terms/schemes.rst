.. _terminology_scheme:

scheme/scheme-type
==================

 There are several scheme-types available. These can be set via the scheme-endpoint.

 .. include:: ../../shared/docLinks/schemeEndpointLink.txt

 These types help aiPhilos interpret and classify you data, so that searches can be more accurate. 
 
 The following scheme-types can be set:

 .. literalinclude:: ../../shared/scheme_types.txt

 - **general.auto** aiPhilos standard mode of interpretation
 - **general.off** tells aiPhilos not to interpret this field
 - **product.number** a number representing the item
 - **product.name** the name of the item
 - **product.category** which category the item belongs to
 - **product.description**  a description of the item
 - **product.price** the price of the item
 - **product.gtin** the global trade item number
 - **product.manufacturer** who manufactures the item
 - **product.manufacturer_number** a number representing the manufacturer
 - **product.stock** the number of items in stock
 - **product.supplier** who supplies the item
 - **product.supplier_number** a number representing the supplier
 - **product.rating** a rating for the item
 - **product.state** information containing the state of the item
 - **order.frequency** information on how often the item is ordered

 Setting a scheme allows aiPhilos to be more specific and accurate when interpreting the items of your shop and therefore allowing for better search result.
 Item-fields for which no scheme is set are interpreted as type *general.auto*, meaning that aiPhilos will analyze their contents and use this additional information when classifying an item.
 If you want to explicitly exclude some fields you need to set their scheme-type to *general.off*.

 **The general rule of thumb is, that the more accurate you set the scheme-types of your data (e. g. setting the manufacturers, the ratings, prices etc) the better aiPihlos will be able to interpret the items in your shop and the better the results will be eventually.**

