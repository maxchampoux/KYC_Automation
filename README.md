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









## GETTING STARTED WITH IBANFIRST KYC API ##

#### 1. Submit your Know Your Customer Report and Get started with you iBanFirst account ####

Just a quick questionnaire before you have access to our services.

[`POST /kyc/gettingStarted`](/services/kyc.md#post_kycGettingStarted)
