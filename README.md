# example-Chatbot
This is a example repository for chatbots. To create a new chatbot fork this repository and fill it with the specific domain.

## Deploy and run the project
To deploy and run this project docker is mandatory, you would need to install docker as well as docker stack or docker compose.
The project depends on another project 'chatbot-core' which is needed to deploy the image.

### Build
You can run the build by the following command. We will tag the image with our docker registry url and the projects name.
```bash
docker build -t docker.nexus.gpchatbot.archi-lab.io/chatbot/kfz-chatbot .
```

### Run
In order to run the chatbot you will need to create a docker network which is called 'chatbot'. You can do this by running the following command:
```bash
docker network create chatbot
```
The chatbot could be started in different modes with  different purposes:

* *local* - in local mode the bot will be trained with the locally located domain file and supplies an api to interact with. You can start the bot with the following command:
   ```bash
      docker-compose -f docker/docker-compose.yaml -f docker/docker-compose.local.yaml up -d
   ```
* *trainer* - in trainer mode the chat bot will train a given model and sens it to our model server, please read the corresponding project documentation '[core-model-server](https://bitbucket.gpchatbot.archi-lab.io/projects/CHATBOT/repos/core-model-server/browse)'. This mode could be run by:
   ```bash
      docker-compose -f docker/docker-compose.yaml -f docker/docker-compose.trainer.yaml up -d
   ```
* *interactive* - in interactive mode the bot will be trained withe the local domain and supplies an api to train and build up new stories. This mode could be started by the following command:
  ```bash
    docker-compose -f docker/docker-compose.yaml -f docker/docker-compose.interactive.yaml up -d
  ```
