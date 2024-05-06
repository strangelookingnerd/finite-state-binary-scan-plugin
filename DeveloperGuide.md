## Developers Guide

### Setting up the project to run in maven locally to develop
To work with the project locally and run it with a Jenkins server, follow these steps:

1. Run Jenkins server locally with the plugin being deployed:
```
source /etc/profile.d/maven.sh 
mvn hpi:run -Dport=5025 
```
> Enter https://localhost:5025/jenkins in your browser

**Note:** Make sure that **port 5025** is free on your machine.

### Setting up dev-test environment in docker

* Make sure a `temp-jenkins` directory exists in your home directory.

* Build the project:
```
mvn clean install
```

* Generate the `hpi` file:
```
mvn hpi:hpi
```

The generated `hpi` file can be found in the `target` folder of your project directory.


* Spin up the jenkins instance with the following command:

**Note:** Make sure that **port 8082** is free on your machine.

```
docker-compose up
```
or if you prefer detach mode
```
docker-compose up -d
```

3. Install the plugin `hpi` file in your Jenkins instance:
>- Go to your Jenkins instance. Enter https://localhost:8082/jenkins in your browser
>- Navigate to **Manage Jenkins** > **Manage Plugins** > **Advanced Settings**.
>- In the **Deploy Plugin** section, click **Choose File**.
>- Select the generated `hpi` file and click **Deploy**.
>- **Restart** your Jenkins instance.

**Note:** `xcode-select` may need to be installed in **Mac** if any kind of error like - `git init` failed or developer path related error is faced while running job from jenkins instance.

Command to install `xcode-select` in Mac:
```
xcode-select --install
```