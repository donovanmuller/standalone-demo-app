# Standalone Demo Application

This demonstration application is used in the context of [this post](https://blog.switchbit.io/introducing-standalone-applications-to-spring-cloud-data-flow) 
introducing the *standalone* application type to Spring Cloud Data Flow.

## Usage

Assuming you have the default local Spring Cloud Data Flow server running (see [here for detailed instructions](https://blog.switchbit.io/introducing-standalone-applications-to-spring-cloud-data-flow/#bootingupindataflow)), 
you can deploy this standalone application using the following methods:

### Spring Cloud Data Flow Shell

To deploy this application using the Spring Cloud Data Flow [Shell](http://docs.spring.io/spring-cloud-dataflow/docs/1.0.1.RELEASE/reference/html/migration-guide.html#_shell_dsl_commands)
issue the following commands:

```
dataflow:>app register --name standalone-demo-app --type standalone --uri maven://io.switchbit:standalone-demo-app:1.0.0.BUILD-SNAPSHOT
Successfully registered application 'standalone:standalone-demo-app'
dataflow:>app list
╔══════╤═════════╤════╤════╤═══════════════════╗
║source│processor│sink│task│    standalone     ║
╠══════╪═════════╪════╪════╪═══════════════════╣
║      │         │    │    │standalone-demo-app║
╚══════╧═════════╧════╧════╧═══════════════════╝

dataflow:>standalone create --name demo-app-9000 --definition "standalone-demo-app --server.port=9000" --deploy
Created and deployed new standalone application 'demo-app-9000'
```

### Spring Cloud Data Flow Maven Plugin

To deploy this application using the [Spring Cloud Data Flow Maven Plugin](https://github.com/donovanmuller/spring-cloud-dataflow-maven-plugin)
simply execute the `scdf:deploy-standalone` goal.
