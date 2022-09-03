# Chatbot-IBM-Watson
Building the chatbot via IBM on VMware Snapshot and Storage troubleshooting

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

import json
from ibm_watson import AssistantV2
from ibm_cloud_sdk_core.authenticators import IAMAuthenticator
import pprint

#Authenticate using AssistantV2
authenticator = IAMAuthenticator("dxTC5gCR9oHI657BpJRxOstetuWs_xEk6uq985jMslqx")
assistant = AssistantV2(
    version='2020-04-01',
    authenticator=authenticator)
    
#Different URL than the library documentation
assistant.set_service_url('https://api.us-south.assistant.watson.cloud.ibm.com/')

response = assistant.create_session(assistant_id='947f1635-499f-4ea7-b469-0715287c5f84').get_result()

print(json.dumps(response, indent=2))

response = assistant.message(
    assistant_id='947f1635-499f-4ea7-b469-0715287c5f84',
    session_id='38eecc3c-a98a-4504-b62f-6c23a18ddb45',
    input={
        'message_type':'text', 
        'text' : 'I need help with snapshot creation' , 
        'options':{ 
            'return_context':True 
        }
    },
    context={
        "skills":{ 
            "main skill":{ 
                "user_defined":{ 
                    "username":"Kiran" 
                }
            }
        }
    }
).get_result()
 
print(json.dumps(response, indent=2))


{
  "output": {
    "intents": [
      {
        "intent": "Snapshot_Creation",
        "confidence": 1
      }
    ],
    "entities": [],
    "generic": [
      {
        "title": "I understand that you have issues with snapshot creation. Below are the most common and popular errors prevailing since past 3 months regarding snapshot creation. Please choose what's your error?",
        "options": [
          {
            "label": "Invalid snapshot configuration",
            "value": {
              "input": {
                "text": "Invalid"
              }
            }
          },
          {
            "label": "File Lock",
            "value": {
              "input": {
                "text": "Lock"
              }
            }
          },
          {
            "label": "No space Left",
            "value": {
              "input": {
                "text": "Out of Space"
              }
            }
          },
          {
            "label": "CID/PID mismatch",
            "value": {
              "input": {
                "text": "Disk Chain Inconsistency"
              }
            }
          },
          {
            "label": "Error Not listed",
            "value": {
              "input": {
                "text": "Error Not Listed"
              }
            }
          },
          {
            "label": "Go to the main menu",
            "value": {
              "input": {
                "text": "Main Menu"
              }
            }
          }
        ],
        "response_type": "option"
      }
    ]
  },
  "user_id": "38eecc3c-a98a-4504-b62f-6c23a18ddb45",
  "context": {
    "global": {
      "system": {
        "session_start_time": "2022-09-03T06:19:45.365Z",
        "turn_count": 1,
        "user_id": "38eecc3c-a98a-4504-b62f-6c23a18ddb45",
        "state": "eyJpZCI6Ijk0N2YxNjM1LTQ5OWYtNGVhNy1iNDY5LTA3MTUyODdjNWY4NCIsInNraWxscyI6W3siY29uZmlnIjp7ImFjdGlvbnMiOmZhbHNlLCJ3b3Jrc3BhY2VfaWQiOiJjMGQ2ZmNjNy01MDRjLTQxMTgtODAzYy03NDdkYzYyZTdhYWIiLCJza2lsbF9yZWZlcmVuY2VfaWQiOm51bGx9LCJkaXNhYmxlZCI6bnVsbCwibGFuZ3VhZ2UiOiJlbiIsInNraWxsX3R5cGUiOiJkaWFsb2ciLCJza2lsbF9yZWZlcmVuY2UiOiJtYWluIHNraWxsIiwic2tpbGxfc25hcHNob3RfaWQiOm51bGwsInNraWxsX3NuYXBzaG90X25hbWUiOm51bGwsIndvcmtlcl9kZWZpbml0aW9uX2lkIjoiYzBkNmZjYzctNTA0Yy00MTE4LTgwM2MtNzQ3ZGM2MmU3YWFiIn1dLCJsYW5ndWFnZSI6bnVsbCwidGVuYW50X2lkIjoiZmMzNWVhZjAtNGI5YS00ZTVkLTllYTctYTI1ODFlY2M3YjFlIiwiZW52aXJvbm1lbnQiOm51bGwsImRlZmF1bHRfaW5zdGFuY2UiOnRydWUsImRpc2FibGVfZmFsbGJhY2siOnRydWUsImFnZW50X2RlZmluaXRpb25faWQiOiI5NDdmMTYzNS00OTlmLTRlYTctYjQ2OS0wNzE1Mjg3YzVmODQiLCJwYXJlbnRfYXNzaXN0YW50X2lkIjpudWxsfQ=="
      },
      "session_id": "38eecc3c-a98a-4504-b62f-6c23a18ddb45"
    },
    "skills": {
      "main skill": {
        "user_defined": {
          "username": "Kiran"
        },
        "system": {}
      }
    }
  }
}
answer = assistant.message(
    assistant_id='947f1635-499f-4ea7-b469-0715287c5f84',
    session_id='38eecc3c-a98a-4504-b62f-6c23a18ddb45',
    input={
        'message_type':'text', 
        'text' : 'Invalid snapshot configuration' , 
        'options':{ 
            'return_context':True 
        }
    }
).get_result()
 
