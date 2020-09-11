[![Build Status](https://travis-ci.com/IBM/MAX-Question-Answering-Web-App.svg?branch=master)](https://travis-ci.com/github/IBM/MAX-Question-Answering-Web-App) [![Website Status](https://img.shields.io/website/http/max-question-answering.codait-prod-41208c73af8fca213512856c7a09db52-0000.us-east.containers.appdomain.cloud/swagger.json.svg?label=api+demo)](http://max-question-answering.codait-prod-41208c73af8fca213512856c7a09db52-0000.us-east.containers.appdomain.cloud) [![Website Status](https://img.shields.io/website/http/max-question-answering-web-app.codait-prod-41208c73af8fca213512856c7a09db52-0000.us-east.containers.appdomain.cloud.svg)](http://max-question-answering-web-app.codait-prod-41208c73af8fca213512856c7a09db52-0000.us-east.containers.appdomain.cloud)

#### Start the server

You then start the web app by running:

```
$ python app.py
```

You can then access the web app at: [`http://localhost:8000`](http://localhost:8000)

#### Configure ports (Optional)

If you want to use a different port or are running the model API at a different location you can change them with command-line options:

```
$ python app.py --port=[new port] --model=[endpoint url including protocol and port]
```

#### Instructions for Docker (Optional)

To run the web app with Docker the containers running the web server and the REST endpoint need to share the same
network stack. This is done in the following steps:

Modify the command that runs the MAX Question Answering REST endpoint to map an additional port in the container to a
port on the host machine. In the example below it is mapped to port `8000` on the host but other ports can also be used.

    docker run -it -p 5000:5000 -p 8000:8000 --name max-question-answering codait/max-question-answering
    
Build the web app image by running:

    docker build -t max-question-answering-web-app .

Run the web app container using:

    docker run --net='container:max-question-answering' -it max-question-answering-web-app
