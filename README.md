# PHP 8.1 Laravel Development Environment

This Docker image is a fork of [Pierre-Yves Guerder's](https://github.com/pierreyves-guerder) PHP 8.1 development environment.

## Original Author
- Pierre-Yves Guerder <pierreyves.guerder@gmail.com>

## What's Included
- Ubuntu 22.04
- PHP 8.1 with common extensions
- MySQL Server
- Apache2
- Node.js & Yarn
- Composer
- Various development tools

## Changes from Original
- Updated to Ubuntu 22.04
- Modernized the Dockerfile to use new Docker best practices

## Usage
```bash
docker build -t your-name/laravel-php81 .
docker run -d your-name/laravel-php81
```

## License
This project maintains the same license as the original work by Pierre-Yves Guerder.

[![](https://images.microbadger.com/badges/version/pyguerder/bitbucket-pipelines-php81.svg)](https://microbadger.com/images/pyguerder/bitbucket-pipelines-php81 "Get your own version badge on microbadger.com") [![](https://images.microbadger.com/badges/image/pyguerder/bitbucket-pipelines-php81.svg)](https://microbadger.com/images/pyguerder/bitbucket-pipelines-php81 "Get your own image badge on microbadger.com")

## Based on Ubuntu 22.04

### Packages installed

- `php8.1-zip`, `php8.1-xml`, `php8.1-mbstring`, `php8.1-curl`, `php8.1-json`, `php8.1-imap`, `php8.1-mysql`, `php8.1-tokenizer`, `php8.1-xdebug`, `php8.1-intl`, `php8.1-soap`, `php8.1-pdo`, `php8.1-cli`, `php8.1-apcu` and `php8.1-gd`
- wget, curl, unzip
- Composer 2
- Mysql 8
- Node + Yarn

### Sample `bitbucket-pipelines.yml`

```YAML
image: iutrace/bitbucket-pipelines-php81
pipelines:
  default:
    - step:
        script:
          - service mysql start
          - mysql -h localhost -u root -proot -e "CREATE DATABASE test;"
          - composer install --no-interaction --no-progress --prefer-dist
          - ./vendor/phpunit/phpunit/phpunit -v --coverage-text --colors=never --stderr
```
