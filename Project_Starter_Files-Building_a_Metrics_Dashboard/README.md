## Project Set up

1. Run `vagrant up` command - Wait till it is finished
2. Run `vagrant ssh` command
3. Run `sudo su -` command. Then navigate to vagrant folder - EX: `cd ..` then `cd /vagrant`
4. Install helm - 
    - `curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3`
    - `chmod 700 get_helm.sh`
    - `./get_helm.sh`
5. Install Grafana and Prometheus
    - run `kubectl create namespace monitoring`
    - run `helm repo add stable https://charts.helm.sh/stable`
    - run `helm repo update`
    - run `helm install prometheus prometheus-community/kube-prometheus-stack --namespace monitoring --kubeconfig /etc/rancher/k3s/k3s.yaml`
6. Open a new bash window and repeat steps `2-3`
7. run `kubectl get pods --all-namespace` to check if pods are finished being created
    - wait until pods are finished being created
    - if a pod is crashing, run `sudo curl -sfL https://get.k3s.io | INSTALL_K3S_VERSION=v1.19.5+k3s1 sh -` and continue waiting for pods to be in running or completed states
8. Install Jaegar
    - run `kubectl create namespace observability`
    - run `kubectl create -f https://raw.githubusercontent.com/jaegertracing/jaeger-operator/master/deploy/crds/jaegertracing.io_jaegers_crd.yaml`
    - run `kubectl create -n observability -f https://raw.githubusercontent.com/jaegertracing/jaeger-operator/master/deploy/service_account.yaml`
    - run `kubectl create -n observability -f https://raw.githubusercontent.com/jaegertracing/jaeger-operator/master/deploy/role.yaml`
    - run `kubectl create -n observability -f https://raw.githubusercontent.com/jaegertracing/jaeger-operator/master/deploy/role_binding.yaml`
    - run `kubectl create -n observability -f https://raw.githubusercontent.com/jaegertracing/jaeger-operator/master/deploy/operator.yaml`
9. run `kubectl get pods --all-namespace` to check if pods are finished being created or in a pending state
10. Cluster wide Jaeger
    - run `kubectl create -f https://raw.githubusercontent.com/jaegertracing/jaeger-operator/master/deploy/cluster_role.yaml`
    - run `kubectl create -f https://raw.githubusercontent.com/jaegertracing/jaeger-operator/master/deploy/cluster_role_binding.yaml`
11. After running cluster wide keep checking on status of the pods using `kubectl get pods --all-namespace`
    - this may take some time, just keep checking until they are finished
12. Install Python app
    - navigate to `manifests` folder
    - run `kubectl apply -f app/`
    - run `kubectl get pods --all-namespace` and check that newly created pods are finished being created
13. Exposing Grafana
    - run `kubectl get pod -n monitoring | grep grafana` and look for pod named `prometheus-grafana-########` where `#` is random characters
    - copy the pods name
    - run `kubectl port-forward -n monitoring [pod name] 3000`

**Note:** For the screenshots, you can store all of your answer images in the `answer-img` directory.

## Verify the monitoring installation

*TODO:* run `kubectl` command to show the running pods and services for the three components. Copy and paste the output or take a screenshot of the output and include it here to verify the installation

## Setup the Jaeger and Prometheus source
*TODO:* Expose Grafana to the internet and then setup Prometheus as a data source. Provide a screenshot of the home page after logging into Grafana.

## Create a Basic Dashboard
*TODO:* Create a dashboard in Grafana that shows Prometheus as a source. Take a screenshot and include it here.

## Describe SLO/SLI
*TODO:* Describe, in your own words, what the SLIs are, based on an SLO of *monthly uptime* and *request response time*.

## Creating SLI metrics.
*TODO:* It is important to know why we want to measure certain metrics for our customer. Describe in detail 5 metrics to measure these SLIs. 

## Create a Dashboard to measure our SLIs
*TODO:* Create a dashboard to measure the uptime of the frontend and backend services We will also want to measure to measure 40x and 50x errors. Create a dashboard that show these values over a 24 hour period and take a screenshot.

## Tracing our Flask App
*TODO:*  We will create a Jaeger span to measure the processes on the backend. Once you fill in the span, provide a screenshot of it here.

## Jaeger in Dashboards
*TODO:* Now that the trace is running, let's add the metric to our current Grafana dashboard. Once this is completed, provide a screenshot of it here.

## Report Error
*TODO:* Using the template below, write a trouble ticket for the developers, to explain the errors that you are seeing (400, 500, latency) and to let them know the file that is causing the issue.

TROUBLE TICKET

Name:

Date:

Subject:

Affected Area:

Severity:

Description:


## Creating SLIs and SLOs
*TODO:* We want to create an SLO guaranteeing that our application has a 99.95% uptime per month. Name three SLIs that you would use to measure the success of this SLO.

## Building KPIs for our plan
*TODO*: Now that we have our SLIs and SLOs, create KPIs to accurately measure these metrics. We will make a dashboard for this, but first write them down here.

## Final Dashboard
*TODO*: Create a Dashboard containing graphs that capture all the metrics of your KPIs and adequately representing your SLIs and SLOs. Include a screenshot of the dashboard here, and write a text description of what graphs are represented in the dashboard.  
