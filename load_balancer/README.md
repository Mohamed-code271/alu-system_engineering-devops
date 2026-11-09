# 0x0F. Load balancer

This project doubles the number of web servers behind a load balancer and uses HAProxy to distribute traffic between them using a round-robin algorithm.

## Requirements

- Ubuntu servers: `web-01`, `web-02` and `lb-01`
- Hostnames set to `[STUDENT_ID]-web-01` and `[STUDENT_ID]-web-02`
- All Bash scripts are executable and pass `shellcheck`

## Tasks

### 0. Double the number of webservers
Configures `web-02` to be identical to `web-01` and adds a custom Nginx response header on both servers.

- Header name: `X-Served-By`
- Header value: the hostname of the server Nginx is running on
- File: [0-custom_http_response_header](./0-custom_http_response_header)

### 1. Install your load balancer
Installs and configures HAProxy on `lb-01` to send traffic to `web-01` and `web-02`.

- Distributes requests using a round-robin algorithm
- HAProxy can be managed via an init script
- File: [1-install_load_balancer](./1-install_load_balancer)

## Usage

Run on web-01 and web-02:

    sudo ./0-custom_http_response_header

Run on lb-01:

    sudo ./1-install_load_balancer

Test (the header should alternate between web-01 and web-02):

    curl -sI <lb-01-IP> | grep X-Served-By

## Author

Abdikarim
