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


# Practical 
### 1. Launch 2 instances first instance which will act as reverse proxy server and best example for reverse proxy server is "Nginx" and second instance will be used for our "website".
**First instance**
![image](https://github.com/user-attachments/assets/fb2c0185-62fb-4d50-a7f6-fbc01ed886ab)
 **second instance**
 ![image](https://github.com/user-attachments/assets/fcd043ca-f56b-421d-a8ee-5cf85cdd6ebe)

 ### 2. Install nginx on first instance.
 ![image](https://github.com/user-attachments/assets/b7fd8cc4-eb7b-4a3f-ac75-6f90670ab556)
 ### 3. Install apache in second instance.
 ![image](https://github.com/user-attachments/assets/4348bac7-e8f8-4186-be40-68ec2afdf218)
 ### 4. In first instance enter into directory "/etc/nginx/sites-enabled" edit default and enter below block
 ### 5. Create reverse proxy file in /etc/nginx/sites-available/reverse-proxy
````
sudo vim /etc/nginx/sites-available/reverse-proxy

````
**Add this code below and add public/private main frontend code**

 ````
server {
    listen 80;
    server_name _;

    location / {
        proxy_pass http://<private-ip of instance-2>;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
````
### 6. Add this reverse-proxy file to sites-enabled from sites-available because where nginx configurations are stored but not active and remove default file from sites-enabled
````
sudo ln -s /etc/nginx/sites-available/reverse-proxy /etc/nginx/sites-enabled

````
### Output
**Proxy setup**
![alt text](image.png)
**Main frontend**
![alt text](image-1.png)



