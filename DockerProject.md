<h2> OpenVAS Docker Installation </h2>
<h6> Using the guide found at: https://utulsa.hosted.panopto.com/Panopto/Pages/Embed.aspx?id=75912983-0806-47a5-a3ad-acc9018aaec3 

<ol>
  <li>I first installed docker onto my Ubuntu VM using the steps in the slide: apt update, install docker.io, etc</li>
  <li>I then made sure that docker was properly installed and working via sudo service docker status.</li>
  <li>I then started up docker via sudo service docker start.</li>
  <li>I then began running openvas (from mikesplain/openvas) on port 443 via sudo docker run -d -p 443:443 --name openvas mikesplain/openvas</li>
  <li>Once openvas was installed, I logged into it at https://localhost/ via the credentials: admin | admin.</li>
  <li>Then it was just a matter of taking the screenshots of openvas in use</li>
</ol>
  
<h2> OpenVAS screenshots </h2>
<img src="https://user-images.githubusercontent.com/46911024/141006493-133fab50-34f7-4020-8c3f-a70de262e75e.png">
<img src="https://user-images.githubusercontent.com/46911024/141006508-c04f883a-673b-40a4-9358-d065bb816403.png">
<img src="https://user-images.githubusercontent.com/46911024/141006516-846c2a04-4c6f-4f20-bbd8-61e7d539fb31.png">
<img src="https://user-images.githubusercontent.com/46911024/141661101-2af24a94-3a66-457a-99cd-12012fa26437.png">
. 
