# KYC_Automation
API &amp; Webhook to automate the KYC process of iBanFirst

## Routes ##

| Route | Description |
|-------|-------------|
| [`POST /kyc/gettingStarted`](#post_kycGettingStarted) | Submit the getting started KYC questionnaire. |

<hr />

## <a id="post_kycGettingStarted"></a> Submit the Getting Started - KYC questionnaire. ##

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
| incomingCountry ([Transaction Object](../objects/objects.md#transaction_object)) | ([Country Number Currency Object](../objects/objects.md#countryNumberCurrency_object) | Optional | The beneficiary country you expect to reveive transaction from in a specific currency in a year. And the number of transactions related. This field is mandatory if you have an expected consilidate volume higher than EUR 100.000,00 |
| acquiringChannel | ([Acquiring Channel List Object](../objects/objects.md#acquiringChanelList_object) | Required | The channel of acquisition you have used to create you account. This field is mandatory if you have an expected consilidate volume higher than EUR 100.000,00 |
| trueData | Binary | Required | You confirm that the data sent in this form is true and accurate. |

**Example:**
```js
{
  "activityCode": "TBD",
  "reason" : "other",
  "reasonDescription": "fan du projet",
  "international": true,
  "transaction": {
    "consolidatedVolume": {
      "amount": {
        "value": 1000.00,
        "currency": "EUR",
       }
    }
    "acquiringChannel": "browser",
    "trueData": true,
   }
}
```


<hr />

# API Objects  

* [NAF Code Object](#NAFCode_object) 
* [Reason Object](#reason_object) 
* [Transaction Object](#transaction_object) 
* [Amount Object](#amount_object) 
* [Country Number Currency Object](#CountryNumberCurrency_object) 
* [Address Object](#address_object)
* [Account Object](#account_object)
* [Phone Object](#phone_object)
* [Individual Name Object](#individualName_object)
* [Amount Object](#amount_object)

## Details ##

#### <a id="NAFCode_object"></a> NAF Code Object ####

TBD. List to be provided by Product.


<hr />

#### <a id="reason_object"></a> Reason Object ####

TBD. List to be provided by Product.


<hr />

#### <a id="transaction_object"></a> Transaction Object ####

TBD. List to be provided by Product.


<hr />

#### <a id="amount_object"></a> Amount Object ####

When an amount of currency is specified as part of a JSON body, it is encoded as an object with the following fields:


<hr />

**Object resources:**

| Field | Type | Description |
|-------|------|-------------|
| value  | [Quoted Decimal](../conventions/formattingConventions.md#type_quoteddecimal) | The quantity of the currency. |
| currency | [Currency](../conventions/formattingConventions.md#type_currency) | The three-digit code specifying the currency related to the amount. |

**Example:**

```js
"amount": {
	"value": "10000.00",
	"currency": "GBP"
}
```

<hr />

#### <a id="CountryNumberCurrency_object"></a> Country Number Currency Object ####

When an amount of currency is specified as part of a JSON body, it is encoded as an object with the following fields:

**Object resources:**

| Field | Type | Description |
|-------|------|-------------|
| country | [Country](../conventions/formattingConventions.md#type_country) | The country of the counterparty of the transaction.|
| currency | [Currency](../conventions/formattingConventions.md#type_currency) | The three-digit code specifying the currency related to the amount. |
| number | [Quoted Decimal](../conventions/formattingConventions.md#type_quoteddecimal) | The number of transaction expected with this country.|

**Example:**

```js
"amount": {
	"country": "US",
	"number": "10000.00",
	"currency": "GBP"
}
```

<hr />


## GETTING STARTED WITH IBANFIRST KYC API ##

#### 1. Submit your Know Your Customer Report and Get started with you iBanFirst account ####

Just a quick questionnaire before you have access to our services.

[`POST /kyc/gettingStarted`](/services/kyc.md#post_kycGettingStarted)
