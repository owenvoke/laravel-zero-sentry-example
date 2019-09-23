# Laravel Zero Sentry Example

## Install

1. Install the required Illuminate dependencies:
   ```bash
   $ composer require illuminate/queue:^5.8
   $ composer require illuminate/log:^5.8
   ```
1. Install the required Sentry dependencies:
   ```bash
   $ composer require sentry/sentry-laravel:^1.2
   ```
1. Register the required service providers in [`config/app.php`](config/app.php):
   ```diff
   +        Illuminate\Log\LogServiceProvider::class,
   +        Illuminate\Queue\QueueServiceProvider::class,
   +        Sentry\Laravel\ServiceProvider::class,
   ```
1. Create a new custom exception handler class under [`App\Exceptions\Handler`](app/Exceptions/Handler.php)
1. Register the new exception handler under [`bootstrap/app.php`](bootstrap/app.php):
   ```diff
   -    Illuminate\Foundation\Exceptions\Handler::class
   +    App\Exceptions\Handler::class
   ```

## Usage

This requires the `SENTRY_LARAVEL_DSN` environment variable to be set in your `.env` file, or global environment.

Throw an exception in a command to test. Or run the Sentry test command using `php application sentry:test`.
