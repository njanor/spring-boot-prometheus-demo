# What is this?

This an example of how to use and configure Prometheus with Spring Boot. More details can be found at [my blog](https://njalnordmark.wordpress.com/2017/05/08/using-prometheus-with-spring-boot/).

## Usage
To build:

`./gradlew build`

To run:

`java -jar build/libs/spring-boot-with-prometheus-0.1.0.jar`

The Spring boot application is now running at <http://localhost:8080/>, with a management interface at <http://localhost:8081/>. Most notably, the Prometheus endpoint is running at <http://localhost:8081/prometheus-metrics/>.

**Note:** `management.security.enabled` is set to `false`.

Configuration in [application.yml](application.yml).

In this sample, I have included a single enpoint (<http://localhost:8080/endpoint>) which will always return `200 OK`, but have a 50/50 percent chance of counting the request as a `success` or `error` on the custom counter `my_sample_counter`. Spam this endpoint to see the Counter increase with the two labels.

Labels implemented in [SampleController](src/main/java/metricsDemo/SampleController.java).