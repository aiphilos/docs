# PHP-SDK

[![Build Status](https://travis-ci.org/aiphilos/api-sdk-php.svg?branch=master)](https://travis-ci.org/aiphilos/api-sdk-php) [![Latest Stable Version](https://poser.pugx.org/aiphilos/api-sdk-php/v/stable)](https://packagist.org/packages/aiphilos/api-sdk-php) [![Total Downloads](https://poser.pugx.org/aiphilos/api-sdk-php/downloads)](https://packagist.org/packages/aiphilos/api-sdk-php) [![Latest Unstable Version](https://poser.pugx.org/aiphilos/api-sdk-php/v/unstable)](https://packagist.org/packages/aiphilos/api-sdk-php) [![License](https://poser.pugx.org/aiphilos/api-sdk-php/license)](https://packagist.org/packages/aiphilos/api-sdk-php)

Currently, **aiPhilos** provides two sets of APIs:
- **items** provides a real-time database and search engine using the **semantics** API (see below) improving search results and indexing through understanding natural language, adding natural language analysis and Artificial Intelligence as a component to understand your data set
- **semantics** can split natural human language input into machine-readable chunks and attach additional information usable to deepen natural language understanding in your application (tokenization, part of speech tagging, word classes and categories, named entity recognition, lexicographical data, synonyms/hypernyms/hyponyms, similarity and sentiment data, and learned knowledge)

## Installation
The easiest way to install this library is to use [composer](https://getcomposer.org/).

```json
{
    "require": {
        "aiphilos/api-sdk-php": "1.*"
    }
}
```

## Usage
### Semantics (Semantic analysis of natural language input)

#### Creating and configuring the client
```php
// Create client
$client = new Aiphilos\Api\Semantics\Client();

// Configure client
$client->setAuthCredentials('user', 'pass');
$client->setDefaultLanguage('de-de');
```

#### Parsing a single string
```php
$res = $client->parseString('Ordner');
```

#### Parsing multiple strings
```php
$res = $client->parseStrings(array('Ordner leitz', 'tastatur'));

// Alternative
$res = $client->parseStrings(array('example_1' => 'Ordner leitz', 'example_2' => 'tastatur'));
```

#### Using custom implementations for Lexemes and Synsets
```php
Aiphilos\Api\Semantics\LexemeFactory::setDefaultClass('My\Namespace\And\Classname'); // Instance of Aiphilos\Api\Semantics\LexemeInterface
Aiphilos\Api\Semantics\SynsetFactory::setDefaultClass('My\Namespace\And\Classname'); // Instance of Aiphilos\Api\Semantics\SynsetInterface
```

## License
This library is available under the Apache 2.0 License.