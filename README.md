SignalR-Web-Client
======================
This is a JavaScript based SignalR Web Client.

It is a debugging tool to test ASP.Net Core SignalR hubs. This is a UI based SignalR client. Using this tool, we can send the data to the SignalR hub and receive the response from the SignalR Hub. This tool is design for dotnetcore developer to make their life easier when they work with SignalR.

<p align="center">
  <img src="./src/images/SignalR-Web-Client.jpg" >
  <br>
</p>

*Table of Contents*

- [SignalR-Web-Client](#signalr-web-client)
- [Basic Understanding of:](#basic-understanding-of)
- [Prerequsit](#prerequsit)
- [How to install?](#how-to-install)
- [How it works?](#how-it-works)
    - [Baisc View](#baisc-view)
      - [Server Method:](#server-method)
      - [Request Payload:](#request-payload)
      - [Data Type supports:](#data-type-supports)
    - [Advance View](#advance-view)
    - [Reporting Issues](#reporting-issues)
  - [How to integrate?](#how-to-integrate)
- [Technologies](#technologies)
- [Browser Support](#browser-support)
- [License](#license)


# Basic Understanding of:

Before using this tool, you should be know few concepts about:

- [What is Asp.Net Core?](https://dotnet.microsoft.com/learn/aspnet/what-is-aspnet-core)
- [What is SignalR in Asp.Net Core?](https://docs.microsoft.com/en-us/aspnet/core/signalr/introduction?view=aspnetcore-3.0)

# Prerequsit

- Node.Js
- Npm
- Git

# How to install?

Tool is available [here](https://gourav-d.github.io/SignalR-Web-Client/dist/).

Locally installation:

1. Need to clone repository. Open cmd and run the below command:
    ```
    git clone https://github.com/gourav-d/SignalR-Web-Client.git
    ```
2. Once the cloning is done, go inside "SignalR-Web-Client" folder.
   ```
   cd SignalR-Web-Client
   ```
3. The tool need to be run under some server. This is one of the requirement of SignalR library. So, if you already have a running server, then copy the content of "SignalR-Web-Client\dist" folder and put it on your server.<br/>
   If you don't have server or wants to run the tool in different server, no worry.<br/>
  Will tell you two approches to run this tool.
  1. Using http server(npm). Here, we will use the published files and run under the server.<br/>
        ```
        npm install http-server -g
        ```
        Then go to "SignalR-Web-Client\dist" folder, and run the below command:<br/>
        ```
        http-server
        ```
        It will start the http-server and host the application. 
        ```
            Starting up http-server, serving ./
            Available on:
            http://192.168.1.5:8080
            http://127.0.0.1:8080
            http://172.18.96.166:8080
            Hit CTRL-C to stop the server
        ```
   
   2. Using npm. Here, we will build the tool and then run under the server. If you wants to customize the tool, then you can you this approch.
       ```
       npm install
       npm run dev
       ```
  It will start the webpack-dev-server and host the application.
  ```
    > signalr-web-client@1.0.0 dev C:\demo\SignalR-Web-Client
    > webpack-dev-server --content-base dist --hot --mode development

    i ｢wds｣: Project is running at http://localhost:8080/
    i ｢wds｣: webpack output is served from /
  ```

# How it works?

SignalR Web Client have two views:
1. Basic
2. Advance

### Baisc View

In this basic view, you can contact to hub by providing the hub address.

1. Pass the valid Hub address in Hub Address textbox.(for ex. https://localhost:5001/Test/OneHub).
<img src="./src/images/1.PNG"  width="600px" height="400px" />

2. Once click on Connect button, it will make connection with server. Once the connection is established, if any data is broadcast from the Hub(ex. OneHub) to all the client. Then, it will be displayed in Response payload textbox.

3. If we want to call any Hub method. For exmaple TesCall method
```csharp
public class OneHub : Hub
{
    public async Task TestCall(string data)
    {
        var connectionId = Context.ConnectionId;
        await Clients.Client(connectionId).SendAsync("ReceiveData", $"Data Received from  TestCall method: {data}");
    }
}
```
In the tool, we have to pass the parameter.

#### Server Method: 
    TestCall

#### Request Payload:
    It can take multiple parameters. In our example, TestCall method only taking one parameter of type string. 
    ex. Arg: abc
        Type: Text

#### Data Type supports:
    Text, Number & JSON

<img src="./src/images/5.PNG" width="300px" height="300px" />

Then click on send button. It will send all the data to the hub. 

<img src="./src/images/3.PNG"   />

### Advance View

It has all the functionality which basic view provides, also it has additional features:
 - Authentication Header
 - Transport Type ([To know more about SignalR Transport](https://kevgriffin.com/signalr-transports-explained/))

 <img src="./src/images/2.PNG"   />


### Reporting Issues

Nothing is perfect.
- Found an issue?
- Wants a new feature?

Then, just open a [new clear and descriptive issue](../../issues/new).


## How to integrate?

1. Create a new project.
  File -> New -> Project -> Select "ASP.NET Core Web Application"

2. Now we have to create hub.
    - Create a folder "Hubs". Inside that folder, create a file called "TestHub.cs".



# Technologies

- Aspnet-Signalr 1.1.4
- Bootstrap 4.3.1
- [Mitt](https://github.com/developit/mitt)
- WebComponentsJs 2.2.10

# Browser Support
Currently it supports only chrome browser.

# License

[MIT License](https://opensource.org/licenses/MIT)

---
Copyright &copy; 2020,
Created by [Gourav Dwivedi](https://github.com/gouravdwivedi6590).
Released under the terms of the [MIT license](https://github.com/gouravdwivedi6590/SignalR-Web-Client/blob/master/LICENSE).