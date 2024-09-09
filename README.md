## **AWX Installation Guide**
### **1. Set Up the Kubernetes Environment**
##### Install Helm (if not already installed)
- curl <https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3> | bash
- Add the AWX Operator Helm Repository
- `helm repo add awx-operator <https://ansible.github.io/awx-operator/>`
- `helm repo update`
### **2. Deploy the AWX Operator**
- Create a Namespace for AWX:
`kubectl create namespace awx`
- Install the AWX Operator:
`helm install awx-operator awx-operator/awx-operator -n awx`
- Verify the AWX Operator Installation:
`kubectl get pods -n awx`
### **3. Deploy AWX Instance**
- Create an `awx.yaml`  file to define the AWX instance
- Apply the file: 
`kubectl apply -f awx.yaml`
### **4. Expose AWX Web Interface**
If you're using Nginx Ingress Controller, here's how to expose the AWX service
Create an Ingress Resource
- Deploy Ingress Resource: 
`kubectl apply -f awx-ingress.yaml`