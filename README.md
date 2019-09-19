# laravel / encrypted-env
Save encrypt values in the ENV file instead of plain text


https://blog.fortrabbit.com/how-to-keep-a-secret

**Case:**

Encrypt values in the ENV file as it could potentially expose the server (as they are in plain text)

**STEPS:**

1. new file: 
`config/enc.php (holds enc keys)`

2. Create a new artisian command for encryption called “encrypt_this” at **app/console/commands/**
`$> artisan make:command encrypt_this`

3. Get individual cyphers for all / specific env vars (as per need) via the new command; replace them in env file. For example 
`$> php artisan encrypt 'xyz'`

4. put a decrypt function `env2()` for our specific env vars at:
bootstrap/envApp.php 

5. bootstrap/app.php (at the top): 
require_once  'envApp.php';

6. change the `env()` calls for these specific env keys to the new method `env2()` instead. 