print(json.dumps(answer, indent=2))
{
  "output": {
    "intents": [
      {
        "intent": "Invalid_snapshot_configuration",
        "confidence": 1
      }
    ],
    "entities": [
      {
        "entity": "Invalid_Snapshot",
        "location": [
          0,
          30
        ],
        "value": "invalid snapshot configuration detected",
        "confidence": 1
      }
    ],
    "generic": [
      {
        "title": "For the error occurred in your environment, please ensure there are no RDM/sharing disks attached and the mode of the scsi controller are set to normal. For more info, please refer the VMware KB https://kb.vmware.com/s/article/80246. Was this helpful ? ",
        "options": [
          {
            "label": "Yes",
            "value": {
              "input": {
                "text": "Yes"
              }
            }
          },
          {
            "label": "No",
            "value": {
              "input": {
                "text": "No"
              }
            }
          }
        ],
        "response_type": "option"
      }
    ]
  },
  "user_id": "38eecc3c-a98a-4504-b62f-6c23a18ddb45",
  "context": {
    "global": {
      "system": {
        "session_start_time": "2022-09-03T06:19:45.365Z",
        "turn_count": 2,
        "user_id": "38eecc3c-a98a-4504-b62f-6c23a18ddb45",
        "state": "eyJpZCI6Ijk0N2YxNjM1LTQ5OWYtNGVhNy1iNDY5LTA3MTUyODdjNWY4NCIsInNraWxscyI6W3siY29uZmlnIjp7ImFjdGlvbnMiOmZhbHNlLCJ3b3Jrc3BhY2VfaWQiOiJjMGQ2ZmNjNy01MDRjLTQxMTgtODAzYy03NDdkYzYyZTdhYWIiLCJza2lsbF9yZWZlcmVuY2VfaWQiOm51bGx9LCJkaXNhYmxlZCI6bnVsbCwibGFuZ3VhZ2UiOiJlbiIsInNraWxsX3R5cGUiOiJkaWFsb2ciLCJza2lsbF9yZWZlcmVuY2UiOiJtYWluIHNraWxsIiwic2tpbGxfc25hcHNob3RfaWQiOm51bGwsInNraWxsX3NuYXBzaG90X25hbWUiOm51bGwsIndvcmtlcl9kZWZpbml0aW9uX2lkIjoiYzBkNmZjYzctNTA0Yy00MTE4LTgwM2MtNzQ3ZGM2MmU3YWFiIn1dLCJsYW5ndWFnZSI6bnVsbCwidGVuYW50X2lkIjoiZmMzNWVhZjAtNGI5YS00ZTVkLTllYTctYTI1ODFlY2M3YjFlIiwiZW52aXJvbm1lbnQiOm51bGwsImRlZmF1bHRfaW5zdGFuY2UiOnRydWUsImRpc2FibGVfZmFsbGJhY2siOnRydWUsImFnZW50X2RlZmluaXRpb25faWQiOiI5NDdmMTYzNS00OTlmLTRlYTctYjQ2OS0wNzE1Mjg3YzVmODQiLCJwYXJlbnRfYXNzaXN0YW50X2lkIjpudWxsfQ=="
      },
      "session_id": "38eecc3c-a98a-4504-b62f-6c23a18ddb45"
    },
    "skills": {
      "main skill": {
        "user_defined": {
          "username": "Kiran",
          "Snapshot_Creation_Error1": "invalid snapshot configuration detected:(invalid snapshot configuration detected)"
        },
        "system": {}
      }
    }
  }
}
answer = assistant.message(
    assistant_id='947f1635-499f-4ea7-b469-0715287c5f84',
    session_id='5818e6a5-d85e-4c4b-8d52-363eda791940',
    input={
        'message_type':'text', 
        'text' : 'NFS mount issue' , 
        'options':{ 
            'return_context':True 
        }
    }
).get_result()
 
