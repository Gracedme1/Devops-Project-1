1. We would be making use of minkube to run our kubernetes commands
2. Open Powershell
3. Ensure your docker desktop is running
    - Ensure that your minikube is installed and you have to start it with docker with this command
 - ` minikube start --driver=docker`
![kub](1.PNG)
4. Check the verion of your application and also the nodes with this commands
    - kubectl version
    - kubectl get nodes
5. also create deployment by this command
    - `kubectl create deployment kubernets-bootcamp`
6. To view and decsribe your deployment, run this commands:
    - `kubectl get deployment`
    - `kubectl describe deployment kubernetes-bootcamp`
![kub](2.PNG)
![kub](3.PNG)
7. check your docker desktop dashboard
![kub](4.PNG)
8. We can also check our pods, logs and have access to the container either to modify or do other changes by running these commands:
    - `kubectl get pods`
    -  `kubectl describe pods`
    - `kubectl logs kubernetes-bootcamp-container id`
    - `kubectl exec kubernetes-bootcmap-container id`
![kub](6.PNG)
![kub](8.PNG)
9. We expose our application to the public
    - `kubectl expose deployment/kubernetes-bootcamp --type="NodePort" --port 8080`
![kub](9.PNG)
10. Also access the services running on clusters
    - `kubectl get services`
![kub](10.PNG)
11. check your labes and describe and delete your pods
![kub](11.PNG)
![kub](12.PNG)
12. scale your deployment to 6 replicas
![kub](13.PNG)
![kub](14.PNG)
13. Update to version 4
    - `kubectl set image deployments/kubernetes-bootcamp kubernetes-bootcamp=jocatalin/kubernetes-bootcamp:v4`
![kub](15.PNG)
    # Done
