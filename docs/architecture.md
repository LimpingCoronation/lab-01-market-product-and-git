## Product choice
- Telegram
- [Link](https://telegram.org/)
- Messanger for daily using. It uses closed enctrypting alogrithm

## Main components
1. ![Telegram Component Diagram](./diagrams/out/telegram/component-diagram/ComponentDiagram.svg)
2. ![Telegram Component Diagram code](./diagrams/src/telegram/component-diagram.puml)
3. Components
- Bot Server Api: responsible for communicating with telegram bots. Bots take information from this
- Event Bus (Kafka): is used for communication between services
- Secret chat relay is used for supporting secret chats
- Sms providers are used for sending sms and other types of messages to clients
- MTProto gateway: security channel for communication between client and backend

## Data flow
1. ![Telegram Component Diagram](./diagrams/out/telegram/sequence-diagram/SequenceDiagram.svg)
2. ![Telegram Component Diagram code](./diagrams/src/telegram/sequence-diagram.puml)
3. Media upload server:
- Firstly, we upload media file to the server
- Then we call rpc method to write media in another service
- We write it to another external storage
- Then we obtain success msg from external server, and return acknowledge to server
- From media server we obtain status of our operation and to storage we send data of file. Also we store file via rpc.

## Deployment
1. ![Telegram Component Diagram](./diagrams/out/telegram/deployment-diagram/DeploymentDiagram.svg)
2. ![Telegram Component Diagram code](./diagrams/src/telegram/deployment-diagram.puml)
3. We support Backend servers via k8s and distribute between different servers, also media and another servers

## Assumptions
- I assume bot api server handle events for the bots, e.g new message. Also, I assume that bot api server can send events to the bot
- I assume auth server send token to the client

## Open questions
- How server chat maintain security between clients?
- How channel/broadcase server works?
