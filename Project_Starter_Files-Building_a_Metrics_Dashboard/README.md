## Project Set up
**Note:** For the screenshots, you can store all of your answer images in the `answer-img` directory.

## Verify the monitoring installation

*TODO:* run `kubectl` command to show the running pods and services for the three components. Copy and paste the output or take a screenshot of the output and include it here to verify the installation
    ![alt text](https://github.com/gpcmax/CNAND_nd064_C4_Observability_Starter_Files/blob/master/Project_Starter_Files-Building_a_Metrics_Dashboard/answer-img/Monitoring_pods_and_services.PNG?raw=true)
    ![alt text](https://github.com/gpcmax/CNAND_nd064_C4_Observability_Starter_Files/blob/master/Project_Starter_Files-Building_a_Metrics_Dashboard/answer-img/Observability_pods_and_services.PNG?raw=true)
    ![alt text](https://github.com/gpcmax/CNAND_nd064_C4_Observability_Starter_Files/blob/master/Project_Starter_Files-Building_a_Metrics_Dashboard/answer-img/Default_pods_and_services.PNG?raw=true)

## Setup the Jaeger and Prometheus source
*TODO:* Expose Grafana to the internet and then setup Prometheus as a data source. Provide a screenshot of the home page after logging into Grafana.
    ![alt text](https://github.com/gpcmax/CNAND_nd064_C4_Observability_Starter_Files/blob/master/Project_Starter_Files-Building_a_Metrics_Dashboard/answer-img/grafana_mainpage.PNG?raw=true)

## Create a Basic Dashboard
*TODO:* Create a dashboard in Grafana that shows Prometheus as a source. Take a screenshot and include it here.
    ![alt text](https://github.com/gpcmax/CNAND_nd064_C4_Observability_Starter_Files/blob/master/Project_Starter_Files-Building_a_Metrics_Dashboard/answer-img/PrometheusDashboard.PNG?raw=true)

## Describe SLO/SLI
*TODO:* Describe, in your own words, what the SLIs are, based on an SLO of *monthly uptime* and *request response time*:

    * What is an SLI: A SLI is a meaningful level of assessment of the services and shows if a SLO was achieved or not. 

    * SLI based on Monthly uptime SLO: The average uptime returned during the month of August was 95% as compared to the SLO of 93%. Meaning the goal for uptime was acheived for the month of August.

    * SLI based on request response time: The aveerage request response time during the month of August was 105 ms compare to the SLO of 150 ms. Meaning the goal for response time was acheived for the month of august

## Creating SLI metrics.
*TODO:* It is important to know why we want to measure certain metrics for our customer. Describe in detail 5 metrics to measure these SLIs:

    * Latency: Latency is important to monitor since this will tell the developers the time it takes for data to pass form one point to another.

    * Memory Usage: Memory usage is important for moniotoring since if the application uses too much memory the applicaiton can start to feel slow and the user will be impacted. Tracking this metric the developer can make tweaks to bring down the memory usage of the application.

    * Error Rate: Error rate is important to monitor since this will tell the developers the amount of errors that are appearing and at the rate they appear. This can point to more important errors by seeing how many of said errors appeared at a given rate the developers can know which will need to be a priority.

    * Uptime: Uptime is important to monitor so that developers know the percentage of the time the service is running. If it drops below a certain point this can be cause for concern and if it was not tracked it would be hard to tell how the service is handling.

    * Network: Network is important to monitor since the developer can see how much bandwith is required for a service to function. With this data the developer can look for ways to decrese the amount of bandwith required.

## Create a Dashboard to measure our SLIs
*TODO:* Create a dashboard to measure the uptime of the frontend and backend services We will also want to measure to measure 40x and 50x errors. Create a dashboard that show these values over a 24 hour period and take a screenshot.
    ![alt text](https://github.com/gpcmax/CNAND_nd064_C4_Observability_Starter_Files/blob/master/Project_Starter_Files-Building_a_Metrics_Dashboard/answer-img/MainDashboard.PNG?raw=true)

## Tracing our Flask App
*TODO:*  We will create a Jaeger span to measure the processes on the backend. Once you fill in the span, provide a screenshot of it here.
    ![alt text](https://github.com/gpcmax/CNAND_nd064_C4_Observability_Starter_Files/blob/master/Project_Starter_Files-Building_a_Metrics_Dashboard/answer-img/jaegerDashboard.PNG?raw=true)

## Jaeger in Dashboards
*TODO:* Now that the trace is running, let's add the metric to our current Grafana dashboard. Once this is completed, provide a screenshot of it here.
    ![alt text](https://github.com/gpcmax/CNAND_nd064_C4_Observability_Starter_Files/blob/master/Project_Starter_Files-Building_a_Metrics_Dashboard/answer-img/jaegerData.PNG?raw=true)
    
## Report Error
*TODO:* Using the template below, write a trouble ticket for the developers, to explain the errors that you are seeing (400, 500, latency) and to let them know the file that is causing the issue.

TROUBLE TICKET

Name: Backend Error

Date: 09/26/2021

Subject: Website 404 Error

Affected Area: Backend Service

Severity: Urgent

Description: Base on metrics the error rate is appearing at high of a rate.


## Creating SLIs and SLOs
*TODO:* We want to create an SLO guaranteeing that our application has a 99.95% uptime per month. Name three SLIs that you would use to measure the success of this SLO.

    * Latency: Weekly Goal: During a week requests will take less then 80 ms 96% of the time.

    * Error Rate: Weekly Goal: During a week 97% of all HTTP status should return 20x.

    * Memory Usage: Weekly Goal: During a week memory usage will be below 50 mb 98% of the time.

## Building KPIs for our plan
*TODO*: Now that we have our SLIs and SLOs, create KPIs to accurately measure these metrics. We will make a dashboard for this, but first write them down here.

    * Total memory usage in mb used during a month for each service.

    * Total network bandwith transmitted per service during a month.

    * Total number of errors per month.

    * Total cpu usage per service during a month of use.

## Final Dashboard
*TODO*: Create a Dashboard containing graphs that capture all the metrics of your KPIs and adequately representing your SLIs and SLOs. Include a screenshot of the dashboard here, and write a text description of what graphs are represented in the dashboard.  
    ![alt text](https://github.com/gpcmax/CNAND_nd064_C4_Observability_Starter_Files/blob/master/Project_Starter_Files-Building_a_Metrics_Dashboard/answer-img/FullDashboard.PNG?raw=true)
