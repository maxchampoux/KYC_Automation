# KYC_Automation
API &amp; Webhook to automate the KYC process of iBanFirst.

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
| activityCode | String(5) | Required | Your business activity as registered with local authorities. To see a full list of state code, please refer to [this site](https://www.insee.fr/fr/information/2406147). |
| activitydescription | String(500) | Required | A customised description of your activity. |
| reason | String(200)  | Required | Why you want to open an account with us. To see a full list of reasons, please refer to the [Reason List](../conventions/formattingConventions.md#type_reasonList) |
| reasonDescription | String(500) | Optional | A customised description of your reason. This field is mandatory when you select the label "other" in the reason List. |
| international ([Transaction Object](../objects/objects.md#transaction_object)) | Binary | Required | If you want to unlock the international module and allow to proceed cross-boarder transactions. |
| consolidatedVolume ([Transaction Object](../objects/objects.md#transaction_object)) | [Amount Object](../objects/objects.md#amount_object) | Optional | The consolidated volume of transaction per year you expect to proceed with us. Required if the field international is true. |
| outgoingVolume ([Transaction Object](../objects/objects.md#transaction_object)) | [Amount Object](../objects/objects.md#amount_object) | Optional | The volume of transaction per year you expect to proceed in a specific currency. |
| outgoingCountry ([Transaction Object](../objects/objects.md#transaction_object)) | [CountryNumberCurrency Object](../objects/objects.md#amount_object) | Required | The beneficiary country you expect to proceed transaction to in a specific currency in a year. And the number of transactions related. |
| incomingVolume ([Transaction Object](../objects/objects.md#transaction_object)) | [Amount Object](../objects/objects.md#amount_object) | Required | The volume of transaction per year you expect to receive in a specific currency. |
| incomingCountry ([Transaction Object](../objects/objects.md#transaction_object)) | [Country Number Currency Object](../objects/objects.md#countryNumberCurrency_object) | Required | The beneficiary country you expect to reveive transaction from in a specific currency in a year. And the number of transactions related. |
| acquiringChannel | string(200) | Required | The channel of acquisition you have used to create you account. To see the full list of acquiring channel, please refer to the [Acquiring Channel List](../conventions/formattingConventions.md#acquiringChanel_list) |
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

* [Reason List](#reason_list) 
* [Transaction Object](#transaction_object) 
* [Amount Object](#amount_object) 
* [Country Number Currency Object](#CountryNumberCurrency_object) 
* [Acquiring Channel List Object](#acquiringChanelList_object)

## Details ##


#### <a id="reason_list"></a> Reason List ####

We need to know WHY you are opening an account with us?
The proposed Reason List is set-out as follow:

**List resources:**

| Code | Label |
|-------|------------|
| internationalTransfer | Interested in having the functionality of Cross-border wire transfer |
| forexTrades | Interested in having the functionality of Foreign exchange trades |
| sepaTransfer | Interested in having the functionality of Sepa Credit Transfer. |
| managementInterface | Interested in having an online interface to management day-to-day banking transactions |
| costBank | My bank is too expensive for me. |
| reactivityBank | My bank is too slow for me. |
| complexityBank | My bank is too complex for me. |
| fintech | Interested in fintechs. |
| other | Other. To describe. |

<hr />

#### <a id="amount_object"></a> Amount Object ####

When an amount of currency is specified as part of a JSON body, it is encoded as an object with the following fields:

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

#### <a id="acquiringChanelList_object"></a> Acquiring Channel List Object ####

We need to know by HOW you had known us?
The proposed Acquiring Channel List is set-out as follow:

**List resources:**

| Code | Label |
|-------|------------|
| browser | By searching with my web browser. |
| webAdvertising | By seing one of our comercials while browsing the web. |
| webExternal | By seing one of our comercials in radio, TV or press. |
| physicalDisplay | By seing one of our comercials physically displayed in the street. |
| wordMouth | By a friend, collaborator or family. |
| sponsorship | I have a coupon. |
| other | Other. To describe. |

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

