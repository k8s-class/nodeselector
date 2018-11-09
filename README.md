# Nodeselector

### How to use node labels to assign workloads to specific nodes

```
  $ kubectl get nodes

  $ kubectl label nodes ip-172-20-42-175.ec2.internal hardware=high-resources
  node "ip-172-20-42-175.ec2.internal" labeled

  $ kubectl label nodes ip-172-20-61-12.ec2.internal hardware=low-resources
  node "ip-172-20-61-12.ec2.internal" labeled

  Now I will go into the deployment and edit it to add the nodeSelector and set it to high-resources

  $ kubectl edit deployment helloworld-deployment

  find the line that says spec: and then go down to the line that says dnsPolicy: ClusterFirst and under that add a stanza that    says nodeSelector: hardware:high-resources

  This will move the containers to the host specified with the label high-resources.
  ```
