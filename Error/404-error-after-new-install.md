#app.php return 404 error after new install

A fresh symfony 2 install does not contain any routing for the production environment. If you take a look under `app/config/routing_dev.yml`, you will notice that all of the routes that you see in the demo application are defined only for development. If you wish to test the demo on `app.php`, you have to first copy the routing from `routing_dev.yml` to `routing.yml`, and also enable the `AcmeDemoBundle` under you `AppKernel.php`:
```php
$bundles = array(
        new Symfony\Bundle\FrameworkBundle\FrameworkBundle(),
        new Symfony\Bundle\SecurityBundle\SecurityBundle(),
        new Symfony\Bundle\TwigBundle\TwigBundle(),
        new Symfony\Bundle\MonologBundle\MonologBundle(),
        new Symfony\Bundle\SwiftmailerBundle\SwiftmailerBundle(),
        new Symfony\Bundle\DoctrineBundle\DoctrineBundle(),
        new Symfony\Bundle\AsseticBundle\AsseticBundle(),
        new Sensio\Bundle\FrameworkExtraBundle\SensioFrameworkExtraBundle(),
        new JMS\SecurityExtraBundle\JMSSecurityExtraBundle(),
+       new Acme\DemoBundle\AcmeDemoBundle()
    }

if (in_array($this->getEnvironment(), array('dev', 'test'))) {
-       $bundles[] = new Acme\DemoBundle\AcmeDemoBundle();
        $bundles[] = new Symfony\Bundle\WebProfilerBundle\WebProfilerBundle();
        $bundles[] = new Sensio\Bundle\DistributionBundle\SensioDistributionBundle();
        $bundles[] = new Sensio\Bundle\GeneratorBundle\SensioGeneratorBundle();
    }
```

(+ is the line you should add, - is the line you should remove)
