## Memo dév

Mettre à jour la bdd structuréllement :
```
php bin/console doctrine:schema:update
```

Charger le jeu de fausses données : 
```
php bin/console doctrine:fixtures:load --env=test --quiet
```

Executer les tests :
```
php bin/phpunit
php bin/phpunit --coverage-html ./var/cache/test
```

