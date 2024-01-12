# `laravel new` checklist

WIP...

## Enforce Morph Maps
Add the following to the `boot` method of `AppServiceProvider`:

```php
use Illuminate\Database\Eloquent\Relations\Relation;

Relation::requireMorphMap();

Relation::morphMap([
  //
]);
```

## Turn on Mode Strictness
Add the following to the `boot` method of `AppServiceProvider`:

```php
Model::shouldBeStrict();
```

Which will turn on:

```php
static::preventLazyLoading($shouldBeStrict);
static::preventSilentlyDiscardingAttributes($shouldBeStrict);
static::preventAccessingMissingAttributes($shouldBeStrict);
```

[More details](https://laravel-news.com/shouldbestrict)
