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

## Turn on Model Strictness
Consider adding the following to the `boot` method of `AppServiceProvider`:

```php
static::preventLazyLoading($shouldBeStrict);
static::preventSilentlyDiscardingAttributes($shouldBeStrict);
// static::preventAccessingMissingAttributes($shouldBeStrict);
```

[More details](https://laravel-news.com/shouldbestrict)

Aaron Francis [argues](https://mostlytechnical.com/episodes/19-its-content-baby) that you should turn on `preventSilentlyDiscardingAttributes` and `preventAccessingMissingAttributes` in production but only enable `preventLazyLoading` locally since lazy loading something in production isn't the end of the world.

## Prevent Stray HTTP Requests

Add this to the `TestCase`'s `setUp` method:

```php
Http::preventStrayRequests();
```

[Docs](https://laravel.com/docs/10.x/http-client#preventing-stray-requests)

## Use Immutable Dates

[Info](https://dyrynda.com.au/blog/laravel-immutable-dates)
