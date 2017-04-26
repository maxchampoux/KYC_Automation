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
URL: /kyc/gettingStarted
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
| consolidatedVolume ([Transaction Object](../objects/objects.md#transaction_object)) | ([Amount Object](../objects/objects.md#amount_object) | Required | The consolidated volume of transaction per year you expect to proceed with us. |
| outgoingVolume ([Transaction Object](../objects/objects.md#transaction_object)) | ([Amount Object](../objects/objects.md#amount_object) | Optional | The volume of transaction per year you expect to proceed in a specific currency. This field is mandatory if you have an expected consilidate volume higher than EUR 100.000,00 |
| outgoingCountry ([Transaction Object](../objects/objects.md#transaction_object)) | ([CountryNumberCurrency Object](../objects/objects.md#amount_object) | Optional | The beneficiary country you expect to proceed transaction to in a specific currency in a year. And the number of transactions related. This field is mandatory if you have an expected consilidate volume higher than EUR 100.000,00 |
| incomingVolume ([Transaction Object](../objects/objects.md#transaction_object)) | ([Amount Object](../objects/objects.md#amount_object) | Optional | The volume of transaction per year you expect to receive in a specific currency. This field is mandatory if you have an expected consilidate volume higher than EUR 100.000,00 |
| incomingCountry ([Transaction Object](../objects/objects.md#transaction_object)) | ([CountryNumberCurrency Object](../objects/objects.md#amount_object) | Optional | The beneficiary country you expect to reveive transaction from in a specific currency in a year. And the number of transactions related. This field is mandatory if you have an expected consilidate volume higher than EUR 100.000,00 |
| acquiringChannel | ([Acquiring Channel List Object](../objects/objects.md#acquiringChanelList_object) | Required | The channel of acquisition you have used to create you account. This field is mandatory if you have an expected consilidate volume higher than EUR 100.000,00 |
| acquiringChannel | ([Acquiring Channel List Object](../objects/objects.md#acquiringChanelList_object) | Required | The channel of acquisition you have used to create you account. This field is mandatory if you have an expected consilidate volume higher than EUR 100.000,00 |









## GETTING STARTED WITH IBANFIRST KYC API ##

#### 1. Submit your Know Your Customer Report and Get started with you iBanFirst account ####

Just a quick questionnaire before you have access to our services.

[`POST /kyc/gettingStarted`](/services/kyc.md#post_kycGettingStarted)
