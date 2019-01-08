---
title: ASP.NET Core load/stress testing
author: Jeremy-Meng
description: Describes several notable tools and approaches for load testing and stress testing ASP.NET Core apps.
ms.author: riande
ms.custom: mvc
ms.date: 01/04/2019
uid: test/loadtests
---
# Load and stress testing ASP.NET Core

Load testing and stress testing are important to ensure a web app is performant and scalable. Their goals are different even they often share similar tests.

**Load tests**: Tests whether the app can handle a specified load of users for a certain scenario while still satisfying the response goal. The app is run under normal conditions.

**Stress tests**: Tests app stability when running under extreme conditions and often a long period of time:

* High user load – either spikes or gradually increasing.
* Limited computing resources.  

Under stress, can the app recover from failure and gracefully return to expected behavior? The app is run under normal conditions.

<!-- We generally don't allow wikipedia links
[A Wikipedia article](https://en.wikipedia.org/wiki/Software_performance_testing) describes different types of performance testing, include
[load testing](https://en.wikipedia.org/wiki/Software_performance_testing#Load_testing)
and [stress testing](https://en.wikipedia.org/wiki/Software_performance_testing#Stress_testing).
 -->

## Visual Studio Tools

Visual Studio allows users to create, develop, and debug web performance and load tests. An option is available to create tests by recording actions in web browser.

[Quickstart: Create a load test project](/visualstudio/test/quickstart-create-a-load-test-project?view=vs-2017)
shows how to create, configure, and run a load test projects using Visual Studio 2017.

See [Additional Resources](#add) for more information.

Load tests can be configured to run in on-premise or run in the cloud using Azure DevOps.

## Azure DevOps

Load test runs can be started using the [Azure DevOps Test Plans](/azure/devops/test/load-test/index?view=vsts) service.

![](./load-tests/_static/azure-devops-load-test.png)

The service supports the following types of test format:

- Visual Studio test – web test created in Visual Studio.
- HTTP Archive-based test – captured HTTP traffic inside archive is replayed during testing.
- [URL-based test](/azure/devops/test/load-test/get-started-simple-cloud-load-test?view=vsts) – allows specifying URLs to load test, request types, headers, and query strings. Run setting parameters such as duration, load pattern, number of users, etc., can be configured.
- [Apache JMeter](https://jmeter.apache.org/) test.

## Azure portal

[Azure portal allows setting up and running load testing of Web Apps,](/azure/devops/test/load-test/app-service-web-app-performance-test?view=vsts) directly from the Performance tab of the App Service in Azure portal.

![](./load-tests/_static/azure-appservice-perf-test.png)

The test can be a manual test with a specified URL, or a Visual Studio Web Test file, which can test multiple URLs.

![](./load-tests/_static/azure-appservice-perf-test-config.png)

At end of the test, reports are generated to show the performance characteristics of the app. Example statistics include:

- Average response time
- Max throughput: requests per second
- Failure percentage

## Third-party Tools

The following list contains third-party web performance tools with various feature sets:

- [Apache JMeter](https://jmeter.apache.org/) : Full featured suite of load testing tools. Thread-bound: need one thread per user.
- [ab - Apache HTTP server benchmarking tool](https://httpd.apache.org/docs/2.4/programs/ab.html)
- [Gatling](https://gatling.io/) : Desktop tool with a GUI and test recorders. More performant than JMeter.
- [Locust.io](https://locust.io/) : Not bounded by threads.

<a name="add"></a>
## Additional Resources

[Load Test blog series](https://blogs.msdn.microsoft.com/charles_sterling/2015/06/01/load-test-series-part-i-creating-web-performance-tests-for-a-load-test/)
by Charles Sterling. Dated but most of the topics are still relevant.