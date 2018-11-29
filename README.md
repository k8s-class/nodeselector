# Nodeselector

### How to use node labels to assign workloads to specific worker nodes

```
  $ kubectl get nodes
  
  *** Make sure you grab a worker node not a master node.

  $ kubectl label nodes ip-172-20-42-175.ec2.internal hardware=high-resources
  node "ip-172-20-42-175.ec2.internal" labeled

  $ kubectl label nodes ip-172-20-61-12.ec2.internal hardware=low-resources
  node "ip-172-20-61-12.ec2.internal" labeled

  Now I will go into a current deployment and to add the nodeSelector and set it to high-resources or, you can create a new deployment.

  $ kubectl edit deployment helloworld-deployment

  find the line that says spec: and then go down to the line that says dnsPolicy: ClusterFirst and under that add a stanza that    says nodeSelector: hardware:high-resources

  This will move the containers to the host specified with the label high-resources.
  ```
```Events:
  Type    Reason     Age   From                             Message
  ----    ------     ----  ----                             -------
  Normal  Scheduled  15m   default-scheduler                Successfully assigned default/helloworld-deployment-nodeselector-5b6df795c8-52v5k to aks-default-24143415-1
  Normal  Pulling    15m   kubelet, aks-default-24143415-1  pulling image "buildmystartup/basicnodeapp:2"
  Normal  Pulled     15m   kubelet, aks-default-24143415-1  Successfully pulled image "buildmystartup/basicnodeapp:2"
  Normal  Created    15m   kubelet, aks-default-24143415-1  Created container
  Normal  Started    14m   kubelet, aks-default-24143415-1  Started container
```
