# KYC_Automation
API &amp; Webhook to automate the KYC process of iBanFirst

## Routes ##

| Route | Description |
|-------|-------------|
| [`POST /kyc/gettingStarted`](#post_kycGettingStarted) | Submit the getting started KYC questionnaire. |

<hr />

## <a id="post_kycGettingStarted"></a> Submit the getting started KYC questionnaire. ##

```
Method: POST 
URL: /companies/
```

Congrats! You just opened an account with us, and then we want to know a bit more about you. Just a few questions to answer before enjoying your iBanFirst account. 

**Parameters:**

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| activityCode | [NAF Code Object](../objects/objects.md#NAFCode_object) | Required | Your business activity as registered with local authorities. |
| activitydescription | String(500) | Optional | A customised description of your activity. This field is mandatory when you select the label "other" in the activityCode List. |
| reason | [Reason Object](../objects/objects.md#reason_object) | Required | Why you want to open an account with us. |
| reasonDescription | String(500) | Optional | A customised description of your reason. This field is mandatory when you select the label "other" in the reason List. |
| international ([Transaction Object](../objects/objects.md#transaction_object)) | Binary | Required | If you want to unlock the international module and allow to proceed cross-boarder transactions. |
| volume ([Transaction Object](../objects/objects.md#transaction_object)) | ([Amount Object](../objects/objects.md#amount_object) | Required | The volume of transaction per year you expect to proceed with us. |









## GETTING STARTED WITH IBANFIRST KYC API ##

#### 1. Submit your Know Your Customer Report and Get started with you iBanFirst account ####

Just a quick questionnaire before you have access to our services.

[`POST /kyc/gettingStarted`](/services/kyc.md#post_kycGettingStarted)
