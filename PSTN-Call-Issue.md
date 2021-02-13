# PSTN Call issue (http Post request)
I'm trying to make a bot call a PSTN number. using this example: [Create peer-to-peer PSTN call with application hosted media](https://docs.microsoft.com/en-us/graph/api/application-post-calls?view=graph-rest-beta&tabs=http#example-10-create-peer-to-peer-pstn-call-with-application-hosted-media) from the 

But the request yields a:

**Call source identity invalid.**
``` json
{
    "error": {
        "code": "7507",
        "message": "Call source identity invalid.",
        "innerError": {
            "date": "2021-02-12T13:10:07",
            "request-id": "2032222f-84b9-4906-bb37-ec938d29ec45",
            "client-request-id": "2032222f-84b9-4906-bb37-ec938d29ec45"
        }
    }
}
```

# What works
It's not like nothing works. I have a functioning bot that can call a user and listen to make a 10 second voice recording ([using MS Graph github sample](https://github.com/microsoftgraph/microsoft-graph-comms-samples/tree/master/Samples/V1.0Samples/StatelessSamples/VoiceRecorderAndPlaybackBot#introduction)).

I can then use a client like postman using this example: [Create peer-to-peer VoIP call with service hosted media](https://docs.microsoft.com/en-us/graph/api/application-post-calls?view=graph-rest-beta&tabs=http#example-1-create-peer-to-peer-voip-call-with-service-hosted-media), toinitiate the call.

# What I try to make example 9 (and/or) 10 work:
## Create

![](./images/2021-02-13-13-13-20.png =300x)

## Post command:
<details>
  <summary>Click to expand!</summary>

```json
{
  "@odata.type": "#microsoft.graph.call",
  "callbackUri": "https://3bxxXXxxXX24.eu.ngrok.io/callback",
  "source": {
    "@odata.type": "#microsoft.graph.participantInfo",
    "identity": {
      "@odata.type": "#microsoft.graph.identitySet",
      "applicationInstance": {
        "@odata.type": "#microsoft.graph.identity",
        "displayName": "Teams PSTN App2",      
        "id": "5cxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxe4" //THE OBJECT ID
      }
    },
    "countryCode": null,
    "endpointType": null,
    "region": null,
    "languageId": null
  },
  "targets": [
    {
      "@odata.type": "#microsoft.graph.invitationParticipantInfo",
      "identity": {
        "@odata.type": "#microsoft.graph.identitySet",
        "phone": {
          "@odata.type": "#microsoft.graph.identity",
          "id": "+4512345678"
        }
      }
    }
  ],
  "requestedModalities": [
    "audio"
  ],
  "mediaConfig": {
    "@odata.type": "#microsoft.graph.appHostedMediaConfig",
    "blob": "<Media Session Configuration>"
  }
}
1. sdfsdf
    * dfsdf
    * sdf sdf
```
</details>


# A collapsible section with markdown
<details>
  <summary>Click to expand!</summary>
  
  ## Heading
  1. A numbered
  2. list
     * With some
     * Sub bullets
</details>