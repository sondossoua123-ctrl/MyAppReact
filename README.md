TP4 : Docker et Docker Compose (application MERN)



1.Liens :

GitHub : https://github.com/sondossoua123-ctrl/MyAppReact

Docker Hub (serveur) : https://hub.docker.com/r/sondossoua/mern-server

Docker Hub (client) : https://hub.docker.com/r/sondossoua/mern-client



2.Structure de projet : 

MyAppReact contient :

client (React + Vite, Dockerfile)

server (Express, Dockerfile)

captures

docker-compose.yml

README.md 



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



4\. Tests : 

Client : http://localhost:3000

API : http://localhost:9000/api/health



