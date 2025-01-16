# trivy
# Installation docker (if installed not do this step)
```
sudo apt-get update -y
sudo apt-get install docker.io -y
service docker restart
sudo usermod -aG docker $USER
newgrp docker
```
# Installation of trivy 
```
sudo apt-get install wget apt-transport-https gnupg lsb-release
wget -qO - https://aquasecurity.github.io/trivy-repo/deb/public.key | gpg --dearmor | sudo tee /usr/share/keyrings/trivy.gpg > /dev/null
echo "deb [signed-by=/usr/share/keyrings/trivy.gpg] https://aquasecurity.github.io/trivy-repo/deb $(lsb_release -sc) main" | sudo tee -a /etc/apt/sources.list.d/trivy.list
sudo apt-get update
sudo apt-get install trivy
```
# trivy help : 
trivy image imagename </br>

trivy fs --security-checks vuln,config   Folder_name_OR_Path  </br></br>

trivy image --severity HIGH,CRITICAL image_name  </br></br>

trivy image -f json -o results.json image_name  </br></br>
cat result.json|jq </br></br>

trivy repo repo-url  </br></br>

trivy k8s --report summary cluster  </br></br>
* Test 1
```
docker pull nginx
```
```
trivy image nginx
```
* Test 2
```
mkdir aditya
cd aditya
```
```
git clone https://github.com/jacob-bd/kubeturbo-sample-yamls.git
```
```
trivy fs --security-cheks vuln, config kubeturbo-sample-yamls
```
* Test 3
```
trivy image -f json -o results.json nginx
```
