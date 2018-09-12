# Laravel-Vue-SPA

Ce répository est le résultat du tutoriel sur la création d'une SPA (Single Page Application) avec gestion de l'authentification par rôles réalisé avec Laravel et Vue.js

Le tutoriel est disponilbe [ici](https://medium.com/@ripoche.b/cr%C3%A9er-une-spa-avec-authentification-par-r%C3%B4les-avec-laravel-et-vue-js-e69782ac6896).

## Prerequis

- PHP 7
- Composer
- NodeJs
- MySQL

## Installation

- Cloner le repository
- Installer les dépendances back avec `composer install`
- Installer les dépendances front avec `npm i`
- Copier le fichier `.env.example` en `.env` et y renseigner les informations suivantes :
    - identifiants d'accès à la base de données (`DB_HOST`, `DB_PORT`, ...)
    - url de l'application (`APP_URL`). Soit l'adresse du virtual host si vous en avez configuré un, soit l'adresse délivrée par la commande `php artisan serve`
- Générer une clef d'application avec `php artisan key:generate`
- Générer une clef JWT avec `php artisan jwt:secret`
- Lancer les migrations avec `php artisan migrate --seed`.
- Compiler le front avec `npm run dev`

Si vous n'avez pas configuré de virtual host, lancez l'application avec la commande `php artisan serve`. Par défaut, cela rendra l'application disponible a l'adresse `http://127.0.0.1:8000`

