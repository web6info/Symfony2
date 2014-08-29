Servizi
===

####Richiamare servizi dentro servizi
Definire il servizio nel file `src/Web6/XxxBundle/Resurces/config/services.yml` come segue:
```yaml
xxx.functions:
  class: Web6\xxxBundle\Helper\Functions
  arguments:
    session: @session
    securityContext: @security.context
```
Nella classe `src/Web6/xxxBundle/Helper/Functions.php` va inserito il seguente codice:
```php
protected $mySession;
protected $mySecurityContext;

public function __construct($session, $securityContext){
  $this->mySession = $session;
  $this->mySecurityContext = $securityContext;
}
```
Adesso è possibile richiamare il servizio richiesto all'interno dei metodi, ad esempio:
```php
...
public function getAdmin(){
    if($this->mySecurityContext->isGranted('ROLE_SUPER_ADMIN')) return null;
    else return $this->mySecurityContext->getToken()->getUser();
}
...
```
