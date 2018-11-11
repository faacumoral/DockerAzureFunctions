## AzureFunction inside Docker Container
How to use Docker with Azure Functions:

1. First, download and install 
    * [npm](https://nodejs.org/dist/v10.13.0/node-v10.13.0-x64.msi)
    * [NET core](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-2.1.403-windows-x64-installer)
    * [Docker for Windows](https://download.docker.com/win/stable/Docker%20for%20Windows%20Installer.exe) (restart needed)
    
2. Then, in your terminal, run
    * `npm install -g azure-functions-core-tools`
    * `mkdir AzureFunctionWithDocker`
    * `cd AzureFunctionWithDocker`
    * `func init --docker` and choose **dotnet** runtime
    * `func new`, choose **HttpTrigger** and then write your function name.
    
3. Open YourFuncName.cs and change **AuthorizationLevel** from *Function* to *Anonymous*, your file should look like [that](https://github.com/faacumoral/DockerAzureFunctions/blob/master/DockerFunctionTutorial.cs)

4. Finally, run:
    * `docker build -t <image-name> .`
    * `docker run -p 8080 <image-name>`

5. Open a browser and go to http://localhost:8080/api/YourFuncName?name=Medium%20Community. You should see "*Hello, Medium Community*"