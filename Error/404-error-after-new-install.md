#app.php return 404 error after new install

A fresh symfony 2 install does not contain any routing for the production environment. If you take a look under `app/config/routing_dev.yml`, you will notice that all of the routes that you see in the demo application are defined only for development. If you wish to test the demo on `app.php`, you have to first copy the routing from `routing_dev.yml` to `routing.yml`, and also enable the `AcmeDemoBundle` under you `AppKernel.php`:

