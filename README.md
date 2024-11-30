In Django, by default, the development server runs on the IP address 127.0.0.1 (localhost) and port 8000. To change the IP address and port the server runs on, you can use the following steps:

### Steps to Change IP Address and Port
Modify the runserver Command
Use the runserver management command with the desired IP address and port as arguments.

```bash
python manage.py runserver <ip_address>:<port>
```
Example:
To bind the server to 192.168.1.100 and port 8080:

```bash
python manage.py runserver 192.168.1.100:8080
```
This makes the server accessible on the specified IP within the network.

Default Port: If you don't specify a port, Django uses port 8000.

Use 0.0.0.0 to Bind to All Interfaces
If you want the Django server to be accessible from any device on the network, bind it to 0.0.0.0.

```bash
python manage.py runserver 0.0.0.0:8000
```
This will make the server accessible via the IP address of the host machine on the local network.

Configure ALLOWED_HOSTS
By default, Django restricts access to the server to avoid potential security risks. To allow connections from specific IPs:

Open your Django project’s settings file (settings.py).

Find the ALLOWED_HOSTS setting and add the allowed IPs or domains.

Example:

```python
ALLOWED_HOSTS = ['127.0.0.1', '192.168.1.100', '0.0.0.0']
```
Use '*' to allow all hosts (not recommended for production):
```python
ALLOWED_HOSTS = ['*']
```
Check Your Network Configuration
If you use a private IP like 192.168.x.x or 10.x.x.x, ensure the device is connected to the same network as other devices that need access. For public IPs, ensure proper port forwarding and firewall configuration.

Testing the Server
Once the server is running, test it:

On the same device:
```bash
curl http://<ip_address>:<port>
```
From another device on the same network, open a browser and navigate to:
```php
http://<host_ip>:<port>
```
### Example Command
To run the server on 192.168.1.50 at port 9000:

```bash
python manage.py runserver 192.168.1.50:9000
```
To bind to all interfaces on port 8000:

```bash
python manage.py runserver 0.0.0.0:8000
```
### Notes
This approach is meant for development only. For production, use a WSGI server like Gunicorn or uWSGI with a reverse proxy (e.g., Nginx).
Avoid exposing the development server (runserver) to the internet for security reasons.
