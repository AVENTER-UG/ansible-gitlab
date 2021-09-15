# Ansible script to install gitlab

This Ansible playbook will populate a gitlab service with self signed SSL, REDIS, Postgresql, Container Repository and
serveral gitlab runners.


## 1) Install Gitlab, Redis, Postgresql, SSL Certificate

```bash
    ansible-playbook -i ../inventory/inventory/gitlab plays/server-config.yaml --tags gitlab
```

## 2) Install Gitlab Runner

```bash
    ansible-playbook -i ../inventory/inventory/gitlab plays/server-config.yaml --tags runner
```

## 3) Install Docker Repo SSL Certificate on client

Because of the fact that we are using a self signed SSL certificate, we have to install the Root CA on every 
Docker client.

```bash
    ansible-playbook -i ../inventory/inventory/<INVENTORY> plays/server-config.yaml --tags dockerssl
```

## Optional) Create only SSL Certificate (will not overwrite)

```bash
    ansible-playbook -i ../inventory/inventory/gitlab plays/server-config.yaml --tags ssl
```

## Optional) Install Trivy

```bash
    ansible-playbook -i ../inventory/inventory/gitlab plays/server-config.yaml --tags trivy
```



