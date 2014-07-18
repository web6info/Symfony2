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
