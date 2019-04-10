---
layout: post
title:  "Working With Curls"
date:   2019-04-10 09:01:00 +0530
categories: Linux
---
CURL is both a library and a command line utility written to handle the transfer of data using many different protocols. It is scriptable and extremely versatile but this makes it quite complicated.

before using curl as wget is more user-friendly in most cases. However, for more complex operations you cannot beat cURL. It has over 100 different command line options many of which can be used in combinations. It is very powerful and can even handle cookies, forms and ssl. However it can also be used for some very simple tasks that you will find useful. In this tutorial we will concentrate on the things that cURL can do that wget can’t.


Lets get started!!!

## The Basics

At its most basic you can use cURL to download a file from a remote server. To download the homepage of example.com you would use curl example.com. cURL can use many different protocols but defaults to HTTP if none is provided. It will, however, try other protocols as well and it can intelligently guess which protocol to use if hints are given. For instance, if you use curl ftp.example.com it will automatically try the FTP:// protocol.

If however you want to help cURL to choose the right protocol then prefix the url with the protocol such as c

Step 1
{% highlight ruby %}

curl http://example.com or curl ftp://example.com.

{% endhighlight %}

## Setting the output file

If you want to give the downloaded file a different name you would use the -o option. For example.

{% highlight ruby %}
curl -o filename.tar.gz http://filename-4.0.1.tar.gz
{% endhighlight %}

## Viewing the complete request and response

Quite often when learning curl you will either get an unexpected output or no output at all. The -v option is very useful in these situations. The -v option displays all the information in the request sent to the remote server and the response it receives.

## Saving a 301-redirected file


{% highlight ruby %}
If a site has WordPress® installed for example and they are using 301 redirects you will by default download the redirect response only. To ensure you follow the redirects and get the final file you will need to use the -L option. If you try curl google.com you will just get the redirect page, if you now try curl -L google.com you will get the page you were after.
{% endhighlight %}

## Nothing returned

{% highlight ruby %}
If you use curl and don’t get any return or an error you can try the -v option. This will show all the headers. The header may have a 301 redirect code in it but no body to display. If this is the case you can use the -L option to follow the redirect.

Those are the basics of cURL. We will now move on to the intermediate levels of cURL usage.


{% endhighlight %}


## Viewing only the response headers for debugging


{% highlight ruby %}
When you are writing a script using cURL sometimes you will want to view the response headers only without seeing the data or the request. Having a clean view of what is happening, without all the data to obscure things, can be helpful with debugging. To do this you would use the -I option. For instance in the previous example with Google® we could use curl -I google.com
{% endhighlight %}


## Skipping SSL checks

{% highlight ruby %}
When connecting to a remote server that has a self signed certificate you will want to skip the ssl checks. To do this use the -k option. For example curl -k https://google.com
{% endhighlight %}

## Setting the user agent

{% highlight ruby %}
The -A option allows you to set the user agent. For example curl -A "Mozilla/5.0 (Windows NT 6.3; WOW64; rv:40.0) Gecko/20100101 Firefox/40.0" -L google.com.

{% endhighlight %}

## Rate Limiting
{% highlight ruby %}
To avoid hitting the remote server hard you can limit the download rate you will use. The command to do this is --limit-rate and use like this --limit-rate 100k
{% endhighlight %}

## FTP Login

{% highlight ruby %}
To set the username and password you can use the –user username:password option.

{% endhighlight %}

## FTP upload and download

{% highlight ruby %}
To download you just need to use the basic curl command but add your username and password like this curl --user username:password -o filename.tar.gz ftp://domain.com/directory/filename.tar.gz .

To upload you need to use both the –user option and the -T option as follows.
curl --user username:password -T filename.tar.g ftp://domain.com/directory/

To delete a file from the remote server.
curl --user username:password -X 'DELE filename.tar.gz' ftp://domain.com/
{% endhighlight %}

## Sending POST requests and different FTP Commands

{% highlight ruby %}
The -X command allows you to send custom commands to the receiving server. For HTTP this could be a POST request or WebDAV’s copy or move. For FTP you can use the -X option to send other commands instead of the default file LIST, like in the previous section's example of using -X to send the DELE command to an FTP server. However, this can also be used to send full POST data to an HTTP server.

If the page you wanted to POST to had a form like this:
{% endhighlight %}

{% highlight ruby %}
<form action="test.php" method="POST">
  <input name="Name" type="text" />
  <input name="button1" type="submit" value="OK" />
</form>
you could submit the form request using curl -X POST --data "name=barrym&button1=OK" http://www.example.com/test.php.
{% endhighlight %}

## Using Cookies


{% highlight ruby %}
If the server you are connecting to requires a cookie then you can send it using curl -b cookiefile.txt http://example.com
{% endhighlight %}

## Sending custom headers

{% highlight ruby %}
If you need to send a custom header to the server you would use the -H option like this
curl -H "Accept: text/html" http://domain.com. Which would set the content type to text/html
{% endhighlight %}


## Verifying an SSL Certificate

{% highlight ruby %}
If you want to verify that your SSL cert is valid without using your browser and run into potential caching issues then use curl --cacert mycert.crt https://domain.com. This is also useful if you need to validate the connection to ensure that you are connecting to the right server.

The certificate must be in PEM format. If the optional password is not specified, it will be queried for on the terminal. Note that this option assumes a “certificate” file that is the private key and the private certificate concatenated.

{% endhighlight %}

## Limiting the connection timeout time

{% highlight ruby %}
Sometimes you will want the connection to time out quickly if it can’t make the connection within a certain time frame. The option to use to do this is –connect-timeout. This only affects the connection time so once you are connected it no longer applies. curl --connect-timeout 5 http://domain.com
{% endhighlight %}


## Finding out more in Curls

{% highlight ruby %}
As stated in the introduction there are over 100 command line options for cURL so we have just covered some of the most commonly used ones in our experiences. cURL can do a lot more than described above and man curl is a good place to start to find out more. If you prefer a web-based reference then http://curl.haxx.se/docs/faq.html is the authoritative one.

{% endhighlight %}

http://curl.haxx.se/docs/faq.html
