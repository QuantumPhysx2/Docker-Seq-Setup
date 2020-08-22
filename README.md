# Docker-Seq-Setup

<h1>How to setup Docker to run Seq for Serilog logging</h1>
<h2>Requirements</h2>
<ul>
  <li><a href="https://docs.docker.com/docker-for-windows/install/">Docker (Windows)</a>. Be sure to keep the 'WSL2' option ticked during installation. If you don't, you may run into issues when attempting to run Docker after installation which will require you to Powershell and enabling a Hyper-V service using a specific command (or by manually turning it on via the Windows Interface).</li>
</ul>
<br />
<p>Next, go to <a href="https://hub.docker.com/r/datalust/seq">this source</a> and open up CMD.</p>
<p>Insert this command: <code>docker run --name seq -d --restart unless-stopped -e ACCEPT_EULA=Y -p 7000:80 datalust/seq:latest</code>.</p>
<p>Unless you've ran the above command before, you will most likely get a warning 'Unable to find image 'datalust/seq:latest' locally'. This is because the seq package for Docker on your system has not been downloaded prior. Thus, it has to asynchronously fetch and download the needed packages for seq to be functional. After waiting for it to finish, you can now close the CMD window.</p>
<p>Now, open up the Docker application. You should see a dedicated tab for 'seq' running on Port 7000 (note: the port can be to your liking). Click on the respective tab. You should now see a CMD terminal which details the current run-time status of the seq service. You can also inspect the system utilisation of the service itself which is pretty neat (this can be changed in the Docker app itself).</p>
<p>Open up your browser of choice and go to 'localhost:7000'. It should open a locally hosted instance of seq. This will be important in liking ASP.NET Core Serilog to your application for logging.</p>
<p>Much like XAMPP, if you close out of Docker entirely and try to browse localhost:7000 again, you will get nothing. So don't close it unless intentional.</p>
<p><b>By taking the Docker approach, we don't need to install the Seq onto our system, allowing us to minimise the amount of software on the (eventually) dedicated system.</b></p>
<br />
<h2>Self Notes</h2>
<p>Docker is essentially XAMPP/WAMP/LAMP, except that it contains a lot more useful features and is not restricted to serving PHP and MySQL related applications (phpmyadmin).</p>
<p>It is also fairly customisable in that you can specify how much dedicated system resources you want to allocate to the Docker program.</p>
<p>The locally hosted version of seq is not all that useful. For seq to be really effective, you will need to setup a dedicated system to monitor the logs (i.e. a VM or if possible, a physical machine).</p>
