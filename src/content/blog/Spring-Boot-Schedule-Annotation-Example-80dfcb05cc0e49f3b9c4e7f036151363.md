---
title: Spring Boot Schedule Annotation Example
author: Nan Wang
pubDatetime: 2023-03-21T04:06:31Z
postSlug: my-recent-2
featured: false
draft: true
tags:
- Spring Boot
- Schedule
  description:
  In any web application, there are certain tasks that need to be executed at regular intervals. These tasks could be anything from updating a database to sending an email. Spring Boot provides an easy way to automate these tasks using the `@Scheduled` annotation. In this blog post, we will discuss how to use the `@Scheduled` annotation in Spring Boot to schedule tasks and automate processes.
---

# Spring Boot Schedule Annotation Example

## Introduction

In any web application, there are certain tasks that need to be executed at regular intervals. These tasks could be anything from updating a database to sending an email. Spring Boot provides an easy way to automate these tasks using the `@Scheduled` annotation. In this blog post, we will discuss how to use the `@Scheduled` annotation in Spring Boot to schedule tasks and automate processes.

## Using the @Scheduled Annotation

To enable the `@Scheduled` annotation in a Spring Boot application, you need to add the `@EnableScheduling` annotation to your configuration class. This will activate the task scheduling infrastructure provided by Spring. Here is an example of how to use the `@EnableScheduling` annotation to enable scheduling of tasks annotated with the `@Scheduled` annotation:

```
@SpringBootApplication
@EnableScheduling
public class Application {
    public static void main(String[] args) {
        SpringApplication.run(Application.class, args);
    }
}

```

By using the `@Scheduled` annotation with the `fixedRate` attribute, you can define a method to be executed at a fixed interval. For example, you can schedule a method to run every 5 seconds by setting the `fixedRate` attribute to 5000:

```
@Component
public class ScheduledTasks {
    private static final Logger log = LoggerFactory.getLogger(ScheduledTasks.class);

    @Scheduled(fixedRate = 5000)
    public void reportCurrentTime() {
        log.info("The time is now {}", new Date());
    }
}

```

In this example, we have annotated the `reportCurrentTime()` method with the `@Scheduled` annotation and set the `fixedRate` attribute to 5000. This means that the method will be executed every 5 seconds.

Alternatively, you can use the `cron` attribute to define a more complex schedule using a cron expression. For example, you can schedule a method to run at 10 AM every day with the following cron expression:

```
@Component
public class ScheduledTasks {
    private static final Logger log = LoggerFactory.getLogger(ScheduledTasks.class);

    @Scheduled(cron = "0 0 10 * * ?")
    public void reportCurrentTime() {
        log.info("The time is now {}", new Date());
    }
}

```

In this example, we have used the `cron` attribute to define the schedule. The expression `0 0 10 * * ?` means that the method will be executed at 10 AM every day.

Finally, you can also control the scheduler using additional attributes like `initialDelay`. For example, you can schedule a method to run every 5 seconds with a delay of 2 seconds before the first execution using the following code:

```
@Component
public class ScheduledTasks {
    private static final Logger log = LoggerFactory.getLogger(ScheduledTasks.class);

    @Scheduled(fixedRate = 5000, initialDelay = 2000)
    public void reportCurrentTime() {
        log.info("The time is now {}", new Date());
    }
}

```

In this example, we have set the `initialDelay` attribute to 2000. This means that the first execution of the method will be delayed by 2 seconds.

## Conclusion

In conclusion, the `@Scheduled` annotation is a useful feature of Spring Boot that can be used to automate processes and schedule tasks in a web application. By using attributes like `fixedRate`, `cron`, and `initialDelay`, you can control the scheduler and define complex schedules. This feature can be used to update a database, send emails, or perform any other automated task at regular intervals.
