# Web Proxy 
This project provides a simple way to set up and run [PHP-Proxy](https://www.php-proxy.com) inside a [Docker container](https://docs.docker.com/language/php/).

![Homepage Screenshot](assets/screenshot.png "Homepage Preview")

## Prerequisites
- Install [Docker](https://docs.docker.com/desktop/setup/install/linux/) on your machine.

## Installation steps 
Follow these steps to tinker with the proxy locally: 
1. Clone or download this project repository.
2. From the project directory run `docker compose up --build ---watch`.
3. Navigate to: http://localhost:9000/index.php?q=https://old.reddit.com
Changes made in the `src` directory will automatically sync with the running container.

## Known limitations
- Works best with simple, JavaScript-free versions of websites, (e.g., https://old.reddit.com)
- old.reddit.com doesn't support media content and redirects to the new version of the website for such requests.

## Exporting for Deployment to PHP Hosting
To deploy PHP-Proxy files to a PHP hosting service:

1. Find the running container's ID or name:
   ```bash
   docker ps
   ```

2. Copy the `/var/www/html` directory from the container to your local machine:
   ```bash
   docker cp <CONTAINER_ID>:/var/www/html ./php-proxy-files
   ```

3. Create a tarball of the files (optional, for easier deployment):
   ```bash
    tar -cvzf php-proxy-files.tar.gz php-proxy-files
   ```

3. Upload the `php-proxy-files.tar.gz` folder to a hosting service that supports:
   - **PHP 8.x**
   - **cURL**
