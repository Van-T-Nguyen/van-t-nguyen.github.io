<h2> Creating a droplet and installing Docker and Wireguard </h2>

<ol>
  <li>First, I created a Digital Ocean account using the link given in the slides </li>
  <li>I then createed a droplet to the specifications in the slides.</li>
  <li>I installed docker using the instructions listed on this page: https://thematrix.dev/install-docker-and-docker-compose-on-ubuntu-20-04/</li>
  <li>I downloaded some preperatory resources for docker via "sudo apt install apt-transport-https ca-certificates curl software-properties-common -y"</li>
  <li>I then added the docker key via "curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -"</li>
  <li>I then added a docker repo for my OS via sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
    stable"" and switched to it via "apt-cache policy docker-ce"</li>
  <li>Finally, I installed docker via "sudo apt install docker-ce -y"</li>
  <li>I then got docker compose "sudo curl -L "https://github.com/docker/compose/releases/download/1.27.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose"</li>
  <li>After the docker stuff was done, I then setup the wireguard directory things "mkdir -p ~/wireguard/
mkdir -p ~/wireguard/config/
    nano ~/wireguard/docker-compose.yml" and changed directories "cd ~/wireguard/"</li>
  <li>I then filled out the docker-compose file by copying out the template and altering it to change the timezone to Chicago, changing the IP address to my droplet's, and trying to complete the bonus by adding "- 80:51820/udp" under the ports section.</li>
  <li>I then started up wireguard via the container using "docker-compose up -d"</li>
  <li>I then created a QR code to connect my phone to the VPN via "docker-compose logs -f wireguard"</li>
</ol>
  
<h2> Connecting on Phone and PC </h2>
<ol>
  <li>I installed wireguard onto my phone and PC and collected screenshots of my current IP via ipleaks.net on both</li>
  <li>I then connected to my VPN on phone via the QR code I created earlier and collected further screenshots of my IP and wireguard in use</li>
  <li>I went to the pc1 .conf file in the droplet and copied it onto my main pc and connected to my VPN on my PC</li>
  <li>Finally, I collected the final screenshots and finished.</li>
</ol>
  
<h2> Phone Screenshots (Regular IP first)</h2>
<img src="https://user-images.githubusercontent.com/46911024/141006493-133fab50-34f7-4020-8c3f-a70de262e75e.png">
<img src="https://user-images.githubusercontent.com/46911024/141006508-c04f883a-673b-40a4-9358-d065bb816403.png">
<img src="https://user-images.githubusercontent.com/46911024/141006516-846c2a04-4c6f-4f20-bbd8-61e7d539fb31.png">

<h2> PC Screenshots (Regular IP first)</h2>
<img src="https://user-images.githubusercontent.com/46911024/141006493-133fab50-34f7-4020-8c3f-a70de262e75e.png">
<img src="https://user-images.githubusercontent.com/46911024/141006508-c04f883a-673b-40a4-9358-d065bb816403.png">
<img src="https://user-images.githubusercontent.com/46911024/141006516-846c2a04-4c6f-4f20-bbd8-61e7d539fb31.png">
  
  <h2> Docker Compose Code Block </h2>
<img src="https://user-images.githubusercontent.com/46911024/142059638-638c0fcc-d5f7-43b7-acea-dd3fe6785571.png">