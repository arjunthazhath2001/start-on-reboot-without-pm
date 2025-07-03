# start-on-reboot-without-pm
Template of a service file that systemd (daemon) use to start a process/application automatically on default without any manual intervention post a reboot or crash of a server. PM2 not required if systemd takes care fo application restart upon reboot

[Unit]
Description=MsgMe Node.js Backend
After=network-online.target
Wants=network-online.target

[Service]
Environment=NODE_PORT=4000
EnvironmentFile=/home/ubuntu/msgme.com/.env
WorkingDirectory=/home/ubuntu/msgme.com
ExecStart=/home/ubuntu/.nvm/versions/node/v16.20.2/bin/node server.js
Restart=always
RestartSec=10
User=ubuntu
Group=ubuntu

[Install]
WantedBy=multi-user.target
