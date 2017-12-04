DEPLOY IN JAVA THROUGH ELASTIC BEANSTALK
========================================

Amazon Web Services (AWS) comprises dozens of services, each of which exposes an area of functionality. While the variety of services offers flexibility for how you want to manage your AWS infrastructure, it can be challenging to figure out which services to use and how to provision them.
![Elastic Console]![(http://notes.webutvikling.org/wp-content/uploads/2016/10/beanstalk.jpg)](https://lh3.googleusercontent.com/-iZ9KEWuyJQE/WiQFztFTDfI/AAAAAAAAD_w/WIPpsw5KW3YYshoeoGIr31XMeYaOD5NtwCLcBGAs/s0/elastic1.png "elastic1.png")

With Elastic Beanstalk, you can quickly deploy and manage applications in the AWS Cloud without worrying about the infrastructure that runs those applications. AWS Elastic Beanstalk reduces management complexity without restricting choice or control. You simply upload your application, and Elastic Beanstalk automatically handles the details of capacity provisioning, load balancing, scaling, and application health monitoring. Elastic Beanstalk uses highly reliable and scalable services that are available in the AWS Free Usage Tier.
For more information  , please check out this link:
http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/Welcome.html

1. Deploy Java file through AWS Console:
----------------------------------------

Deploying Java Application through the console is a multi step process during which EC2 asks for a simple .jar file to read in and broadcast it on the AWS console. 

(https://www.dropbox.com/home/Malachite?preview=elastic1.png)

To execute this , please follow the steps described in this console:

![EB Console](https://lh3.googleusercontent.com/-mWbupTTkmBA/WiKOqAJcX1I/AAAAAAAAD_U/TZDP5rOWX1kT3EOJEL270CXPTxgvpxNHwCLcBGAs/s0/ebdeploy.png "ebdeploy.png")


Notice : Before you build your project to upload and deploy, make sure that the AWS server will register your file. Applications launched in Spring are basically set for a default server  (**_localhost:8080/_**).

You can simply change the port in the application.properties:

![Setting the Port](https://lh3.googleusercontent.com/-Sfqav50CLpk/WiJ2PVestCI/AAAAAAAAD8g/QhfJdGMldusmnIGIa10PCo6bC0dW2CvngCLcBGAs/s0/approp.png "approp.png")

2. Deploy Java application through the Elastic Beanstalk Command Line Interface.
------------------------------------------------------------------------

The EB CLI is a command line interface for Elastic Beanstalk that provides interactive commands that simplify creating, updating and monitoring environments from a local repository. Use the EB CLI as part of your everyday development and testing cycle as an alternative to the AWS Management Console.

Before you set up your CLI , be sure to have access to the latest version of Python Package

[Python 3.6 Installation](https://www.python.org/downloads/).

[Install on Windows](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/eb-cli3-install-windows.html)
[Install on Linux](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/eb-cli3-install-linux.html)
[Install on Mac](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/eb-cli3-install-osx.html)
[Install on Virtual Enviroment](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/eb-cli3-install-virtualenv.html)

The CLI will be launched by entering the **_"eb"_** command

![EB launch](https://lh3.googleusercontent.com/-a_QNla-EMDc/WiJ8wpfGmXI/AAAAAAAAD9M/BKxJDvZaHT88WQMQo-IlyQmUZGVwNYDyACLcBGAs/s0/eblaunch.JPG "eblaunch.JPG")


To get started ,type "eb init". Then type "eb create" and "eb open"



a.Create a folder in your PC where you would copy your actual .jar/.war file, and make sure that you execute the deploy process in that folder.

![Folder Check](https://lh3.googleusercontent.com/-9EMjQp-ZpRQ/WiJ6-LiMkbI/AAAAAAAAD84/Kwn4jq4bmaICYyzK0pf2p1CIwjWiuJCEgCLcBGAs/s0/ebinit0.JPG "ebinit0.JPG")

b.Run **"eb init"** in your application's project directory to configure the EB CLI and your project.

The EB CLI prompts you to select a region. Type the number that corresponds to the region that you would like to use and press Enter

![Region Selection](https://lh3.googleusercontent.com/-ow9bioOu88g/WiKBSgNyWTI/AAAAAAAAD9g/_2haQngSf4wavCPPjienJEiluLLW0qZ7ACLcBGAs/s0/ebinit1.JPG "ebinit1.JPG")

Provide your access key and secret key so that the EB CLI can manage resources for you. Access keys are created in the AWS Identity and Access Management management console.

![EB Credential](https://lh3.googleusercontent.com/-9TaJtgO-Nx8/WiKG5PhZBGI/AAAAAAAAD94/_SEGIVEGQ2Qeihh0rLPXLuBfi_I0LmqGACLcBGAs/s0/ebcred.JPG "ebcred.JPG")

An application in Elastic Beanstalk is a resource that contains a set of application versions (source), environments, and saved configurations that are associated with a single web application.

![Selecting Application](https://lh3.googleusercontent.com/-aJlM0f9idqA/WiKHM3gBkWI/AAAAAAAAD-A/tYs-WUCBr6wKRQCVPu-LpuiFmPVrGDQOwCLcBGAs/s0/ebinit2.JPG "ebinit2.JPG")

![Entering application name](https://lh3.googleusercontent.com/-zm99BYlLeqk/WiKHaAmzj0I/AAAAAAAAD-M/M7GkuyMe4owgwBLk359DCyTJGmgh-FwoACLcBGAs/s0/ebinit3.JPG "ebinit3.JPG")

Select a platform that matches the language or framework that your web application is developed in. If you haven't started developing an application yet, choose a platform that you are interested in.

Choose **yes** to assign an SSH key pair to the instances in your Elastic Beanstalk environment, allowing you to connect directly to them for troubleshooting.

![Choosing platform](https://lh3.googleusercontent.com/-baMi7X3lm5c/WiKILUKt-qI/AAAAAAAAD-c/yH1ZkNqwlNsEpTmrWbyqzuSvWzwyYhctQCLcBGAs/s0/ebinit4.JPG "ebinit4.JPG")

You have completed the configuration of your project folder. The application will be deployed after the enviroment is defined.

2.**"eb create"** sets up the enviroment and deploys an application version

Environment names must be between 4 and 40 characters in length, and can only contain letters, numbers, and hyphens. Environment names can't begin or end with a hyphen.

If you include an environment name in the command, the EB CLI doesn't prompt you to make any selections or create a service role.

![Creating enviroment](https://lh3.googleusercontent.com/-LihJ7NE2Wl4/WiKM1allWwI/AAAAAAAAD_A/5NQJSCEnqFIAKvBNJS2BwTWVGPvxBSJ5gCLcBGAs/s0/ebcreate.JPG "ebcreate.JPG")

If you run the command without parameters, it runs in an interactive flow, and prompts you to enter or select values for some settings. In this interactive flow, in case you are deploying a sample application, the EB CLI also asks you if you want to download this sample application to your local project directory. This enables you to use the EB CLI with the new environment later to run operations that require the application's code, like **eb deploy**

To open your environment's website in a browser, use **eb open**:

>User@User MINGW64 ~/greenfox/foxclub
$ eb open





