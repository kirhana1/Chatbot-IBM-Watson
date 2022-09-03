# Troubleshooting Guidance using IBM Assistant ChatBot
Building the chatbot via IBM on VMware Snapshot and Storage troubleshooting

This chatbot is specifically built on IBM Watson Assistant environment and has the hierarchical topology and interactive conversational dialogues to query and troubleshoot support based architectural procedure towards VMware Snapshot and Storage related issues.

A user needs to have an account in IBM Watson Cloud to be able to create and use the Watson Assistant Services
The account can be either free or paid version.

After creating an account, the user needs to register and select a particular resource list to be able to create and provide the necessary computational and infrastructural resources and services required to create/manage/modify/query the Watson Assistant chatbot.

Once the resource repository location is selected, a user needs to create a Watson Assistant chatbot from the catalogue selection and proceed with Launching the Watson Assistant.
After launching the Watson Assistant, a user needs to be well aware and thorough with the Watson Assistant complete architecture and Integrating the Intent,Entities and Navigational options that are integrated with Watson Assistant Dialog Boxes and WorkFlow.

The dialog workflow and orientation are depicted in the json file "Storage---Snapshot-Snap-Up-Buddy-dialog" attached to this GitHub repositories and intents/entities can be found in the CSV files.
One can also start conversing with the chatbot created with respect to this project via preview link attested.

If the user wants to query the chatbot using the Python codes, we can query the IBM Watson via Python using the following parameters :- 
                          1. API Key :- dxTC5gCR9oHI657BpJRxOstetuWs_xEk6uq985jMslqx
                          2. Service URL :-  https://api.us-south.assistant.watson.cloud.ibm.com/
                          3. Assistant ID :- 947f1635-499f-4ea7-b469-0715287c5f84
                          4. Session ID :- This keeps changing with every query with the Assistant ID
                          
Python interaction with IBM Chatbot Assistant is depicted below

<img width="398" alt="image" src="https://user-images.githubusercontent.com/89430999/188258928-3fbcc99d-4dc3-4f65-849c-bb5d06d31772.png">

<img width="809" alt="image" src="https://user-images.githubusercontent.com/89430999/188258952-34ea03ef-5ffa-40ae-ba7b-70d8a887607c.png">

<img width="905" alt="image" src="https://user-images.githubusercontent.com/89430999/188258957-893d2373-b11a-41fc-a6fe-6f79da15dd58.png">

The HTML and iPYNB files of the code is uploaded to this GitHub Respository
