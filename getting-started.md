# Getting Started
> A developer development workflow

### Table of Contents

- [Features](#features)
- [Produce](#produce)
- [Workflows](#workflow)
- [Hosting](#hosting)
- [Deployment](#hosting)
- [Production](#production)

## Features

1. [#2 [Feature] 🚀 : UI | Voice Assistant Interface](https://github.com/iPoetDev/template-guided-projects/issues/2)
2. [#3 [Feature] 🚀 Server | Backend for Voice Assistant Services](https://github.com/iPoetDev/template-guided-projects/issues/3)
3. [#4 [Feature] 🚀 : Infra/Host | Containerization: Packaging App and Components](https://github.com/iPoetDev/template-guided-projects/issues/4)
4. [#5 [Feature] 🚀 : API | Watson Speech-to-Text > Integrate](https://github.com/iPoetDev/template-guided-projects/issues/5)
5. [#6 [Feature] 🚀 : API | OpenAI API](https://github.com/iPoetDev/template-guided-projects/issues/6)
6. [#7 [Feature] 🚀 API | Watson Text-to-Speech > Integrate](https://github.com/iPoetDev/template-guided-projects/issues/7)
7. [#8 [Feature] 🚀 Backend | API | Endpoints: Flask HTTP Routing (Server | Worker)](https://github.com/iPoetDev/template-guided-projects/issues/8)

<br> 

> <hr>

## Produce

**<ins>UI</ins>**

- [ ] To type in text input to a UI interface for a Virtual Assistant chat bot
- [ ] To speak in spoken inpy to a UI interface for a Virtual Assistant chat bot
- [ ] To change and select different personal assistant voices

**<ins>Backend</ins>**

- [ ] To be able to have my spoken words transcribed from speech to text
- [ ] To interact via the front end using natural language and voice transcribed input
- [ ] To receive the responses in natural language or text
- [ ] To have the response displayed or have the choice to synthesise (to speak) the response

*<ins>API Endpoint Routing</ins>*
- [ ] To route and converts the user's speech-to-text using the speech_to_text functionality via a Speech to Text routing.
- [ ] To accept a user's message in text form with their preferred voice via defined routing for the processed message with text to speech.
- [ ] To use our previously defined helper functions to call the LLM Providers API to process this prompt via a defined routing for the processed message
- [ ] convert that response to text using Watson's Text to Speech API and then return this data back to the user via defined routing for the processed message

**<ins>Infra/Host</ins>**

- [ ] To combining (package) all the above components into a functional app
- [ ] To be able to deploy and consistently across different environments, via containers.

**<ins>API</ins>**

- [ ] To to be able to take a user's voice as input for a chat application by integrating a speech to text model
- [ ] To process transcribed queries by OpenAI's a state-of-the-art natural language processing model.
- [ ] To have a LLM NLP model in your assistant to understand and respond to a wide range of user inputs.
- [ ] To process responses from OpenAI's a state-of-the-art natural language processing model.
- [ ] To be able to take a NLP LLM output as text and convert it / synthesise into voices for a chat application by integrating a text to speech model

<br> 

> <hr>

## Workflow

- Coding and compoenent development

### Frontend: The UI 

- **Feature**: [#2 [Feature] 🚀 : UI | Voice Assistant Interface](https://github.com/iPoetDev/template-guided-projects/issues/2)

#### Getting Started: UI

- [ ] Knowledge of the basics of HTML/CSS, Javascript to build a visually appealing and interactive frontend for your assistant.
  - [ ] HTML (Hypertext Markup Language) is a markup language used to structure content on the web
  - [ ] CSS (Cascading Style Sheets) is a stylesheet language used to describe the look and formatting of a document written in HTML
  - [ ] Javascript is a programming language that is commonly used to add interactivity to web pages. 
- [ ] Users will be able to interact with the voice assistant through a web interface that's built using HTML, CSS, and Javascript. 
- [ ] Bootstrap for styling
- [ ] Font Awesome for Icons
- [ ] JQuery for efficient handling of actions

#### Design Brief

- The user interface will be similar to other voice assistant applications, like Google Assistant. 
- The code for the interface is provided as part of the guided app.
- The focus is on building a voice assistant
- And integrating it with various services and APIs.

**<ins>1. Interface</ins>**
- [`index.html`]() is responsible for the layout and structure of the web interface
  - External Libraries incorproation
    - JQuery: 
    - Bootstrap: 
    - FontAwesome Icons: 
    - as well as
- [`style.css`]() CSS Style code responsible for customizing the visual appearance of the page's components
   - CSS Keyframes loading animation:  Keyframes are a way of defining the values of an animation at various points in time, allowing for a smooth transition between different styles and creating dynamic animations. 
- [`script.js`]() JavaScript code responsible for the page's interactivity and functionality.
    - Necessary functions:    
      - switching between light and dark mode, 
      - sending messages, and 
      - displaying new messages on the screen. 
      - enables the users to record audio.

**<ins>2. UI Design</ins>**       

- View the demo app here: 🔗<sub>[![IBM Code Engine](https://img.shields.io/badge/IBM%20Code%20Engine:_Demo_App-AI_Personal_Assistant:_OpenAI_&_WatsonX-1261FE?logo=ibm&logoColor=white)](https://ai-personal-assistant.xs6r134s1i6.us-east.codeengine.appdomain.cloud/)</sub>

- [ ] Employs Dark and Light mode toggle.


### Backend: Controller: `server.py`

- **Feature**: [#3 [Feature] 🚀 Server | Backend for Voice Assistant Services](https://github.com/iPoetDev/template-guided-projects/issues/3)
- **Feature**: [#8 [Feature] 🚀 Backend | API | Endpoints: Flask HTTP Routing (Server | Worker)](https://github.com/iPoetDev/template-guided-projects/issues/8)

#### Getting Started: Server

- Python 3.10 or later is the choosen programming language
- Flask is library for:
   - web development framework for Python and 
   - can be used as a backend for the application.
   - can handle API endpoint routing and HTTP requests/responses.
   - defining the CORS policies.

#### Design

- The server is how the application will run and communicate with all your services
- `server.py` added addtionall functionalities to interact with core functionalities like speech (IBM speech-to-text, text-to-speech) and LLM NLP Tranformer model (e.g. GPT-3)
   - imports key libraries
   - imports key modules
- `server.py` defines
  - Index: `GET` route requests for root endpoint `/` for the `index` function, which renders `index.html`
  - Speech Input Route: `POST` route processes the end point for `/speech-to-text` input for 
    - the user message, 
    - captures/processes the audio binary into text, and 
    - dispatches the request in a machine (json) format for HTTP communication.
  - Process Prompt Route: `POST` route processes the response
    - 1. Captures the `usersMessage`
    - 2. Defined the text to speech Voice
    - 3. Processes the OpenAI response to userMessage
    - 4. Combined the voice with the OpenAi response for output
    - 5. Encodes the output
    - 6. Assemebled the json response when HTTP status is 200/OK
  - `server.py/main()` - initited the Flash app on port and host IP. 

### Backend: Model: `worker.py`

- **Feature**: [#8 [Feature] 🚀 Backend | API | Endpoints: Flask HTTP Routing (Server | Worker)](https://github.com/iPoetDev/template-guided-projects/issues/8)


#### Getting Started: Model

- [ ] Define and set the Openai API Key
- [ ] Test (Curl) access to Speech to Text for remote accces
- [ ] Build the docker build for Speech to Text for local/remote access
- [ ] Test (Curl) access to Text to Speech for remote access
- [ ] Build the docker build for Text to Speech for local/remote access

#### Design: Speech to Text

- [#5 [Feature] 🚀 : API | Watson Speech-to-Text > Integrate](https://github.com/iPoetDev/template-guided-projects/issues/5)

- [ ] Speech to Text function to process the audio input
  - Access local host docker image via port 1080 
  - API 
  - Assign the model parameters
  - Prepare the POST response with json format/encodings
  - Build text to generate from the Get response while true 

#### Design: Text to Speech

- [#7 [Feature] 🚀 API | Watson Text-to-Speech > Integrate](https://github.com/iPoetDev/template-guided-projects/issues/7)

- [ ] Text to Speech function to process the text, with a voice
  - Process the response headers for correct formats/encodings
  - Access local host docker image via port 1081
  - API 
  - Select a voice
  - Prepare the POST response with json format/encodings
  - Process the tts response

#### Design: Open AI API

- [#6 [Feature] 🚀 : API | OpenAI API](https://github.com/iPoetDev/template-guided-projects/issues/6)

- [ ] Open AI Process Message
  - Prepare the prompt and attach to the user message
  - Display the prompt
  - Define the OpenAI response: 
    - Select the model
    - Add the prompt
    - Max the max tokens
  - Prepare the response text and clean it

### Infra/Host

- **Feature**: [#4 [Feature] 🚀 : Infra/Host | Containerization: Packaging App and Components](https://github.com/iPoetDev/template-guided-projects/issues/4)

#### Getting Started: Dockerfiles

- Docker containers 
  - to package application and dependencies.
  - to simplify the deployment process, as the image can be easily distributed and run on any machine
- Docker Locally
  - [ ] Set up WSL ❌ Broken and its dependencies
  - [ ] Set up Windows Native 🤔 TBC
- Docker Remotely
  - [ ] Use labs.cognitiveclass.ai as a remote docker.CDE environment  
  - [ ] Use GitHub Codespaces
  - [ ] Use GitPod or any CDE with .devcontainers / docker installed
  - `devcontainers.json` is required for most remote CDEs.
- Docker compose
  - 3 different containers run (side by side) simulatenously
    - 1: `app`
    - 2: `speech-to-text` (stt)
    - 3: `text-to-speech` (tts)
  - `app` Dockerfile:
      - Python3: 3.10-3.12  
      - requirements.txt
      - rootCA.crt
    - Enviromental Variables
      - OPENAI_API_KEY
      - REQUESTS_CA_BUNDLE
      - SSL_CERT_FILE
    - CMD: `server.py` is the app entrypoint  
  - `stt` Dockerfile: [see here]()
  - `tts` Dockerfile: [see here]()

### API: Watson Speech to Text

Speech-to-Text functionality is a technology that converts speech into text using machine learning.

- **Feature**: [#5 [Feature] 🚀 : API | Watson Speech-to-Text > Integrate](https://github.com/iPoetDev/template-guided-projects/issues/5

#### Requirements

- Skills Network provides its own Watson Speech-to-Text image that runs automatically in this environment. 
  - [ ] Base_URL: https://sn-watson-stt.labs.skills.network
  - [ ] Curl: `curl https://sn-watson-stt.labs.skills.network/speech-to-text/api/v1/models`
  - [ ] API Version: 1
  - [ ] ACCEPT_LICENSE=true

#### Getting Started: TTS

- Set up Watson Speech-to-Text HTTP Api url
- Set up parameters for our HTTP reqeust
- Set up the body of our HTTP request
- Send a HTTP Post request
- Parse the response to get our transcribed text

### API: OpenAI 

- **Feature**: [#6 [Feature] 🚀 : API | OpenAI API](https://github.com/iPoetDev/template-guided-projects/issues/6)

#### Getting Started: Open AI Prompt and AI 

- Set the prompt for OpenAI Api
- Call the OpenAI Api to process our prompt
- Parse the response to get the response message for our prompt

### API: Watson Text to Speech

Text-to-Speech models to give your assistant a voice using Text-to-Speech functionality, that will convert that response to speech.

- **Feature**: [#7 [Feature] 🚀 API | Watson Text-to-Speech > Integrate](https://github.com/iPoetDev/template-guided-projects/issues/7)

#### Getting Started: TTS

- Skills Network provides its own Watson Text-to-Speech image that runs automatically in this environment. 
  - [ ] Base_URL: https://sn-watson-tts.labs.skills.network
  - [ ] Curl: `curl https://sn-watson-tts.labs.skills.network/text-to-speech/api/v1/voices`
  - [ ] API Version: 1
  - [ ] ACCEPT_LICENSE=true

- Set up Watson Text-to-Speech HTTP Api url
- Adding voice parameter in api_url if the user has selected a preferred voice
- Set the headers for our HTTP request
- Set the body of our HTTP request
- Send a HTTP Post request to Watson Text-to-Speech Service

<br> 

> <hr>

## Hosting

### Python

In defining `requirements.txt`, which is used in the folliwng


| Package | Python 3.10 | Python 3.11 | Python 3.12🗝️ |
| --- | --- | --- | --- |
| Flask~=3.0.0 | ✅ | ✅ | ✅🗝️ |
| Flask_Cors~=4.0.0 | ✅ | ✅ | ✅🗝️ |
| openai>=1.0.0, <=1.38 | ✅ | ✅ | ✅🗝️ |
| requests~=2.32.0 | ✅ | ✅ | ✅🗝️ |

- **Key**: ✅ Compatible | 🗝️ Local

Notes:
- Not pining exact versions.
- Using the compatible release operator: `~=` This is equivalent to package>=1.4.2,==1.4.*, which means it will install the latest version that is compatible with 1.4.2, but not 1.5.0 or higher
- Flask~=3.0.0: Flask supports Python 3.8 and including 3.10, 3.11, and 3.12.
- Flask_Cors~=4.0.0: Flask-Cors is compatible with the same versions of Python as Flask.
- openai>=1.0.0, <=1.38: The OpenAI Python client library supports Python 3.7 and  including 3.10, 3.11, and 3.12.
- requests~=2.32.0: Requests library is compatible with Python 3.7 and including 3.10, 3.11, and 3.12.

OpenAI is rapidly iterating its leading GPT models and as such older models are being deprecated.  
- As of the release of OpenAI Python SDK v1.1.0 on November 6, 2023, the minimum non-deprecated GPT model was gpt-3.5-turbo. 
- As of the release of OpenAI Python SDK v1.38.0 on August 2, 2022, the minimum non-deprecated GPT model was gpt-3.5-turbo.

### Local

- Python-3.12 installed
- Docker

### Remote

#### IDE | CDE

Use the following a remote docker.CDE environment  

| CDE \| Remote Environments| DevContainers | Pre-configured | Configure | Git clone/init | Extensions | Persistence | Docker | Deploy | Ports | Host/Live |
| :----------------------- | :----------- | :------------- | :------- | :------- | :------- | :------- | :------- | :------- | :------- | :------- | 
| labs.cognitiveclass.ai   | ❌           | ✅             | ❌       |   Manual   | Manual | TBC | TBC⁉️ | TBC | TBC | TBC |
| GitHub Codespaces <sup>1</sup>       | ✅           | ❌             | ✅       |   Automatic   | Both | Yes, Commits | ✅  | TBC | TBC | 
| GitPod <sup>1</sup>                   | ✅           | ❌             | ✅       |   Automatic   | Both |Yes, Commits | ✅ | TBC | TBC | 

- Confirmed/Yes
- N/A/No
- Automatic
- Manual
- Both: Manual, Automatic

#### Services

|  Service  | External Image/Service |  image_url    |  API ver (Function)  | Dockerfile | Keys | 
| :---- | :---- | :---- | :---- | :---- | :---- |  
| `app`  | ❌  |     |       | ✅ | | 
| `stt`  | ✅  | `https://sn-watson-stt.labs.skills.network`      |  `/speech-to-text/api/v1/recognize`     | ✅ | [Entitlement]() |
| `tts`  | ✅  |`https://sn-watson-tts.labs.skills.network`   |  `/api/v1/synthesize`     | ✅ | [Entitlement]() |
| openai.api     | ☑️    |   |  | 1.38.0 | [OpenAI Key] |

#### Licenses/Keys

> Care must be taken when registering, subscribing (inc credit card), accessing and removing external services keys on trail basise or on freemium to paid usages. 

**<ins>IBM</ins>**
- [IBM Watson Speech to Text Library for Embed Trial](https://www.ibm.com/account/reg/us-en/subscribe?formid=urx-51754)
    - []()
    - [Entitlement Key](https://myibm.ibm.com/products-services/containerlibrary)
- [IBM Watson Text to Speech Library for Embed Trial](https://www.ibm.com/account/reg/us-en/subscribe?formid=urx-51758)
    - []()
    - [Entitlement Key](https://myibm.ibm.com/products-services/containerlibrary)
- [Container software library access is blocked](https://myibm.ibm.com/products-services/containerlibrary): Entitlement to software in the IBM Entitled Registry is based on your IBM ID having access to a Passport Advantage Site.

**<ins>OpenAI</ins>**
- [OpenAI API](https://openai.com/index/openai-api/) | [Docs: API Reference](https://platform.openai.com/docs/api-reference/introduction) | [OpenAi Key](https://platform.openai.com/api-keys)
  - Project: Default

#### DevContainers <sup>1</sup>

```json
{
    "name": "Multi-Service Development Environment",
    "dockerComposeFile": "docker-compose.yml",
    "service": "app",
    "workspaceFolder": "/workspace",
    "remoteUser": "root",
    "customizations": {
      "vscode": {
        "extensions": [
          "ms-vscode-remote.remote-containers",
          "ms-python.python",
          "ms-python.vscode-pylance",
          "ms-azuretools.vscode-docker"
        ]
      }
    },
    "forwardPorts": [8000, 8080, 8081],
    "postCreateCommand": "pip install --user -r requirements.txt",
    "remoteEnv": {
      "OPENAI_API_KEY": "skills-network",
      "REQUESTS_CA_BUNDLE": "/etc/ssl/certs/ca-certificates.crt",
      "SSL_CERT_FILE": "/etc/ssl/certs/ca-certificates.crt"
    }
  }

```

##### <ins>Dependabot Integration</ins>

```plaintext
# To get started with Dependabot version updates, you'll need to specify which
# package ecosystems to update and where the package manifests are located.
# Please see the documentation for all configuration options:
# https://docs.github.com/github/administering-a-repository/configuration-options-for-dependency-updates

version: 2
updates:
  - package-ecosystem: "devcontainers" # See documentation for possible values
    directory: "/"
    schedule:
      interval: weekly

```

```
```

<br> 

> <hr>

## Deployment

<br> 

> <hr>

## Production

<br> 

> <hr>