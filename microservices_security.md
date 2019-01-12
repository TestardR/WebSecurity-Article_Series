This article was done using my notes from a speech made by Antonio Goncalves in 2018.

<sub>Goncalves A. (2018). "Microservices: The Big Picture", Pluralsight, https://app.pluralsight.com/player?name=b8e004c8-b449-46aa-a09c-684b036b865f&clip=0&course=microservices-big-picture&author=antonio-goncalves</sub>

## What are microservices ?

Microservices describe a software development style that has grown in recent trends. It is a set of pratices that aims at increasing speed and efficiency in the development and management of software solutions that scale.This set of pratices is technology agnostic. It is more about applying principles and architectural patterns.

## "Micro" / "Services"

### About the micro in "microservices"

No universal meseare defines the perfect size of a microservice. Each microservice is supposed to do one thing and do it well. The micro refers to the scope of functionalities. Microservices are built upon a specific business capability, which can independently be deployed. It is known as "bounded context". One of the main goal for architects is to identify sub-domains within a project and divide it into microservices (user management, invoices, etc...).

### About the sercice in "microservices"

A service is an independently deployable component. It supposes interoperability through message based communication. It is known as service-oriented architecture (SOA).

### "Microservices" then ?

According to Martin Fowler (2019) "The microservice architectural style is an approach to developing a single application as a suite of small services, each running in its own process and communicating with lightweight mechanisms.".

<sub>Fowler M. (2019), Microsercices Resource Guide, url : https://www.martinfowler.com/microservices/</sub>

According to Sam Newman (Thoughtworks) "Microservices are small, autonomus services that work together".

<sub>Slocum M. (2018), Microservices: A quick and simple definition, url: https://www.oreilly.com/ideas/a-quick-and-simple-definition-of-microservices</sub>

## How doest it affect sofware development lifecycle ?

Microservices divide bigger project into smaller pieces allowing better time to market. Smaller pieces become smaller projects allowing for smaller teams. As such it is crucial to become more Agile as well. Teams divived upon the number of microservices have to communicate for better integration. Each microservice lives independently but relies on the rest of the microservices. Being small in terms of functionality means that they have to interact with the others. Only properly integrated, microservices will make the application work.

## Microservices emerged from throwbacks in monolith applications

### What the deal with monolith applications ?

The bigger the application gets the harder it is for developers to modify it, resuming itself into a decrease in productivity. Once the application reaches a certain size it will be necessary to divide the application into teams that focus on specificy areas (for instance one for the UI, another for the backend, another for testing, and another for deploying). The problem with monolith application is that it prevents the team from working independently. The whole team must be coordinated.

The bigger the application gets the harder the code is to understand. As a result, development typically slows down followed by a bad quality of code. Monolith applications hardly take advantage of emerging technologies, but bet on an long term commitment to a technology stack.

Monolith applications tend to scale up for bad reasons. You will need to change a lot of code just for modifying little stuffs, such as allocating a different database to a part of your application. Quickly, the web container hosting the application will get overloaded. The larger the application the more ressources it will consume. Finally, the app might run a huge database, which might negatively impact performances.

## How microservices influence your organization ?

You might want to set a team per subdomain, for instance for an ecommerce site, you would consider a team for User, another for Order and one for Product. As such, you can pick right-sized teams for each subdomain. Each team is independent and solely responsible for the lifecycle of the product, from development to deployment. That is why you have to embrace Agile and Devops methodologies. Even though microservices are independent, they will end up communicating. This means that at a certain point in that the integration as to properly managed.

## What about security in microservices ?

For Authorization and Authentication, it is a practice to use an Identity and Access Management system (IAM). It addresses the need to ensure appriopriate access to ressources accross your system. This means that microservices do not need to deal with authentication or authorization, or even storing credentials. You delegate authentication and authorization to the Identity and Access Management system. With Single Sign-on, once logged in, users do not have to log in again to access a different microservice. Identification protocols can be handled by Kerberos, OpenID, Oauth 2.0 or SAML.

Having a gateway to authenticate and authorize users, as a single entry point, comes with a lot of benefits. It authenticates requests and forward them to other services, which might in turn invoke other services. Some well known Identity and Access Management system are Okta, Keyclock or Shiro.

How does one microservice communicate to another the identity of the requester ? The answer is through access token. An access token securely stores information about user and is then exchanged between services. Each microservice has to make sure that the token is valid and access user information out of it. To verify that user is authorized to perform the operation or not, tokens can follow the specification of JSON Web Token. Another possibility is to use cookies.
