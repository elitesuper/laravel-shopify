# Laravel Shopify App

[![Build Status](https://secure.travis-ci.org/ohmybrew/laravel-shopify.png?branch=master)](http://travis-ci.org/ohmybrew/laravel-shopify)
[![Coverage Status](https://coveralls.io/repos/github/ohmybrew/laravel-shopify/badge.svg?branch=master)](https://coveralls.io/github/ohmybrew/laravel-shopify?branch=master)

*Work in progress*. A Laravel package for aiding in Shopify App development, it will follow suit to `shopify_app` for Rails.

## Goals

+ Provide assistance in developing Shopify apps with Laravel
+ Integration with Shopify API
+ Authentication & installation for shops
+ Auto install app webhooks and scripttags thorugh background jobs
+ Provide basic ESDK views

## Requirements

Here are the requirements to run this Laravel package.

| Package                | Version   | Notes                                    |
| ---------------------- |:---------:|:---------------------------------------- |
| `php`                  | 7         | Due to `ohmybrew/basic-shopify-api`      |
| `laravel/framework`    | 5.4.*     |                                          |

## Installation

### Provider

Open `config/app.php` find `providers` array. Add a new line with:

```php
\OhMyBrew\ShopifyApp\ShopifyAppProvider::class,
```

### Facade

Open `config/app.php` find `aliases` array. Add a new line with:

```php
'ShopifyApp' => \OhMyBrew\ShopifyApp\Facades\ShopifyAppFacade::class,
```

### Middleware

Open `app/Http/Kernel.php` find `routeMiddleware` array. Add a new line with:

```php
'auth.shop' => \OhMyBrew\ShopifyApp\Middleware\AuthShop::class,
```

### Migrations

Run `php artisan migrate`.

## Routes

Here are the defined routes and what they do.

| Route                     | Notes                                    |
| ------------------------- |:---------------------------------------- |
| GET /login                | Displays login/install page              |
| POST /authenticate        | Authenticates the shop/installs the shop |

## Usage

### Accessing the current shop

Using the facade:

```php
// Returns instance of \OhMyBrew\ShopifyApp\Models\Shop
ShopifyApp::shop()
```

### Accessing API for the current shop

```php
// Returns instance of \OhMyBrew\BasicShopifyAPI (ohmybrew/basic-shopify-api)
$shop = ShopifyApp::shop();
$shop->api()->request(...);
```

## Notes

I have not touched PHP in years, I've been primarily a full-time Ruby developer. Please forgive any quirks :)

## LICENSE

This project is released under the MIT license.