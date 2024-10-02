# Déployer Directus

## Etape 3 

### Configurer le service Directus 

#### Premier essai
```
echo "[Unit]
Description=Directus Service
Requires=sqlite.service
After=sqlite.service
[Service]
User=student
Group=student
Restart=always
WorkingDirectory=/var/www/directus.site
Environment=NODE_VERSION=18
ExecStart=/home/student/.nvm/nvm-exec npx -y directus start
[Install]
WantedBy=multi-user.target
" | sudo tee -a /etc/systemd/system/directus.service > /dev/null
```
![image](https://github.com/WendyAlverde/tips-WendyAlverde/assets/148342924/5fd2a8fd-92b8-49f9-83ae-d0cbe3808599)

#### Deuxième essai
```
echo "[Unit]
Description=Directus Service
Requires=sqlite
After=sqlite
[Service]
User=student
Group=student
Restart=always
WorkingDirectory=/var/www/directus.site
Environment=NODE_VERSION=18
ExecStart=/home/student/.nvm/nvm-exec npx -y directus start
[Install]
WantedBy=multi-user.target
" | sudo tee -a /etc/systemd/system/directus.service > /dev/null
```
![image](https://github.com/WendyAlverde/tips-WendyAlverde/assets/148342924/3550bdb8-7255-4df5-be80-b2654c767ec4)

#### Troisième essai
```
echo "[Unit]
Description=Directus Service
Requires=data.db
After=data.db
[Service]
User=student
Group=student
Restart=always
WorkingDirectory=/var/www/directus.site
Environment=NODE_VERSION=18
ExecStart=/home/student/.nvm/nvm-exec npx -y directus start
[Install]
WantedBy=multi-user.target
" | sudo tee -a /etc/systemd/system/directus.service > /dev/null
```
![image](https://github.com/WendyAlverde/tips-WendyAlverde/assets/148342924/40ce8eab-2c60-46a6-aba9-66b316e892f3)

#### Quatrième essai
```systemctl status directus.service```
![image](https://github.com/WendyAlverde/tips-WendyAlverde/assets/148342924/c6407d59-a6a7-4e4f-940c-fbc277ad3160)

