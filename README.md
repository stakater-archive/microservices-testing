# microservices-testing

how to test microservices based applications?

![Testing Pyramid 1](img/testing-pyramid.png)

Unit tests are fast to execute, give the right level of feedback about what is broken. As you go up the pyramid, the tests are slower and it becomes harder to point out root cause of failures because the surface area is larger.

Its essential point is that you should have many more low-level unit tests than high level end-to-end tests running through a GUI.

![Test Pyramid](img/test-pyramid.png)

A common problem is that teams conflate the concepts of end-to-end tests, UI tests, and customer facing tests. These are all orthogonal characteristics. For example a rich javascript UI should have most of its UI behavior tested with javascript unit tests using something like Jasmine. A complex set of business rules could have tests captured in a customer-facing form, but run just on the relevant module much as unit tests are.

> I always argue that high-level tests are there as a second line of test defense. If you get a failure in a high level test, not just do you have a bug in your functional code, you also have a missing or incorrect unit test. Thus I advise that before fixing a bug exposed by a high level test, you should replicate the bug with a unit test. Then the unit test ensures the bug stays dead.

# Testing Strategies for Microservices

![Testing Strategies for Microservices](img/test-types.png)

# Unit Tests

Unit tests : exercise the smallest pieces of testable software in the application to determine whether they behave as expected.

# Integration Tests

Integration tests : verify the communication paths and interactions between components to detect interface defects.

# Component tests

limit the scope of the exercised software to a portion of the system under test, manipulating the system through internal code interfaces and using test doubles to isolate the code under test from other components.

# Contract tests

Verify interactions at the boundary of an external service asserting that it meets the contract expected by a consuming service.

# End-to-end tests

verify that a system meets external requirements and achieves its goals, testing the entire system, from end to end.

# Consumer Driven Contracts
  
It's nearly impossible for you to know all the ways consumers might use your services. With a [consumer-driven contract](http://martinfowler.com/articles/consumerDrivenContracts.html) model, it's the consumer's responsibility to provide a suite of tests that specify what types of interactions are needed and in which format. Your service would then agree to this contract and ensure that it's not broken. This gets rid of dependencies on other services. This approach also enables you to verify that the contract is being fulfilled at build time.

Tools like [Pact](https://github.com/realestate-com-au/pact) will give you a better understanding of how you can achieve this type of functionality for developing and testing microservices. Once you have a consumer-driven contract process in place, the next key step in testing microservices is to shift-right into the previously forbidden world of production.

# References

* https://martinfowler.com/articles/microservice-testing/
* https://www.thoughtworks.com/insights/blog/architecting-continuous-delivery
