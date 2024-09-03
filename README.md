# Notificaciones para azure pipelines
---
In this repo you will find different ways to implement azure devops pipeline notifications other than Teams notifications, that is, using other systems such as Google chat or slack. In the first versions you will find the version for google chat and in future releases implementations for more corporate chat systems.

---

## Google Chat

For the use of the file corresponding to this tool, you must enter the folder _files_ and there you will find the folder with the name _google-chat_. Inside it you will find a single file which contains the execution of a bash file, which configures a card to be sent by means of a POST request to the Google Chat Webhook.

#### Recomendaciones:

- 3 VITAL variables must be configured for the operation of the task, these must be done either by setting environment variables at the time of executing the stage, either within a group of variables, or by setting each one at the time of execution.

```bash
    webHookUrl=$(webhook-url)
    repositoryGroupURL=$(azure-url)
    stage=$(stage)
```

- The first variable (webHookUrl) you are going to get, creating a chat group type ads in google chat:

![alt text](images-readme/image.png)

once it is created, you must go to the space settings, then to the applications and integrations section and there you will find the webhooks section, proceed to create one.

![alt text](images-readme/image3.png)

Creating the webhook:

![alt text](images-readme/image4.png)

_note: you can configure an avatar if you wish, this can be done by clicking here --> [GRAVATAR](https://vinicius73.github.io/gravatar-url-generator/#/)_

![alt text](images-readme/image2.png)

Once created, we copy the url and we must pass it through the following converter so that it works without problem: 

[CONVERSOR](https://onlinelinuxtools.com/escape-shell-characters)

![alt text](images-readme/image5.png)
Already this is the value needed to use it in the webHookUrl variable.

- For the next value which is the URL of the Azure DevOps repository, the URL of the Azure DevOps project should be set as follows:

        https://dev.azure.com/{Organization}/{Project}

- For the last variable, it is already something that is put for more order at the time of the notifications since it informs the environment in which the pipeline is being executed, giving more information. 

This is the final result of the card created and how it looks like on notification:

![alt text](images-readme/image7.png)

It also notifies when the pipeline fails and when it ends with errors:

![alt text](images-readme/image6.png)

_NOTA: El desarrollo de implementacion del boton de Sonarcloud esta en fase beta, una vez haya estabilidad subire la version_