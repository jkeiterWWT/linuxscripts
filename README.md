🛠️ How to Use
Save the Script: Copy the above script into a file named install_k8s.sh.​

Make it Executable: Run the following command to make the script executable:​

bash
Copy
Edit
chmod +x install_k8s.sh
Execute the Script: Run the script with root privileges:​

bash
Copy
Edit
sudo ./install_k8s.sh
Initialize the Control Plane: On the control plane node, initialize the cluster:​
CyberPanel
+3
GitHub
+3
Medium
+3

bash
Copy
Edit
sudo kubeadm init --pod-network-cidr=192.168.0.0/16
Set Up kubeconfig: Configure kubectl for the current user:​
CyberPanel

bash
Copy
Edit
mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config
Install a CNI Plugin: Deploy a Container Network Interface (CNI) plugin like Calico:​
CyberPanel
+1
Medium
+1

bash
Copy
Edit
kubectl apply -f https://raw.githubusercontent.com/projectcalico/calico/v3.25.0/manifests/calico.yaml
Join Worker Nodes: On the control plane node, generate the join command:​
Medium
+2
CyberPanel
+2
GitHub
+2

bash
Copy
Edit
kubeadm token create --print-join-command
Execute the generated command on each worker node to join them to the cluster.
