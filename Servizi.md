Servizi
===

####Richiamare servizi dentro servizi
- [Referenziare (iniettare) servizi](http://symfony.com/it/doc/current/book/service_container.html#referenziare-iniettare-servizi)
- [How can I access a service outside of a controller with Symfony2?](http://stackoverflow.com/questions/6124444/how-can-i-access-a-service-outside-of-a-controller-with-symfony2)
- [Symfony2-How to use access a service from outside of a controller](http://stackoverflow.com/questions/8757916/symfony2-how-to-use-access-a-service-from-outside-of-a-controller)

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