print(json.dumps(answer, indent=2))
{
  "output": {
    "intents": [
      {
        "intent": "NFS_Mount_Issue",
        "confidence": 0.49208505153656007
      }
    ],
    "entities": [
      {
        "entity": "NFS_Datastore_Mount",
        "location": [
          0,
          15
        ],
        "value": "nfs mount issue",
        "confidence": 1
      }
    ],
    "generic": [
      {
        "title": "For this error, please ensure the host has accessibility to the NFS server and all required ports are open. is not a part of any of the replication lun and the datastore uuid is different/unique. You may refer to the vmware kb https://kb.vmware.com/s/article/1005948 for further info. Did this resolution help ?",
        "options": [
          {
            "label": "Yes",
            "value": {
              "input": {
                "text": "Yes"
              }
            }
          },
          {
            "label": "No",
            "value": {
              "input": {
                "text": "No"
              }
            }
          }
        ],
        "response_type": "option"
      }
    ]
  },
  "user_id": "5818e6a5-d85e-4c4b-8d52-363eda791940",
  "context": {
    "global": {
      "system": {
        "session_start_time": "2022-07-26T05:06:27.837Z",
        "turn_count": 3,
        "user_id": "5818e6a5-d85e-4c4b-8d52-363eda791940",
        "state": "eyJpZCI6Ijk0N2YxNjM1LTQ5OWYtNGVhNy1iNDY5LTA3MTUyODdjNWY4NCIsInNraWxscyI6W3siY29uZmlnIjp7ImFjdGlvbnMiOmZhbHNlLCJ3b3Jrc3BhY2VfaWQiOiJjMGQ2ZmNjNy01MDRjLTQxMTgtODAzYy03NDdkYzYyZTdhYWIiLCJza2lsbF9yZWZlcmVuY2VfaWQiOm51bGx9LCJkaXNhYmxlZCI6bnVsbCwibGFuZ3VhZ2UiOiJlbiIsInNraWxsX3R5cGUiOiJkaWFsb2ciLCJza2lsbF9yZWZlcmVuY2UiOiJtYWluIHNraWxsIiwic2tpbGxfc25hcHNob3RfaWQiOm51bGwsInNraWxsX3NuYXBzaG90X25hbWUiOm51bGwsIndvcmtlcl9kZWZpbml0aW9uX2lkIjoiYzBkNmZjYzctNTA0Yy00MTE4LTgwM2MtNzQ3ZGM2MmU3YWFiIn1dLCJsYW5ndWFnZSI6bnVsbCwidGVuYW50X2lkIjoiZmMzNWVhZjAtNGI5YS00ZTVkLTllYTctYTI1ODFlY2M3YjFlIiwiZW52aXJvbm1lbnQiOm51bGwsImRlZmF1bHRfaW5zdGFuY2UiOnRydWUsImRpc2FibGVfZmFsbGJhY2siOnRydWUsImFnZW50X2RlZmluaXRpb25faWQiOiI5NDdmMTYzNS00OTlmLTRlYTctYjQ2OS0wNzE1Mjg3YzVmODQiLCJwYXJlbnRfYXNzaXN0YW50X2lkIjpudWxsfQ=="
      },
      "session_id": "5818e6a5-d85e-4c4b-8d52-363eda791940"
    },
    "skills": {
      "main skill": {
        "user_defined": {
          "username": "Kiran",
          "Snapshot_Creation_Error1": "invalid snapshot configuration detected:(invalid snapshot configuration detected)",
          "Datastore_Mount_Error3": "nfs mount issue"
        },
        "system": {}
      }
    }
  }
}




