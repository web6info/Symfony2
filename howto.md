HowTo
===

### SESSION
- `$this->get('session')->set('name', 'value')` memorizza una variabile di sessione nel controller
- `$this->get('session')->get('name')` recupera il valore di una variabile di sessione nel controller
- `{{ app.session.get('name') }}` recupera il valore di una variabile di sessione nel template
- `$this->get('session')->remove('name')` elimina la variabile di sessione
- `$this->get('session')->clear()` cancella tutta la sessione

### SUBSELECT DQL
La subselect si usa per selezionare gli ID. Per selezionare un campo diverso usare il comando IDENTITY.
```
SELECT u FROM Web6CondominiBundle:Unita u
LEFT JOIN u.condominio c
LEFT JOIN u.tipo t
WHERE u.id NOT IN (SELECT IDENTITY(p.unita) FROM Web6CondominiBundle:Proprieta p)
```

### SET/GET GLOBAL VARS IN TWIG TEMPLATE
Dichiarare la variabile nel file `app/config/config.yml`
```
twig:
  globals:
    var: "Ciao"
```
Per recuperare il valore della variabile nel template twig è sufficiente scrivere `{{var}}`

###SET/GET PARAMETERS IN CONTROLLER
Dichiarare la variavile nel file `app/config/parameters.yml`
```
parameters:
  var: "Ciao"
```
Per recuperare il valore della variabile nel controller è sufficiente scrivere `$this->container->getParameter('var')`

###GET USER IN CONTROLLER
```php
$user = $this->get('security.context')->getToken()->getUser();
$user = $this->getUser();
```

###CHECK ROLE
```php
$this->get('security.context')->isGranted('ROLE_ADMIN')
```

###PASSARE PARAMETRI AD UN FORM TYPE
editEscursioneAction; EscursioneType
