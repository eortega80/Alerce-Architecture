### Passwords

Always use randomly generated passwords.

Don't store passwords in plain text supports. Don't commit passwords to a Git filesystem.

Use an appliance like [Vault by Hashicorp](https://www.vaultproject.io/) to manage secrets.

Not one single account should be shared between multiple users. Each user should have their own account on every system they need to use.

### Development

When developing apps, be aware of [OWASP's Top Ten Application Security Risks](https://owasp.org/www-project-top-ten/) in order to minimize risks and produce more secure code.

Using widely spread libraries will also mitigate the risks. When developing an application from scratch, you will need to think to security risks on top of your own logic; using libraries that already address these risks will reduce your efforts and the probability of wrong implementation.

**DevSecOps and Container security**

Container security is the process of implementing security tools and policies that will give you the assurance that everything in your container is running as intended. This includes protecting the infrastructure, the software delivery chain, runtime, and everything in between.
With this in mind, the process of securing containers is continuous. It should be integrated into your development process, automated to remove the number of manual touch points, and extended into the maintenance and operation of the underlying infrastructure. This means protecting your build pipeline container images and runtime host, platform, and application layers. Implementing security as part of the continuous delivery life cycle means your business will mitigate risk and reduce vulnerabilities across an ever-growing attack surface.

Vulnerability Advisor provides security management for IBM Cloud Container Registry, generating a security status report that includes suggested fixes and best practices.

When you add an image to a namespace, the image is automatically scanned by Vulnerability Advisor to detect security issues and potential vulnerabilities. If security issues are found, instructions are provided to help fix the reported vulnerability.

Any issues that are found by Vulnerability Advisor result in a verdict that indicates that it is not advisable to deploy this image. If you choose to deploy the image, any containers that are deployed from the image include known issues that might be used to attack or otherwise compromise the container. The verdict is adjusted based on any exemptions that you specified.

The following functions are available:

- Scans images for issues.
- Provides recommendations to secure configuration files for a subset of application types.
- Provides instructions about how to fix a reported vulnerable package or configuration issue in its reports.
- Applies exemptions to reports at an account, namespace, repository, or tag level to mark when issues that are flagged do not apply to your use case.


### Others

Although you should use firewalls and WAFs (Web Application Firewall), don't trust them: They're a single point of failure. Instead, make sure each and every component of your system is secure on its own.

On an application level, thoroughly log every login and action performed by a user.

**DDoS Attack preventions**

From a high level, a distributed denial-of-service (DDoS) attack is like a traffic jam clogging up a highway, preventing regular traffic from arriving at its desired destination.

A DDoS attack is a malicious attempt to disrupt the normal traffic of a server, service or network by overwhelming the target or its surrounding infrastructure with a flood of internet traffic. DDoS attacks achieve effectiveness by utilizing many compromised computer systems as sources of attack traffic.

IBM Cloud Internet Services is a set of edge network services for clients looking to secure their internet-facing applications from DDoS attacks, data theft and bot attacks, and for those clients needing to optimize their web applications, or ensure global responsiveness and the ongoing availability of their internet-facing applications.

### Segmentation/Isolation Best Practices

| **Security Feature** | **Description** |
| ---------------- | ----------- |
| **Limit the number of exposed apps** | By default, apps and services that run within the cluster are not reachable over the public internet. Through the use of ALB/NLB, apps can be exposed externally from the cluster on the public or private network.  When apps and services are private, leverage the built-in security features (Calico Policies) to assure secured communication between worker nodes and pods. To expose services and apps to the public internet, use OpenShift routes, or leverage the NLB and/or ALB mentioned earlier to securely services publicly available.                                                                                                        |
| **[Keep Worker Nodes Private](https://cloud.ibm.com/docs/openshift?topic=openshift-security#network_segmentation)** | Every cluster is automatically connected to a private VLAN. The private VLAN determines the private IP address that is assigned to a worker node. Keep worker nodes private by connecting them to a private VLAN only. In addition, the cluster master can be configured with a [private, public, or private and public endpoint](https://cloud.ibm.com/docs/openshift?topic=openshift-plan_clusters#workeruser-master). <br><br>**Attention**: Keep in mind that in order to communicate with the OpenShift master from a local machine and for Red Hat OpenShift on IBM Cloud to connect to IBM Cloud services that do not support a private service endpoint, public connectivity must be configured to [specific URLs and IP addresses](https://cloud.ibm.com/docs/openshift?topic=openshift-firewall#firewall_outbound). If the IBM Cloud services have a private service endpoint and the account is enabled for VRF, network traffic to and from these services is automatically routed over the private network and no public network connection is required. To set up public connectivity for cluster that is connected to a private VLAN only, there **are [two approaches](https://cloud.ibm.com/docs/containers?topic=containers-plan_clusters#gateway)**: <br><br>1. **Use a Gateway Appliance**, such as a [Virtual Router Appliance](https://cloud.ibm.com/docs/infrastructure/virtual-router-appliance?topic=virtual-router-appliance-about-the-vra), in front of the worker nodes and enable network traffic to these URLs and IP addresses. If a router appliance already exists, such as a [Virtual Router Appliance (VRA)](https://cloud.ibm.com/docs/infrastructure/virtual-router-appliance?topic=virtual-router-appliance-about-the-vra#about-the-vra), the newly added portable subnets from those VLANs that the cluster is connected to are not configured on the router.   To use NLBs or Ingress ALBs, ensure that network devices can route between different subnets on the same VLAN either through VLAN Spanning or that VRF is enabled on the account. <br><br>2. **[Use a Gateway Enabled Cluster](https://www.ibm.com/cloud/blog/announcements/ibm-cloud-kubernetes-service-gateway-enabled-clusters)** by creating a cluster that is connected to a public VLAN and a private VLAN and has an enabled gateway. The cluster is created with a compute worker pool of compute worker nodes that are connected to a private VLAN only, and a gateway worker pool of gateway worker nodes that are connected to public and private VLANs. Gateway worker nodes help you achieve network connectivity separation between the internet or an on-premises data center and the compute workload that runs in your cluster. |
| **Restrict Traffic to Edge Worker Nodes** | Every worker node is configured to accept app pods and associated load balancer or ingress pods. Label worker nodes as [edge nodes](https://cloud.ibm.com/docs/openshift?topic=openshift-edge#edge) to force load balancer and ingress pods to be deployed to these worker nodes only. In addition, [taint your worker nodes](https://cloud.ibm.com/docs/openshift?topic=openshift-edge#edge_workloads) so that app pods cannot schedule onto the edge nodes. With edge nodes, you can isolate the networking workload on fewer worker nodes in your cluster and keep other worker nodes in the cluster private.|