# 300 - Gateway Service

Based on "Manage NGINX configurations inside Docker container" at https://dev.to/kutsyk/manage-nginx-configurations-inside-docker-container-9da

Based on "Virtual Hosts on NGinX" at https://gist.github.com/soheilhy/8b94347ff8336d971ad0

When hosting our web applications, we often have one public IP address (i.e., an IP address visible to the outside world) using which we want to host multiple web apps. For example, one may wants to host three different web apps respectively for example1.com, example2.com, and example1.com/images on the same machine using a single IP address.

How can we do that? Well, the good news is Internet browsers send the domain name inside HTTP requests and all we need to do is to parse the requested domain name and URL and then route the HTTP request to the actual web server.

Oh, do I really need to parse HTTP requests? You can if you really want to, but there are lots of tools and technologies that readily do this for you. In this tutorial, we walk you through how you can use nginx to proxy multiple web applications.

## 100 - Install NGinX

To Do: ...

## 200 - Configure NGinX

### Step 1 -- Booting Servers for Virtual Hosts

Write three different node applications running on different ports (say 8080, 8181, 8282) on your machine.

### Step 2 -- Configure NGinX's Port

To do so, you need to edit your ```nginx``` config file.

In the config file, find the server section:

```
server {
    listen       80;
    ...
    location / {
       ...
    }
    ...
}
```
containers/app/gateway/nginx/nginx.conf.development

If you're using CDF, make sure you change 80 to a vacant port number (ask for one from your instructor). If not, you can keep using 80 or change the port if you will.

Test nginx

1. Run ```./nginx``` on CDF, or run ```sudo nginx``` on your local machine.
2. Open the browser and log on to ```localhost:$PORT``` (replace $PORT with the port number you configured for nginx).

### Step 3 -- Configure /

Let say we want to configure ```nginx``` to route requests for ```/```, ```/company-purpose```, ```/bpm/modeler```,```/chat/chat``` and ```/cms/cms```, respectively onto localhost:3000, localhost:8181, localhost:8182, and localhost:8281.

```
                  +--- host --------> node.js on localhost:3000
                  |
users --> nginx --|--- host/company-purpose ---> node.js on localhost:8181
                  |
                  +--- host/bpm/modeler ---> node.js on localhost:8182
                  |
                  +--- host/chat/chat ---> node.js on localhost:8281
                  |
                  +--- host/cms/cms ---> node.js on localhost:8281                            
``` 

To route ```/```, you need to edit your ```nginx``` config file.

In the config file, find the ```server``` section:

```
server {
    listen       80;
    ...
    location / {
       ...
    }
    ...
}
```
containers/app/gateway/nginx/nginx.conf.development

This section is simply telling ```nginx``` how it should serve HTTP requests.

Now, change the location section to this snippet:

```
server {
    listen       80;
    ...
    location / {
        proxy_pass http://127.0.0.1:3000;
    }
    ...
}
```
containers/app/gateway/nginx/nginx.conf.development

```proxy_pass``` simply tells nginx to forward requests to ```/``` to the server listening on http://127.0.0.1:3000.

More ...
