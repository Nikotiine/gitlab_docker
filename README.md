# GIT LAB - DOCKER

### Pre requis
* Docker engine > V3
* Docker compose > V2
* 4Go d'espace libre

## installation
```bash
docker-compose up -d
```

Laisser le container se builder 

puis acceder a l'instance gitlab sur 
>localhost:8080

Recuperer le mdp root initial
```bash
docker exec -it gitlab-ce grep 'Password:' /etc/gitlab/initial_root_password
```
Se connecter avec les identifiants
* username= root
* password  = le resultat de la derniere ligne de commande
* pensez a changer le mdp

### alternative pour le mot de passe
```bash
sudo docker exec -it gitlab-ce bash 
gitlab-rails console -e production
user = User.where(id: 1).first
user.password = 'secret_pass'
user.password_confirmation = 'secret_pass'
user.save!
exit
exit
```
### Configuration 
Le docker-compose est prevu pour tourner sur Macos ARM64
pour une utilisation sur AMD86 changer la ligne 4
>  image: 'yrzr/gitlab-ce-arm64v8'

par

> image: 'gitlab/gitlab-ee'
# gitlab_docker
