# SysAdminDocker
This is the Docker project from my System Administration course

# Install Docker
1. `sudo apt update`
2. `sudo apt install docker.io`
3. `sudo apt install curl`
4. `sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose`
5. `sudo chmod +x /usr/local/bin/docker-compose`

    1.  Test it with `docker-compose --version`

# Install OpenVAS/Greenbone vulnerability scanner
6. `sudo docker run -d -p 443:443 --name openvas mikesplain/openvas`
7. Wait for it to finish recieving NVTs
    1. Open system monitor, and wait for the CPU usage to go down

# Start using OpenVAS
8. Open a web browser and go to `https://localhost/`
    - Username: `admin`
    - Password: `admin`

9. Run a scan
    - Go to Configuration -> Targets
    - Click the star to create a new target
    - Set it up accordingly (I used 127.0.0.1) and called it "Local"
    - Go to Scans -> Tasks
    - Click the star button to create a new task
      - Set up the task according ot what you need (I called it Local Scan, and it scanned my Local targets, and everything else was default)
    - Click the start button next to the task to make the task start
# Results
![image](https://user-images.githubusercontent.com/72999136/142086378-50bf3910-f304-475e-9646-07ba474bc7db.png)

# YAML File 
        `version: '3.3'

        services:

            openvas:

                ports:

                    - '443:443'

                container_name: openvas

                image: mikesplain/openvas`
