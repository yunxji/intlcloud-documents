## Operation Scenario

This documentation provides information on cluster scaling. You can scale TKE container clusters in two ways:

- [Manually adding/removing a node](#ManuallyAddAndRemove)
- [Automatically adding/removing a node via Auto Scaling](#AutomaticAddAndRemove)

## Prerequisites

You are logged in to the [TKE console](https://console.cloud.tencent.com/tke2).

## Directions

<span id="ManuallyAddAndRemove"></span>

### Manually Adding/Removing a Node
#### Creating a Node
For detailed directions, see [Creating a Node](https://intl.cloud.tencent.com/document/product/457/30652#createNode).
During the creation, you can configure the CVM instance and scale the cluster on the **CVM Configuration** page.

#### Adding an Existing Node
> - Currently, you can only add CVM instances in the same VPC.
>- If you add an existing node to the cluster, the OS of the CVM instance will be reinstalled.
> - If you add an existing node to the cluster, the CVM instance will be migrated to the project set for the cluster.
> - If you want to add a node with only one data disk to the cluster, you can choose whether to set a container directory. Setting a container directory will format the disk. If a CVM does not have data disks or has multiple data disks, you will not be able to set a container directory.

For detailed directions, see [Adding an Existing Node](https://intl.cloud.tencent.com/document/product/457/30652#addExistingNode).
During the adding process, you can configure the CVM instance you want to add to the cluster and scale the cluster on the **CVM Configuration** page.

#### Removing a Node
For detailed directions, see [Removing a Node](https://intl.cloud.tencent.com/document/product/457/30653).
<span id="AutomaticAddAndRemove"></span>

### Automatically Adding/Removing a Node via Auto Scaling
Cluster Autoscaler (CA) is an independent program that dynamically adjusts the number of nodes in a cluster to meet your needs. When there is any Pod in a cluster that cannot be scheduled due to a lack of resources, scaling out is automatically triggered to reduce your labor costs. When some other conditions are met (for example, there are idle nodes), scaling in is automatically triggered to reduce your resource costs.

#### Enabling CA
#### Creating a Scaling Group

1. <span id="step1">In the left sidebar, click **[Clusters](https://console.cloud.tencent.com/tke2/cluster?rid=4)** to enter the **Cluster Management** page.</span>
2. Click the ID/name of the cluster for which scaling groups need to be created, and enter its cluster management page as shown below:
![Management page](https://main.qcloudimg.com/raw/25229e1731c1a0c9dea51bb7603b39da.png)
3. In the left sidebar, select **Node Management** > **Scaling Groups** to enter the **Scaling group list** page.
4. Click **Create a scaling group**, you will see a pop-up window as shown below:
![Create a scaling group](https://main.qcloudimg.com/raw/06b5ceeaedd52d856b9ca81b03c0efd1.png)
5. Configure the scaling group based on your needs. The primary parameter information is as follows:
**Launch configuration**:
 - Name: user-defined name.
 - Creation Method: you can choose from **Select other model configurations** and **Select existing node model** based on your needs.
 - Instance Type: **Pay as you go**  billing method.
 - Model Configuration: please choose from the options based on your needs.
 - Login Method:
    - Set Password: please set a password as prompted.
    - SSH Key Pair: a key pair is a pair of parameters generated by an algorithm. Using a key pair to log in to a CVM is more secure than using regular passwords. For details, see [SSH Key](https://intl.cloud.tencent.com/document/product/213/6092).
     - Random Password: a password will be automatically generated and sent to you through an internal message.
 - Data Disk mounting: choose whether to select based on your needs.
 - Security Group: used to set the network access control for the CVM instance. Please select based on your needs. You can click **Create security group** to open other ports to the Internet.
 - Label: set a label for the scaling group. The label will be added to the nodes that are created during automatic scale-out to implement elastic scheduling policies for services.

   **Scaling Group Configurations**:
 - Supported Network: this is the cluster network by default and cannot be changed.
 - Supported Subnets: select based on your needs.
 - Number of Nodes: the limit to the number of nodes in the scaling group.
 - Retry policy: you can choose from **Instantly Retry** and **Retry with Incremented Intervals** based on your needs.
6. <span id="step6">Click **Submit** to complete creation.</span>
7. You can create multiple scaling groups by repeating [step 1](#step1) to [step 6](#step6).

> - You need to configure the `request` value of the containers under the service. With the `request` value, whether the resources in the cluster are sufficient can be assessed in order to decide whether to trigger automatic scale-out.
>- Do not directly modify the nodes that are in a scaling group.
> - All nodes in the same scaling group should have the same configuration (such as model and Label).
> - You can use PodDisruptionBudget to prevent a Pod from being deleted during scale-in.
> - Check whether the quota of the availability zone is large enough before setting the minimum/maximum number of nodes for a scaling group.
> - It is not recommended to enable monitoring metric-based auto scaling of nodes.
> - Deleting a scaling group will also terminate the CVM instances in it. Please be cautious when doing so.

#### Scaling-triggering Conditions
##### Scale-out Triggers
If there is any container Pod in a cluster that cannot be scheduled due to a lack of available resources, the auto scale-out policy will be triggered to scale out the node to run the Pod.
Whenever the Kubernetes scheduler cannot find a place to run a Pod, it will set the Pod's PodCondition to false and set the reason to **Unschedulable**. The CA program scans the cluster regularly to see if there are unschedulable Pods. If so, it will scale out the nodes to run the Pods.

##### Scale-in Conditions
If the proportion of both CPU and memory requests of all the Pods on a node is less than 50%, an attempt will be made to scale in the node. If any of the following conditions is met, the node cannot be scaled in until all the Pods on it can be scheduled to other nodes.
- You set strict PodDisruptionBudget for Pods on the node, and the PDB is not met.
- There are Pods under the Kube-system.
- On the node there are Pods that are not created by controllers such as Deployment, ReplicaSet, Job, or StatefulSet.
- There are Pods with local storage.
- There are Pods that cannot be scheduled to another node due to certain reasons.

## FAQs

For issues related to scaling, see [FAQs for Scaling](https://intl.cloud.tencent.com/document/product/457/31425).

