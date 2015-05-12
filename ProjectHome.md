The Cloud Application Modeling Language (CAML) enables expressing cloud-based deployments directly in UML. CAML provides a dedicated model library for expressing high-level deployment topologies and a set of UML profiles for wiring such deployment topologies with concrete cloud provider offerings.

## Downloads ##

  * The Cloud Library and the set of Cloud Provider Profiles are available at: [CAML Eclipse Plugins](https://code.google.com/a/eclipselabs.org/p/caml/source/browse/eclipse-plugins)

  * Deployment models for a reference application (it's based on the [Java Petstore)](http://www.oracle.com/technetwork/java/index-136650.html) can be found [here](https://code.google.com/a/eclipselabs.org/p/caml/source/browse/application). These models import CAML's cloud library and apply a cloud provider profile. Therefore, the respective plugins need to be installed first to avoid validation errors or unresolved references. It's best to locate the provided CAML plugins into the plugins / dropins folder of your Eclipse distribution. We have tested the plugins with Eclipse Kepler SR2, Modeling Distribution. The deployment model of the reference application for the [Google App Engine](https://developers.google.com/appengine/) also applies profiles provided by the [UML-Profile-Store](https://code.google.com/a/eclipselabs.org/p/uml-profile-store/). Therefore, the respective UML-Profile-Store [plugins](https://code.google.com/a/eclipselabs.org/p/uml-profile-store/source/browse/#git%2Feclipse-plugins) need to be installed as well. At least, the following two plugins are required: _eu.artist.migration.umlprofilestore_ and _eu.artist.migration.model.resources_. We used the [Papyrus](https://www.eclipse.org/papyrus/) modeling tool to create the models.

  * A set of application deployment blueprints based on [Amazon AWS best practices](http://aws.amazon.com/de/architecture/) are available at: [Blueprints](https://code.google.com/a/eclipselabs.org/p/caml/source/browse/deployment-blueprints)

## AWS-based Deployment ##

As CAML is based on UML, its reuse mechanisms can be applied for cloud application
deployments. This is particularly useful to provide frequently occurring deployment
patterns as predefined UML templates. To demonstrate the use of such a blueprint, the model beneath shows how our reference application is bound to a template, which refer, in our case, to a 2-tier web architecture. To reuse the predefined template, the deployable artifacts, i.e., _PetstoreBusiness_ and _PetstoreData_  need to be bound to the template parameters.

![http://caml.eclipselabs.org.codespot.com/git.wiki/img/AWSDeployment.png](http://caml.eclipselabs.org.codespot.com/git.wiki/img/AWSDeployment.png)

The depicted deployment model covers the component viewpoint of our reference application and the respective template for web application deployments. It consists of two cloud nodes that refer to the "M3Medium" offering of Amazon. Their location is required to be in Europe while the operation system needs to be Linux. For reliability reasons, they are placed in different availability zones. Requests that arrive at the cloud nodes are first handled by a load balancing service, which enables a greater fault tolerance of the application. The number of running cloud nodes is automatically managed by Amazon as expressed by the scalability strategy. Only the minimum number of running cloud nodes and their adjustment is configured. Both cloud nodes are connected to a cloud storage that in turn is replicated to improve data availability. Finally, as Amazon cloud nodes operate at the infrastructure level, the required middleware for our reference application is defined.

## Publications ##
Alexander Bergmayr, Javier Troya, Patrick Neubauer, Manuel Wimmer, and Gerti Kappel:[UML-based Cloud Application Modeling with Libraries, Profiles and Templates](http://caml.eclipselabs.org.codespot.com/git.wiki/publication/cloudmde2014.pdf), Accepted in CloudMDE@MODELS2014, [MODELS 2014](http://modelsconference.org/), Valencia, Spain