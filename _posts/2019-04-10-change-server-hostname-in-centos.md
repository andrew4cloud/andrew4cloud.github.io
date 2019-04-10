---
layout: post
title:  "Change a server's hostname in CentOS"
date:   2019-04-10 07:06:00 +0530
categories: Linux
---
By default, your server is started with the server’s given name as the hostname. Some software such as cPanel® requires a valid fully qualified domain name (FQDN) for the hostname to be used during their licensing verification system. This article describes how to change a server hostname in CentOS®.

Lets get started!!!

## Change a server’s hostname

Using a text editor, open the server’s /etc/sysconfig/network file. The following example shows how to open this file in the GNU nano text editor:

Step 1
{% highlight ruby %}

sudo nano /etc/sysconfig/network

{% endhighlight %}

Step 2

Modify the HOSTNAME= value to match your FQDN hostname, as shown in the following example:


{% highlight ruby %}

HOSTNAME=myserver.domain.com

{% endhighlight %}

Step 3

Open the file at /etc/hosts. To update the information for internal networking, change the host that is associated with the main IP address for your server, as shown in the following example:

{% highlight ruby %}

127.0.0.1      localhost localhost.localdomain

 123.45.67.89   hostname.domain.com   hostname

 ~

 ~

 ~

 ~

 -- INSERT --                         2,43-57    ALL
{% endhighlight %}


Step 4

Run the hostname command. This command enables you to change the hostname on the server that the command line remembers, but it does not actively update all of the programs that are running under the old hostname. The following code provides an example:

{% highlight ruby %}

[root@defiant ~]# hostnamectl set-hostname hostname.domain.com

 [root@defiant ~]# hostname

 hostname.domain.com

 [root@defiant ~]#

 {% endhighlight %}

Step 5

Use the following command to restart networking on your server to ensure that changes persist on restart:

{% highlight ruby %}

/etc/init.d/network restart

{% endhighlight %}
