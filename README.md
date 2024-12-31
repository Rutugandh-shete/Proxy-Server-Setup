# Proxy-Setup
## What is Proxy-server?
**It is intermediatary between client and server. There are 2 types of proxy server 1. *Forward proxy* server and 2. *Reverse proxy server***
![image](https://github.com/user-attachments/assets/821bd24a-5485-4cd3-8600-6e3d0409c2d8)

# Proxy Servers: Forward and Reverse

## **Forward Proxy**
A forward proxy is a server that acts as an intermediary for requests from a client to the internet or external services. It is primarily used to manage and control client-side requests.

### **Use Cases**
- **Anonymity:** Hides the client’s IP address from external servers.
- **Content Filtering:** Blocks access to restricted or unwanted websites.
- **Caching:** Reduces latency by storing frequently accessed content locally.
- **Security:** Protects internal clients from external threats.

### **How It Works**
Client → Forward Proxy → Internet/External Service

---

## **Reverse Proxy**
A reverse proxy is a server that sits in front of one or more backend servers and forwards client requests to them. It is mainly used to enhance server-side operations.

### **Use Cases**
- **Load Balancing:** Distributes client requests across multiple servers to optimize resource usage.
- **Security:** Hides backend servers’ IP addresses and adds an extra layer of protection.
- **SSL Termination:** Manages SSL encryption and decryption.
- **Caching:** Reduces server load by serving cached responses.
- **Compression:** Improves response delivery speeds by compressing content.

### **How It Works**
Client → Reverse Proxy → Backend Server(s)

## **Examples**
### **Forward Proxy Example**
- A corporate network using a forward proxy to restrict access to social media websites.

### **Reverse Proxy Example**
- A website using Nginx as a reverse proxy to distribute traffic between multiple application servers.

---

## **Common Tools**
- **Forward Proxy:** Squid, HAProxy, SOCKS Proxy
- **Reverse Proxy:** Nginx, Apache, AWS Elastic Load Balancer



