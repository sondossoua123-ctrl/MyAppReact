TP4 : Docker et Docker Compose (application MERN)



1.Liens :

\-GitHub : https://github.com/sondossoua123-ctrl/MyAppReact

\-Docker Hub (serveur) : https://hub.docker.com/r/sondossoua/mern-server

\-Docker Hub (client) : https://hub.docker.com/r/sondossoua/mern-client



2.Structure de projet :

MyAppReact contient :

\-client (React + Vite, Dockerfile)

\-server (Express, Dockerfile)

\-captures

\-docker-compose.yml

\-README.md

\-Jenkinsfile



3\. Les commandes utilisées :



3.1. Clonage du projet : git clone https://github.com/wiem-kb/MyAppReact.git

&#x20;                        cd MyAppReact



3.2. Dockerfile du serveur : docker build -t mern-server ./server



3.3. Dockerfile du client : docker build -t mern-client ./client



3.4. Réseau Docker et MongoDB : docker network create mern-network

&#x20;                               docker run -d --name mongodb --network mern-network mongo



3.5. Execution du serveur et du client : docker run -d --name server --network mern-network -p 9000:9000 mern-server

&#x20;                                        docker run -d --name client --network mern-network -p 3000:3000 mern-client

&#x20;                                        docker ps



3.6. Push sur Docker Hub : docker login

&#x20;                          docker tag mern-server sondossoua/mern-server:latest

&#x20;                          docker push sondossoua/mern-server:latest

&#x20;                          docker tag mern-client sondossoua/mern-client:latest

&#x20;                          docker push sondossoua/mern-client:latest



3.7. Docker Compse : docker compose up --build





3.8 Pipeline Jenkins :

\-Jenkinsfile à la racine automatise 4 étapes : Build, Push, Deploy, Test

\-Job Jenkins : tp4-mern 



4\. Tests :

\-Client : http://localhost:3000

\-API : http://localhost:9000/api/health



5\. Captures d'écran :



\-Images Docker : captures/image.png

\-Conteneurs en cours d'exécution : captures/ps.png

\-Pipeline Jenkins : captures/jenkins.png

&#x20;                   captures/jenkins\_console.png

\-Docker Hub : captures/dockerhub.png

