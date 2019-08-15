# Php_cs_precommit
___
## About
Auto installed git pre-commit hook for running Php-cs-fixer and Phpcpd code checking to PSR2 coding standard compliance, duplicate code. It checks only files that are to be committed.

  - Check code php-cs-fixer
  - Check code phpcpd
___
## Installation
Install `BaDung7576/php_cs_precommit` with composer require command:
```sh
$ composer require --dev "BaDung7576/php_cs_precommit"
```
To enable code sniff, аdd to "post-install-cmd" and "post-update-cmd" in `composer.json` installation script:
```
"post-install-cmd": [
    "sh ./vendor/BaDung7576/php_cs_precommit/src/setup.sh"
],
"post-update-cmd": [
    "sh ./vendor/BaDung7576/php_cs_precommit/src/setup.sh"
]
```

Then run `composer install` or `composer update`. `pre-commit` hook will be installed or updated if it already exists.
Create simple file `.php_cs` in root directory project. 
File `.php_cs` using to config rules checkcode php-cs-fixer. 
**PHP-CS-Fixer has a lot of options and ways of config.  You can read more it here: [PHP_CS_FIXER]( https://github.com/FriendsOfPHP/PHP-CS-Fixer)**

```php
<?php

$finder = PhpCsFixer\Finder::create()
    ->notPath('vendor')
    ->notPath('bootstrap')
    ->notPath('storage')
    ->in(__DIR__)
    ->name('*.php')
    ->notName('*.blade.php');

return PhpCsFixer\Config::create()
    ->setRules([
        '@PSR2' => true,
        'no_unused_imports' => true,
    ])
    ->setFinder($finder);
    
```
When Php-cs-fixer run, it will create file `.php_cs.cache`, you can add it to `.gitignore` to ignore
If you have error : `sh not recognized internal external command` 
=> Adding directory `C:\Program Files\Git\bin` to PATH Environment Variable in Windows

