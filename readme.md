# Laravel Postman export

**Updates:**

0. It's a Package created with Dingo Router to OnePulse internal use. Fork and rewrite as you wish.
1. Postman collection scheme
2. Artisan consol commands
3. Can post project **URL** address via console
4. Basic file name change to **postman_collection.json**
5. Exporting @descriptions / @desc / @des
6. Exporting @params

## Installation

Install via composer:

```
composer require --dev galter/laravel-postman-export-onepulse
```

Add the service provider to your `providers` array in `config/app.php`

```php
galter\LaravelPostmanExportOnePulse\PostmanServiceProvider::class,
```

That's all!

## Usage

```
php artisan postman:export
```

This will create a `postman_collection.json` inside your `storage/app` folder. You are free to change the name of the file by specifying the filename as follows:

```
php artisan postman:export --name=MyAppName --api
```

### phpdoc Code rules

#### @var

`class Foo
{
/\*\*

- @var string $name Should contain a description
- @var string $description Should contain a description
  \*/
  protected $name, $description;
  }`

#### @param

`
/\*\*

- Counts the number of items in the provided array.
-
- @param mixed[] $items Array structure to count the elements of.
-
- @return int Returns the number of elements.
  \*/
  function count(array $items)
  {
  <...>
  }
  `

#### @return

`/\*\*

- @return integer Indicates the number of items.
  \*/
  function count()
  {
  <...>
  }`

#### @description

[phpdoc.org](https://docs.phpdoc.org/references/phpdoc/index.html)
