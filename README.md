# DockerPesa
DockerPesa is an M-Pesa C2B API image for docker, You dont need any SDK or programming language, 
all you need is two minutes deploy it 

## Installation
Just clone this repository into your local computer

```bash
git clone git@github.com:GraHms/dockerpesa.git
```
## Usage
edit the config.json file. 
M-Pesa API uses the same service provider code for testting, 
You can change the default 171717 code when you are in production

```json
{
    "api_key":"paste in here, your mpesa api key",
    "public_key":"paste in here your mpesa public key",
    "sp_code": "171717"
    
}
```
## Understanding the Dockerfile
This by default it exposes the port to 8080, 
but you can choose any port you want, by adding EXPOSE ${your port number}

```Dockerfile
FROM grahms/dockerpesa

COPY . ./
```
## Image Build
Go to the terminal and run your the dockerfile to build the image with your configurations

```bash
docker build --pull --rm -f "Dockerfile" -t mydockerpesa "."
```
## Run Image
Now you can run you can create a docker container by running the image you just created
```bash
docker run --rm -d  -p 8080:8080/tcp mydockerpesa:latest
```
##

## Make a C2B Payment
since your docker container is running on port 8080,if you are on local host just send a post request
to localhost:8080 with this parameters msidsdn=84xxxxx and amount=200

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License
[MIT](https://choosealicense.com/licenses/mit/)
