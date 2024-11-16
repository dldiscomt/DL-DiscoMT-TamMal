
# DL-DiscoMT - Tamil to Malayalam MT 

 This project provides a translation model that converts Tamil text into Malayalam. It is built to facilitate smooth and accurate translation between these two languages. The model has been optimized using CTranslate2, which allows it to run efficiently and provides a compact model file suitable for deployment in various environments. This project is ideal for developers and organizations needing language translation support for Tamil and Malayalam in their applications.
   
## Download - Model

Download the model from the provided drive link: 

   [https://drive.google.com/drive/folders/1DbA40CJsLZVXLlW3l0-AXIogsm7Hfy0a?usp=sharing](https://drive.google.com/drive/folders/1DbA40CJsLZVXLlW3l0-AXIogsm7Hfy0a?usp=sharing)

Alternatively, you can use the following command:

```bash
pip install gdown

gdown --folder https://drive.google.com/drive/folders/1DbA40CJsLZVXLlW3l0-AXIogsm7Hfy0a?usp=sharing

```
* The download path, we will consider as **"basePath"** in this readme

## Deployment - Docker  

* To create a Docker image, use the following command. Replace <Image Name> with your desired image name, and <replace/the/path/Dockerfile> with the actual path to the Dockerfile you downloaded from the drive.


```bash
## windows

   docker build -t <Image Name> <basepath/Tam-Mal-NMT-AUKBC-ULCA-Deploy/>
```
Or on Ubuntu:
```bash
## ubuntu

   sudo docker build -t <Image Name> <basepath/Tam-Mal-NMT-AUKBC-ULCA-Deploy/>
```

* After creating the Docker image, use this command to run the model. Make sure to replace <Image Name> with the actual image name you created.

```bash
## windows

   docker run -ti --gpus all -p 8000:8000 -p 8001:8001 -p 8002:8002 <Image Name>
```
Or on Ubuntu:
```bash
## ubuntu

   sudo docker run -ti --gpus all -p 8000:8000 -p 8001:8001 -p 8002:8002 <Image Name>
```
**Breakdown of the Command:**

- docker run: This command starts a new container from an existing Docker image.

- ti:

  - t: Allocates a pseudo-TTY, which allows you to interact with the container.
  - i: Keeps the standard input open so you can interact with the container, useful for running commands interactively.
- --gpus all: This option enables the use of all available GPUs on the host machine inside the container. It ensures the container can access the GPU resources, which is crucial for running machine learning models or any computation that requires GPU acceleration.

- -p 8000:8000 -p 8001:8001 -p 8002:8002: These options map the container’s internal ports to the host machine’s ports. In this case:

  - 8000:8000: Maps the container's internal port 8000 to port 8000 on the host machine.
  - 8001:8001: Maps port 8001 in the container to port 8001 on the host.
  - 8002:8002: Maps port 8002 in the container to port 8002 on the host.

    This ensures that any services running inside the container on these ports (e.g., Triton Inference Server) can be accessed externally on the same ports from the host machine.

- <Image Name>: This is a placeholder for the actual name of the Docker image that was built earlier. You will replace <Image Name> with the name of your Docker image containing the model and the server.



## Access the Model Using Python 

* Install the required dependencies:

```bash
  pip install tritonclient[all] numpy
```

* Run the Python file NMT_tritonAPI_request.py. Before running, replace url="<url of triton server>" in the code with the actual URL of your Triton server (e.g., 192.168.85.24:8000)




## Screenshots
input :"People can enjoy boating in the lake, either in normal or luxury boats."
![App Screenshot](https://github.com/dldiscomt/DL-DiscoMT-HinTam/blob/main/OutputScreenshots/Screenshot%20from%202024-09-10%2015-37-03.png?raw=true)


input :"The first boat  was brought to the lake from Tuticorin."
![App Screenshot ](https://github.com/dldiscomt/DL-DiscoMT-HinTam/blob/main/OutputScreenshots/Screenshot%20from%202024-09-10%2015-38-40.png?raw=true)


input :"There is also a Kodaikanal Boat Club."
![App Screenshot](https://github.com/dldiscomt/DL-DiscoMT-HinTam/blob/main/OutputScreenshots/Screenshot%20from%202024-09-10%2016-08-46.png?raw=true)


## Demo

You can see the demo and working of the model in 
[Machine Translation](https://searchko.co.in/transaukbc/)


## License
CC BY 4.0 
