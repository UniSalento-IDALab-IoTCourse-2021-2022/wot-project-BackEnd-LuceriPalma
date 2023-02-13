
# wot-project-BackEnd-LuceriPalma

Project Road Condition Monitoring System based on Nordic Thingy:52


The complete project is composed by:
- FrontEnd (https://github.com/UniSalento-IDALab-IoTCourse-2021-2022/wot-project-FrontEnd-LuceriPalma)
- BackEnd (https://github.com/UniSalento-IDALab-IoTCourse-2021-2022/wot-project-BackEnd-LuceriPalma)
- presentation (https://github.com/UniSalento-IDALab-IoTCourse-2021-2022/wot-project-presentation-LuceriPalma)



## Authors

- [@mluceri ](https://www.github.com/mluceri)
- [@cpalma-usal](https://www.github.com/cpalma-usal)


## Installation and instruction

In the development environment, a local machine was utilized, with the following needed services:
- A web server (http-server, live-server, ‘express’ in node app, or apache web server) working on localhost. An an express web server is included in the node application serverApp.js.
- A database (JSON Server, MongoDB, PostgreSQL), working on localhost. This project mainly uses json-server, a little development database (DB) server, with live reload capability to create a quick REST API for a DB stored on file in .json format (db.json file). The json-server is included in the node application serverApp.js
- A node application serverApp.js with extra functionalities such as web socket, routing control, access control, launch the trained model and more. ServerApp.js works on port 3002 on localhost.

In the production environment more configuration and settings are required:
- a private certificate for secure (https) connection, 
- a domain (or a dynamic domain with duckdns.org or similar services)

This repository contains the backend : a json-server file, the model environment, and the node serverApp.js


### Setting of the virtualenv python3 for the model

Assuming python3, pip and virtualenv installed.
(on ubuntu or similar distro you can sudo apt install python3-virtualenv)
Setting of the virtual environment for the model with python3 venv. Assuming installend virtualenv of python3

```bash
  cd model
  virtualenv venv 
  source ./venv/bin/activate
  pip install -r requirements.txt
```

Please, note that the bash script to launch the model is into the model folder, and the first line set the interpeter to /bin/zsh, please edit that line as required by your OS.


tested (on unix systems) with 
- Python 3.9.12
- pip 22.3.1 


### Launch the node serverApp.js with node.
Assuming node and npm installed.

```bash
  cd node
  npm i 
  node serverApp.js
```

The node app will be listening on :
  http://localhost:3002/

In details, 
the included json-server will read the db.json file and it will be listening on :
  http://localhost:3002/
  and will answer to GET,POST,DELETE http requests for instances
  http://localhost:3002/db
  http://localhost:3002/points
  http://localhost:3002/potholes
  http://localhost:3002/potfinds

the included websocket will be listening on :
  ws://localhost:3002/

the included 'express' web server (for static file as html,js,css) will be listening on :
  http://localhost:3002/iot/
and it will offer the file included into the 'public' subfolder of the node folder.
Please, note that you need to upload the frontend repository into the 'public' subfolder of the node folder, to complete the webapp.

tested with 
- node version v18.12.0
- npm version 8.19.2



### Other requirements 
Other requirements for the project are:
- curl (https://curl.se/)
- jq  (https://stedolan.github.io/jq/)
- zsh (or another bash interpeter, but you need to edit the script_per_model.sh file)

## Acknowledgements
 - [Nordic Thingy js library](https://github.com/NordicPlayground/Nordic-Thingy52-Thingyjs)
 - [Leaflet interactive map](https://leafletjs.com/)
 - [json-server](https://github.com/typicode/json-server/)


### Put the frontend files into the public web server folder :
The FrontEnd part is available on the [FrontEnd repository](https://github.com/UniSalento-IDALab-IoTCourse-2021-2022/wot-project-FrontEnd-LuceriPalma)