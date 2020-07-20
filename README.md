# HELM DEEP DIVE

## Concepts

- A Chart is a Helm package. It contains all of the resource definitions necessary to run an application, tool, or service inside of a Kubernetes cluster. Think of it like the Kubernetes equivalent of a Homebrew formula, an Apt dpkg, or a Yum RPM file.
- A Repository is the place where charts can be collected and shared. It's like Perl's CPAN archive or the Fedora Package Database, but for Kubernetes packages.
- A Release is an instance of a chart running in a Kubernetes cluster. One chart can often be installed many times into the same cluster. And each time it is installed, a new release is created. Consider a MySQL chart. If you want two databases running in your cluster, you can install that chart twice. Each one will have its own release, which will in turn have its own release name.

> Helm installs charts into Kubernetes, creating a new release for each installation. And to find new charts, you can search Helm chart repositories.

## Installation

1. Download helm binary (as root)

   ```shell
   curl -L https://mirror.openshift.com/pub/openshift-v4/clients/helm/latest/helm-darwin-amd64 -o /usr/local/bin/helm
   ```

2. Make the file executable

   ```shell
   chmod +x helm
   ```

3. Check the installed version:

   ```shell
   helm version
   version.BuildInfo{Version:"v3.1.3+2.el8", GitCommit:"4edcae3c96edf7fa6a3bcf93de6d85763aed1284", GitTreeState:"clean", GoVersion:"go1.13.4"}
   ```

## Basic commands

1. Create a project `my-app`.

   ```shell
   oc new-project my-app
   ```

2. Add a repository of Helm charts to your local Help client

   ```shell
   $ helm repo add stable https://kubernetes-charts.storage.googleapis.com/
   "stable" has been added to your repositories
   ```

   ---
   **NOTE**

   There are are two sources for Helm charts repositories
   - [https://kubernetes-charts.storage.googleapis.com](https://kubernetes-charts.storage.googleapis.com) is the `stable` repository;
   - [https://kubernetes-charts-incubator.storage.googleapis.com](https://kubernetes-charts-incubator.storage.googleapis.com) is the `incubator` repository.

   ---

3. Update the repository

   ```shell
   help repo update
   ```

4. Install an example MySQL chart

   ```shell
   helm install example-mysql stable/mysql
   ```

5. Verify that the chart has installed successfully.

   ```shell
      helm list
   ```

   ---
   **NOTE**

   With list you can get all [helm charts](https://helm.sh/docs/topics/charts/) installed in the namespace.

   ---

## Charts

