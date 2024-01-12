# Load Balancing with Nginx

## What is a Load Balancer?

A load balancer is a device or software application that distributes incoming network traffic across multiple servers. The primary purpose is to ensure that no single server becomes overwhelmed with too much traffic, improving the overall performance, availability, and reliability of the system.

## Using Nginx as a Load Balancer

Nginx is a versatile web server that can also act as a powerful load balancer. Below are examples of different types of load balancing configurations using Nginx.

### Round Robin Load Balancing

In this configuration, Nginx distributes incoming requests equally among the backend servers.

```nginx
http {
    upstream backend {
        server server1.example.com;
        server server2.example.com;
        server server3.example.com;
    }

    server {
        location / {
            proxy_pass http://backend;
        }
    }
}
