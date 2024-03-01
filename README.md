#ChatGemini

ChatGemini is a web client based on Google Gemini. It benchmarks against ChatGPT 3.5 and uses the same logic as ChatGPT 3.5. It also supports uploading images in chat and automatically calls the Gemini-Pro-Vision model for image recognition.

This project can also customize the Gemini API server address. Users can deploy this project to a server or virtual host that supports PHP, or configure the Nginx reverse proxy themselves and modify the Gemini API path to make it accessible in mainland China.

If you are interested in this project, you are welcome to Star and Fork.

## Demo site (need to bypass the firewall)

[ChatGemini](https://gemini.vnprox.com/)

## Discussion Group

Welcome to join the Telegram group to communicate with other users, feedback questions or suggestions, and learn about the latest developments in the group.

Join the group and chat in a friendly manner.

  - [ChatGemini@Telegram](https://t.me/+iHpQPT3hTDtlNDM1)

## Features

  - Adapt to mobile terminal
  -Support multiple API key offloading
  - The operation logic is the same as ChatGPT
  - Imitation ChatGPT 3.5 interface
  -Support multiple rounds of chat dialogue
  - Support uploading pictures for identification
  - Verbatim output (SSE) response
  - Integrated reverse proxy for PHP
  - Custom Gemini API address
  - Site passcode can be enabled to prevent abuse
  - Chat content export (HTML and PDF)
  -Conversation content is saved in IndexedDB
  - Run Python code in AI responses

## Interface preview

<details><summary>Click to expand the webpage effect</summary>

| Features | Preview |
| :----------: | :---------------------------------- -------------------------------------------------- ----------------------------------: |
| Main interface | <img src="https://raw.githubusercontent.com/bclswl0827/ChatGemini/master/preview/home.png" alt="Main interface" /> |
| Multi-round chat | <img src="https://raw.githubusercontent.com/bclswl0827/ChatGemini/master/preview/chat.png" alt="Multi-round chat" /> |
| Attachment recognition | <img src="https://raw.githubusercontent.com/bclswl0827/ChatGemini/master/preview/attachment.png" alt="Attachment recognition" /> |
| Execute Python | <img src="https://raw.githubusercontent.com/bclswl0827/ChatGemini/master/preview/python.png" alt="Execute Python" /> |
| Output the response verbatim | <img src="https://raw.githubusercontent.com/bclswl0827/ChatGemini/master/preview/sse.png" alt="Output the response verbatim" /> |
| Chat export HTML | <img src="https://raw.githubusercontent.com/bclswl0827/ChatGemini/master/preview/export_html.png" alt="Chat export HTML" /> |
| Chat export PDF | <img src="https://raw.githubusercontent.com/bclswl0827/ChatGemini/master/preview/export_pdf.png" alt="Chat export PDF" /> |

</details>

## Application deployment

Please make sure you have obtained the Gemini API key. To apply for the Gemini API, please go to [Google AI Studio](https://makersuite.google.com/app/apikey).

### Manual deployment

Make sure [Node.js](https://nodejs.org/zh-cn/) and [Git](https://git-scm.com/) are installed.

After the preparation is complete, perform the following steps:

  1. Clone the warehouse locally
```bash
$ git clone https://github.com/royzxje/chat-with-gemini/
```
  2. Enter the project directory
```bash
$ cd ChatGemini
```
  3. Install dependencies
```bash
$ npm install
```
  4. Modify configuration
> Refer to the [Application Configuration](#ApplicationConfiguration) section below
  5. Build the project
```bash
$ npm run build
```
  6. Deployment project
> Deploy the files in the `build` directory to the server or virtual host

  7. Start the service (optional)
> If running locally, execute
```bash
$ npm run start
```

### Docker deployment

Make sure [Docker](https://www.docker.com/) is installed on the server, then perform the following steps:

  1. Pull the image
```bash
$ docker pull ghcr.io/bclswl0827/chatgemini
```
  2. Run the container
```bash
$ docker run -d \
     --name chatgemini \
     --restart always \
     --publish 8080:8080 \
     --env REACT_APP_GEMINI_API_KEY="your key" \
     ghcr.io/bclswl0827/chatgemini
```
> To enable the automatically set Nginx reverse proxy in the Docker version, please set the `REACT_APP_GEMINI_API_URL` variable value to `__use_nginx__`, that is, add the `--env REACT_APP_GEMINI_API_URL="__use_nginx__"` parameter when creating the container
  3. Access the application
> Just visit `http://<IP>:8080`

### Vercel Deployment

This project supports one-click deployment by Vercel. Click the button below to deploy to the Vercel platform.

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2Froyzxje%2Fchat-with-gemini&env=REACT_APP_GEMINI_API_KEY&envDescription=REACT_APP_GEMINI_API_KEY%20is%20essential&envLink=https%3A%2F%2Fgithub.com%2Fbclswl0827%2FChatGemini%2Fblob%2Fmaster%2FREADME.md&demo-title=ChatGemini&demo-url=https%3A%2F%2Fibcl .us%2FChatGemini&demo-image= https%3A%2F%2Fraw.githubusercontent.com%2Fbclswl0827%2FChatGemini%2Fmaster%2Fsrc%2Fassets%2Flogo.svg)

Only the required `REACT_APP_GEMINI_API_KEY` variable is left in the template. After the deployment is completed, if you need to modify or add a new configuration, please go to the Vercel console, click on the corresponding item, and then click on `Settings` -> `Environment Variables` to modify it . After the modification is completed, deployment needs to be triggered again in the Vercel console for the new configuration to take effect.

## Keep updating

### If using manual deployment

If you use manual deployment, you can keep it updated by following these steps:

  1. Enter the project directory
```bash
$ cd ChatGemini
```
  2. Pull the latest code
```bash
$ git pull
```
  3. Install dependencies
```bash
$ npm install
```
  4. Rebuild the project
```bash
$ npm run build
```
  5. Deploy the project
  6. Restart the service

### If you use Docker deployment

If you use the traditional `docker run` command to deploy the version, you can keep it updated through the following steps:

  1. Delete old containers
```bash
$ docker rm -f chatgemini
```
  2. Pull the latest image
```bash
$ docker pull ghcr.io/bclswl0827/chatgemini
```
  3. Run the new container
```bash
$ docker run -d \
     --name chatgemini \
     --restart always \
     --publish 8080:8080 \
     --env REACT_APP_GEMINI_API_KEY="your key" \
     ghcr.io/bclswl0827/chatgemini
```

If you use the `docker-compose` command to deploy the version, you can keep it updated through the following steps:

  1. Enter the directory where `docker-compose.yml` is located
  2. Pull the latest image
```bash
$ docker-compose pull
```
  3. Restart the container
```bash
$ docker-compose up -d --remove-orphans
```
1. Remove the old image (optional)
```bash
$ docker image prune
```

### If using Vercel deployment

For projects deployed using Vercel, the platform will create a new repository in the user's GitHub repository instead of forking the repository, so updates cannot be detected correctly. Please follow these steps to update manually:

  1. Delete the repository created by Vercel
  2. Use the Fork button in the upper right corner of the page to Fork this project
  3. Re-select and deploy the Fork project in Vercel and complete the deployment

For the warehouse after the fork, due to the limitations of GitHub, you need to manually enable Workflows on the Actions page of the warehouse after the fork, and enable the Upstream Sync Action. Once enabled, you can turn on hourly automatic synchronization of the upstream code.

## Application configuration

The basic configuration of the project is located in the `.env` file in the root directory. When deploying manually, please create this file and configure it according to the actual situation; if you use Docker to deploy, please pass the `--env` parameter when creating the container. configuration.

The configuration format is `KEY="VALUE"`. It is recommended to use double quotes to wrap the value, for example:

```bash
REACT_APP_GEMINI_API_URL="https://api.example.com"
```

## Open Source License

This project is open source based on the MIT license. For details, please refer to [LICENSE](https://github.com/bclswl0827/ChatGemini/blob/master/LICENSE)

Cre: [bclsw10827](https://github.com/bclswl0827/)

![Star History Chart](https://api.star-history.com/svg?repos=bclswl0827/ChatGemini&type=Date)
