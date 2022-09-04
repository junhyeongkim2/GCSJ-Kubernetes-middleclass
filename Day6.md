### 1주차 - Day 6

**-Getting started with Google Kubernetes Engine-**

# **Task 1. Deploy GKE clusters**

In this task, you use the Google Cloud Console and Cloud Shell to deploy GKE clusters.

# Use the Google Cloud Console to deploy a GKE cluster

1. In the Google Cloud Console, on the **Navigation menu** (), click **Kubernetes Engine** > **Clusters**.

   [https://cdn.qwiklabs.com/tkgw1TDgj4Q%2BYKQUW4jUFd0O5OEKlUMBRYbhlCrF0WY%3D](https://cdn.qwiklabs.com/tkgw1TDgj4Q%2BYKQUW4jUFd0O5OEKlUMBRYbhlCrF0WY%3D)

2. Click **Create** to begin creating a GKE cluster. Click **configure** for **Standard: You manage your cluster**.
3. Examine the console UI and the controls to change the cluster name, the cluster location, Kubernetes version, the number of nodes, and the node resources such as the machine type in the default node pool.

Clusters can be created across a region or in a single zone. A single zone is the default. When you deploy across a region the nodes are deployed to three separate zones and the total number of nodes deployed will be three times higher.

1. Change the cluster name to **standard-cluster-1** and zone to **us-central1-a**. Leave all the values at their defaults and click **Create**.

The cluster begins provisioning.

**Note:** You need to wait a few minutes for the cluster deployment to complete.

When provisioning is complete, the **Kubernetes Engine > Clusters** page looks like the screenshot:

[https://cdn.qwiklabs.com/syYSoVJHBotCDpSDi4OSQB1KleBOUbhmJXxmXfvrhpI%3D](https://cdn.qwiklabs.com/syYSoVJHBotCDpSDi4OSQB1KleBOUbhmJXxmXfvrhpI%3D)

Click *Check my progress* to verify the objective.

Assessment Completed!

Deploy GKE cluster

**Check my progress**

_Assessment Completed!_

1. Click the cluster name **standard-cluster-1** to view the cluster details
2. You can scroll down the page to view more details.
3. Click the **Storage** and **Nodes** tabs under the cluster name (standard-cluster-1) at the top to view more of the cluster details.

# **Task 2. Modify GKE clusters**

It is easy to modify many of the parameters of existing clusters using either the Google Cloud Console or Cloud Shell. In this task, you use the Google Cloud Console to modify the size of GKE clusters.

1. In the Google Cloud Console, on the **Navigation menu** (), click **Kubernetes Engine** > **Clusters** > **standard-cluster-1**, click **NODES** at the top of the details page.

   [https://cdn.qwiklabs.com/tkgw1TDgj4Q%2BYKQUW4jUFd0O5OEKlUMBRYbhlCrF0WY%3D](https://cdn.qwiklabs.com/tkgw1TDgj4Q%2BYKQUW4jUFd0O5OEKlUMBRYbhlCrF0WY%3D)

2. In **Node Pools** section, click **default-pool**.
3. In the Google Cloud Console, click **RESIZE** at the top of the **Node Pool Details** page.
4. Change the number of nodes from 3 to 4 and click **RESIZE**.

[https://cdn.qwiklabs.com/c%2Bnek4K0%2BlE107Y%2FsEtEcUQ7mp95gW2veEn5SmTGGj8%3D](https://cdn.qwiklabs.com/c%2Bnek4K0%2BlE107Y%2FsEtEcUQ7mp95gW2veEn5SmTGGj8%3D)

1. In the Google Cloud Console, on the **Navigation menu** (), click **Kubernetes Engine** > **Clusters**.

   [https://cdn.qwiklabs.com/tkgw1TDgj4Q%2BYKQUW4jUFd0O5OEKlUMBRYbhlCrF0WY%3D](https://cdn.qwiklabs.com/tkgw1TDgj4Q%2BYKQUW4jUFd0O5OEKlUMBRYbhlCrF0WY%3D)

When the operation completes, the **Kubernetes Engine > Clusters** page should show that standard-cluster-1 now has four nodes.

Click *Check my progress* to verify the objective.

Please change the number of nodes.

Modify GKE clusters

**Check my progress**

_Please change the number of nodes._

# **Task 3. Deploy a sample workload**

In this task, using the Google Cloud console you will deploy a Pod running the nginx web server as a sample workload.

1. In the Google Cloud Console, on the **Navigation menu**(), click **Kubernetes Engine** > **Workloads**.

   [https://cdn.qwiklabs.com/tkgw1TDgj4Q%2BYKQUW4jUFd0O5OEKlUMBRYbhlCrF0WY%3D](https://cdn.qwiklabs.com/tkgw1TDgj4Q%2BYKQUW4jUFd0O5OEKlUMBRYbhlCrF0WY%3D)

2. Click **Deploy** to show the Create a deployment wizard.
3. Click **Continue** to accept the default container image, nginx:latest, which deploys 3 Pods each with a single container running the latest version of nginx.
4. Scroll to the bottom of the window and click the **Deploy** button leaving the **Configuration** details at the defaults.
5. When the deployment completes your screen will refresh to show the details of your new nginx deployment.

Click *Check my progress* to verify the objective.

Assessment Completed!

Deploy a sample nginx workload

**Check my progress**

_Assessment Completed!_

# **Task 4. View details about workloads in the Google Cloud Console**

In this task, you view details of your GKE workloads directly in the Google Cloud Console.

1. In the Google Cloud Console, on the **Navigation menu** (), click **Kubernetes Engine** > **Workloads**.

   [https://cdn.qwiklabs.com/tkgw1TDgj4Q%2BYKQUW4jUFd0O5OEKlUMBRYbhlCrF0WY%3D](https://cdn.qwiklabs.com/tkgw1TDgj4Q%2BYKQUW4jUFd0O5OEKlUMBRYbhlCrF0WY%3D)

2. In the Google Cloud Console, on the **Kubernetes Engine > Workloads** page, click **nginx-1**.

This displays the overview information for the workload showing details like resource utilization charts, links to logs, and details of the Pods associated with this workload.

1. In the Google Cloud Console, click the **Details** tab for the **nginx-1** workload. The Details tab shows more details about the workload including the Pod specification, number and status of Pod replicas and details about the horizontal Pod autoscaler.
2. Click the **Revision History** tab. This displays a list of the revisions that have been made to this workload.
3. Click the **Events** tab. This tab lists events associated with this workload.
4. And then the **YAML** tab. This tab provides the complete YAML file that defines these components and full configuration of this sample workload.
5. Still in the Google Cloud Console's **Details** tab for the **nginx-1** workload, click the **Overview** tab, scroll down to the **Managed Pods** section and click the name of one of the Pods to view the details page for that Pod.
6. The Pod details page provides information on the Pod configuration and resource utilization and the node where the Pod is running.
7. In the **Pod details** page, you can click the Events and Logs tabs to view event details and links to container logs in Cloud Operations.
8. Click the **YAML** tab to view the detailed YAML file for the Pod configuration.
