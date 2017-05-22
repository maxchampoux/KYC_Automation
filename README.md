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
| reason | String(200)  | Required | Why you want to open an account with us. To see a full list of reasons, please refer to the [Reason List](#type_reasonList) |
| accountancyCurrency | [Currency](../conventions/formattingConventions.md#type_currency) | Required | The three-digit code specifying the accountancy currency of the client. |
| currencyAccountsToOpen | Array<[Currency](../conventions/formattingConventions.md#type_currency)> | Required |  array of three-digit code specifying the currencies of account the client wants to open with us. |
| reasonDescription | String(500) | Optional | A customised description of your reason. This field is mandatory when you select the label "other" in the reason List. |
| international (Transaction Object) | Binary | Required | If you want to unlock the international module and allow to proceed cross-boarder transactions. |
| consolidatedVolume (Transaction Object) | [Amount Object](#amount_object) | Optional | The consolidated volume of transaction per year you expect to proceed with us. Required if the field international is true. |
| outgoingVolume (Transaction Object) | [Amount Object](#amount_object) | Optional | The volume of transaction per year you expect to proceed in a specific currency. |
| outgoingCountry (Transaction Object) | [Country Number Currency Object](#countryNumberCurrency_object) | Required | The beneficiary country you expect to proceed transaction to in a specific currency in a year. And the number of transactions related. |
| incomingVolume (Transaction Object) | [Amount Object](#amount_object) | Required | The volume of transaction per year you expect to receive in a specific currency. |
| incomingCountry (Transaction Object) | [Country Number Currency Object](#countryNumberCurrency_object) | Required | The beneficiary country you expect to reveive transaction from in a specific currency in a year. And the number of transactions related. |
| acquiringChannel | string(200) | Required | The channel of acquisition you have used to create you account. To see the full list of acquiring channel, please refer to the [Acquiring Channel List](#acquiringChanel_list) |
| documentIdentityCheck | [Document Object]#type_document) | Optional | The document you must send to us with an additional proof of identity when kyc scoring risk is medium or higher. |
| trueData | Binary | Required | You confirm that the data sent in this form is true and accurate. |

**Example:**
```js
{
  "activityCode": "TBD",
  "reason" : "other",
  "reasonDescription": "fan du projet",
  "accountancyCurrency" "EUR",
  "currencyAccountsToOpen": "EUR",
  "international": true,
  "transaction": {
    "consolidatedVolume": {
      "amount": {
        "value": 1000.00,
        "currency": "EUR",
       }
    }
    "acquiringChannel": "browser",
    "documentIdentityCheck": {
			"documentType": "identityCheck",
			"tag": "identityCheck.pdf",
			"file": "iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAMAAAAoLQ9TAAAABGdBTUEAANbY1E9YMgAAABl0RVh0U29mdHdhcmUAQWRvYmUgSW1hZ2VSZWFkeXHJZTwAAAGAUExURQxS1ISawgBGyebt+VZ6vmGK1miV58bO3O3u8gRJykV31E170brM7RNSyXuRukJ64jNkvl2H1Xmh6wFK0fT19+vw++rs8QFGxlt/xOLm7KOwylSB01l7urbB1LW/0lJ/0py25vDw8+ju+oucv9PZ4yJezUh40oOo7zJpzSljzV6I1lmE1Ep50e7z/PDx9Ky4zfb2+JOt3FF+0hlc2AlLxjxvzUFptEd406+60EZ73NTf9EhxvWGP5XeOuixm0z9x0HeQvSxlzVB90xZZ1h5d0unr7+7w85qx3s/V4Stgwo+x8bnC1b/I2Vp6tliC0ViD1H6ZzF6G0UyD6GSAtVB+1Chm2drf5yVgzZy68kh931F6xlR/zuDp+tbg9N/o+l6Bw8HJ2iFk4DRw4YCWv0p601KF5V6P6T9puW+Ku4qewnCIt3iOuE980WSL0iVk2Stfvixo1jlz3Vt9vl5+uk11wPPz9VyDzAhO0MnQ3S5lyYeg0FB90aG+80l40Nzg6P///xIhGr0AAACAdFJOU/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////8AOAVLZwAAAPdJREFUeNpiqAcBPRVvWQ8OMJMBiEXkbIvjJWSy9PUgAmLKRYFarKzafix8kiABA2UJQW1WHh5BeemobA6ggByLv7Q8a6yVIDc3d4lUPUMpX7SRUXUOqxa3jo5abbArQ5ivEze3jqCCQoiGo2Z4OjsDO0sKl72GuaiSpri4OFO+BQO7tSqvibgqM7MLExB4WjDUmXGKM3HaKSkVlAsLCwtUMIhk8HIyuFiKikbmGTMwyIgx1MsKOIcW2ujqsvEnJVZKgRzGaMqfKhQXo54WxOXgBnZ6ZhmbekSNl1BusiTUc7KMAYbuVYwWUM8BgaJKgo8KxPsAAQYAJwc98FQAQqUAAAAASUVORK5CYII=",
		},
    "trueData": true,
   }
}
```


<hr />

# API Objects  

* [Amount Object](#amount_object) 
* [Country Number Currency Object](#CountryNumberCurrency_object) 

## Details ##

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


#### <a id="CountryNumberCurrency_object"></a> Country Number Currency Object ####

When an amount of currency is specified as part of a JSON body, it is encoded as an object with the following fields:

**Object resources:**

| Field | Type | Description |
|-------|------|-------------|
| country | [Country](../conventions/formattingConventions.md#type_country) | The country of the counterparty of the transaction.|
| currency | [Currency](../conventions/formattingConventions.md#type_currency) | The three-digit code specifying the currency related to the amount. |
| number | [Number](../conventions/formattingConventions.md#type_number) | The number of transactions expected with this country.|

**Example:**

```js
"amount": {
	"country": "US",
	"number": "10000.00",
	"currency": "GBP"
}
```

<hr />

<hr />

# API lists #  

* [Reason List](#reason_list) 
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
