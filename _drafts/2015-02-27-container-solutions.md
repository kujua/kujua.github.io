---
layout: post
title: Container solutions - a trial
photo-front-url: /res/container_1504.jpg
photo-front-class: grid-image-wrapper
photo-credit: 1
photo-front-credit-link: flickr.com/photos/glynlowe
photo-front-credit: Glyn Lowe Photoworks
sortorder: 2015-04-24
date: 2015-04-24
ignoredate: 0
---

**The idea of containers is very compelling. We get rid of heavy virtual machines and just serve lightweight application files.**

For a training environment I wanted to have containers for database, web server and IDE. As far as I know it is not possible, or at least not easily possible, to run interactive user interfaces in Docker. So my idea was to have Vagrant as host for an IDE container and two Docker-containers for the services.

image: container architecture

I evaluated this setup on an OS X machine. First I installed boot2docker - this is a wrapper for a Linux virtual machine that actually can load the Docker containers and the runtime, because OS X can't load containers directly. Boot2docker also exists for Windows, but I have not tried it.
The installation went well. I started the application, which spawns a shell, and after a little waiting I had a Docker prompt and everything was working fine.
Installing Vagrant was eventless as well and I could run a Vagrant box without problems.

Now to the first test, running a docker container in Vagrant. I specified to run the hello-world container in a vagrantfile:

{% highlight ruby linenos %}
Vagrant.configure(2) do |config|
    config.vm.provider "docker" do |d|
      d.image = "hello-world"
      d.remains_running = false
    end
end
{% endhighlight %}

I got a little bit concerned when Vagrant was downloading boot2docker again, apparently a private version as their /docker version is private and not accessible outside of Vagrant. The hello-world container ran and exited and I tried a few times more. I also confirmed that my Docker installation was still working as well.

Time for a break, the computer went to sleep and when I re-started the machine all hell break loose. First I changed my vagrantfile to run two machines, one docker container, one Vagrant box.

{% highlight ruby linenos %}
Vagrant.configure(2) do |config|

  config.vm.define "hellodocker" do |hellodocker|
    hellodocker.vm.provider "docker" do |d|

  config.vm.define "db" do |db|
    db.vm.box = "mitchellh/boot2docker"
  end

end
{% endhighlight %}

The docker machine was never brought up. It told me something about "denied access" and trying to start several times did not change anything. The command *vagrant status* was hanging and *vagrant suspend* told me that the Docker provider does not support this command, which is probably a bug. I thought, restarting the machine would bring it back to a clean state. But that failed as well as uninstalling Vagrant and installing it again. In between I had to kill the VirtualBox headless process, because I could not install Vagrant.

My boot2docker installation did not work anymore as well. It could not bring up Docker.

At the end I uninstalled both Vagrant and boot2docker. Re-installing boot2docker at least brought back Docker on the machine.

At the end I am not sure what caused the problems. Was it the double installation? Was it the vagrantfile that brought the system into a faulty state? Is it the boot2docker configuration?

What concerns me most is that there was no way to get out of the mess, not even re-starting the machine. Vagrant seems to have some persistent cache that survives all events, good or bad.

Eventually I tried on a Ubuntu virtual machine. The installation went well without problems and I could run Docker containers with or without Vagrant. The next step is to mix them - have one Vagrant box for UI related applications and a few Docker containers for services, databases etc.
