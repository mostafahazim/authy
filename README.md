# Rinvex Authy

**Rinvex Authy** is a simple wrapper for @Authy TOTP API, the best rated Two-Factor Authentication service for consumers, simplest 2fa Rest API for developers and a strong authentication platform for the enterprise.

[![Packagist](https://img.shields.io/packagist/v/rinvex/authy.svg?label=Packagist&style=flat-square)](https://packagist.org/packages/rinvex/authy)
[![VersionEye Dependencies](https://img.shields.io/versioneye/d/php/rinvex:authy.svg?label=Dependencies&style=flat-square)](https://www.versioneye.com/php/rinvex:authy/)
[![Scrutinizer Code Quality](https://img.shields.io/scrutinizer/g/rinvex/authy.svg?label=Scrutinizer&style=flat-square)](https://scrutinizer-ci.com/g/rinvex/authy/)
[![Code Climate](https://img.shields.io/codeclimate/github/rinvex/authy.svg?label=CodeClimate&style=flat-square)](https://codeclimate.com/github/rinvex/authy)
[![Travis](https://img.shields.io/travis/rinvex/authy.svg?label=TravisCI&style=flat-square)](https://travis-ci.org/rinvex/authy)
[![SensioLabs Insight](https://img.shields.io/sensiolabs/i/287d9498-12cc-4e5f-8d5d-685823ff0347.svg?label=SensioLabs&style=flat-square)](https://insight.sensiolabs.com/projects/287d9498-12cc-4e5f-8d5d-685823ff0347)
[![StyleCI](https://styleci.io/repos/73740838/shield)](https://styleci.io/repos/73740838)
[![License](https://img.shields.io/packagist/l/rinvex/authy.svg?label=License&style=flat-square)](https://github.com/rinvex/authy/blob/develop/LICENSE)

![Rinvex Authy](https://rinvex.com/assets/frontend/layout/img/products/rinvex-authy.png "Rinvex Authy")


## Table Of Contents

- [Usage](#usage)
- [Installation](#installation)
- [Changelog](#changelog)
- [Support](#support)
- [Contributing & Protocols](#contributing--protocols)
- [Security Vulnerabilities](#security-vulnerabilities)
- [About Rinvex](#about-rinvex)
- [Trademarks](#trademarks)
- [License](#license)


## Usage

Usage is pretty easy and straightforward:

### Prepare requirements

```php
$apiMode = 'production';
$apiKey = 'AuthyProductionKeyHere';
$httpClient = new \GuzzleHttp\Client();
```

> **Note:** make sure to replace `AuthyProductionKeyHere` with your keys from the installation steps.

### Authy App

Create a new Authy app instance and interact with it:

```php
$authyApp = new \Rinvex\Authy\App($httpClient, $apiKey, $apiMode);

$appStats = $authyApp->stats(); // Get app stats
$appDetails = $authyApp->details(); // Get app details
```

### Authy User

Create a new Authy user instance and interact with it:

```php
$authyUser = new \Rinvex\Authy\User($httpClient, $apiKey, $apiMode);

$user = $authyUser->register('user@domain.com', '317-338-9302', '54'); // Register user
$userActivity = $authyUser->registerActivity($user->get('user')['id'], 'cookie_login', 'Test Data'); // Register user activity
$userStatus = $authyUser->status($user->get('user')['id']); // Get user status
$userDeleted = $authyUser->delete($user->get('user')['id']); // Delete user
```

### Authy Token

Create a new Authy token instance and interact with it:

```php
$authyToken = new \Rinvex\Authy\Token($httpClient, $apiKey, $apiMode);

$smsTokenSent = $authyToken->send($user->get('user')['id'], 'sms'); // Send SMS token
$callTokenStarted = $authyToken->send($user->get('user')['id'], 'call'); // Start automated call
$tokenVerified = $authyToken->verify(54321, $user->get('user')['id']); // Verify token
```

### Intuitive Responses

Work Intuitively with Authy responses:

```php
$body = $tokenVerified->body(); // Get all response body
$code = $tokenVerified->statusCode(); // Get response status code
$succeed = $tokenVerified->succeed(); // Check whether respose is a success
$failed = $tokenVerified->failed(); // Check whether respose is a failure
$message = $tokenVerified->message(); // Get response message
$item = $tokenVerified->get('item'); // Get response body item
$errors = $tokenVerified->errors(); // Get response errors
```

> **Note:** All authy requests returns authy response, with a unified interface for your convenience, so you can interact with all responses the same way as above.


## Installation

1. Install the package via composer:
    ```shell
    composer require rinvex/authy
    ```

2. If you haven't already: Register an [Authy](https://www.authy.com) account -> Sign in -> Access [dashboard](https://dashboard.authy.com) -> Create new application -> Copy your API keys (you've two keys, one for production & another for testing/sandbox)

3. Done! You can refer to [Usage](#usage) again.


## Changelog

Refer to the [Changelog](CHANGELOG.md) for a full history of the project.


## Support

The following support channels are available at your fingertips:

- [Chat on Slack](http://chat.rinvex.com)
- [Help on Email](mailto:help@rinvex.com)
- [Follow on Twitter](https://twitter.com/rinvex)


## Contributing & Protocols

Thank you for considering contributing to this project! The contribution guide can be found in [CONTRIBUTING.md](CONTRIBUTING.md).

Bug reports, feature requests, and pull requests are very welcome.

- [Versioning](CONTRIBUTING.md#versioning)
- [Pull Requests](CONTRIBUTING.md#pull-requests)
- [Coding Standards](CONTRIBUTING.md#coding-standards)


## Security Vulnerabilities

If you discover a security vulnerability within this project, please send an e-mail to help@rinvex.com. All security vulnerabilities will be promptly addressed.


## About Rinvex

Rinvex is a software solutions startup, specialized in integrated enterprise solutions for SMEs established in Alexandria, Egypt since June 2016. We believe that our drive The Value, The Reach, and The Impact is what differentiates us and unleash the endless possibilities of our philosophy through the power of software. We like to call it Innovation At The Speed Of Life. That’s how we do our share of advancing humanity.


## Trademarks

- [Authy™](https://www.authy.com) is a trademark of [Twilio Inc.](https://www.twilio.com)


## License

This software is released under [The MIT License (MIT)](LICENSE).

(c) 2016 Rinvex LLC, Some rights reserved.
