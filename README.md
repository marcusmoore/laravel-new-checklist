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

Aaron Francis [argues](https://mostlytechnical.com/episodes/19-its-content-baby) that you should turn on `preventSilentlyDiscardingAttributes` and `preventAccessingMissingAttributes` in production but only enable `preventLazyLoading` locally since lazy loading something in production isn't the end of the world.
