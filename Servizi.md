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
