HowTo
===

###SESSION
- `$this->get('session')->set('name', 'value')` memorizza una variabile di sessione nel controller
- `$this->get('session')->get('name')` recupera il valore di una variabile di sessione nel controller
- `{{ app.session.get('name') }}` recupera il valore di una variabile di sessione nel template
- `$this->get('session')->remove('name')` elimina la variabile di sessione
- `$this->get('session')->clear()` cancella tutta la sessione
