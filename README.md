# Laravel-Vue-SPA

This repository is the result of a tutorial about creating a SPA (Single Page Application) with role-based authentication with Laravel and Vue.

This tutorial is available [here](https://medium.com/@ripoche.b/create-a-spa-with-role-based-authentication-with-laravel-and-vue-js-ac4b260b882f) (version française [ici](https://medium.com/@ripoche.b/cr%C3%A9er-une-spa-avec-authentification-par-r%C3%B4les-avec-laravel-et-vue-js-e69782ac6896)).

## Info
This branch is an update for Laravel 6. For Laravel 5.8 check the branch "master".

## Prerequiries

- PHP 7
- Composer
- NodeJs
- MySQL

## Installation

- Clone the repository
- Installer back dependencies with `composer install`
- Install front dependencies with `npm i`
- Copy file `.env.example` in `.env` and add following informations:
    - Database credentials (`DB_HOST`, `DB_PORT`, ...)
    - Application url (`APP_URL`). Either virtual host address if you configure one, either address form the command `php artisan serve`
- Generate application key with `php artisan key:generate`
- Generate JWT key with `php artisan jwt:secret`
- Launch migrations with `php artisan migrate --seed`.
- Build front with `npm run dev`

If you did'nt set a virtual host, launch application with the `php artisan serve` command. By default, application will be served at `http://127.0.0.1:8000`

## Configuration

You can change the length of time (in minutes) that the token will be valid for by changin the `JWT_TTL` value in the `.env` file.

## Usage

Log as admin with `admin@test.com:admin` or as user with `user@test.com:secret`
