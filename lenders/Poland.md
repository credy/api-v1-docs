![Logo](../assets/img/logo.png?raw=true)

# Credy API for receiving leads

## Introduction

Traffic Control is a company that specializes on the quality lead generation for lenders.

This document further describes how to integrate API to receive leads from Traffic Control to your loan administration system.

Should you have any questions, please do not hesitate to contact the IT manager at it@credy.eu.

## General information

Process starts when lead is received in Traffic Control. Based on algorithms TC calculates the client who will get the lead and makes request to client’s system. See API method* receiveClient()*. Traffic Control waits immediate response that client is accepted or rejected.

## API Methods

**receiveClient()**

Lead is received into Client’s system. TC sends lead to Client system via the url client has provided when accepting agreement.


Method: POST

Content-Type: JSON

**Request fields**

<table>
  <tr>
    <td>Parameter name</td>
    <td>Type</td>
    <td>Description</td>
  </tr>
  <tr>
    <td>lead_id</td>
    <td>String</td>
    <td>Required

The application ID in TC database</td>
  </tr>
  <tr>
    <td>client_id</td>
    <td>Integer</td>
    <td>Required

Client ID on TC database</td>
  </tr>
  <tr>
    <td>loan_sum</td>
    <td>Integer</td>
    <td>Required
Must be number

Loan amount</td>
  </tr>
  <tr>
    <td>loan_period</td>
    <td>Integer</td>
    <td>Required
Must be number

Loan period in days</td>
  </tr>
  <tr>
    <td>first_name</td>
    <td>String</td>
    <td>Required
Must be string

First name</td>
  </tr>
  <tr>
    <td>last_name</td>
    <td>String</td>
    <td>Required
Must be string

Last name</td>
  </tr>
  <tr>
    <td>email</td>
    <td>String</td>
    <td>Required
Must be valid email address (MX is checked)</td>
  </tr>
  <tr>
    <td>phone</td>
    <td>String</td>
    <td>Required

Phone number without area code or spaces</td>
  </tr>
  <tr>
    <td>gender</td>
    <td>ENUM</td>
    <td>Required

Must be one of following:
MALE
FEMALE</td>
  </tr>
  <tr>
    <td>birth_date</td>
    <td>Date</td>
    <td>Required

Format: YYYY-mm-dd</td>
  </tr>
  <tr>
    <td>bank_account_number</td>
    <td>String</td>
    <td>Required
Must be valid IBAN

Bank account number</td>
  </tr>
  <tr>
    <td>id_card_number</td>
    <td>String</td>
    <td>Required

ID card number</td>
  </tr>
  <tr>
    <td>personal_code</td>
    <td>String</td>
    <td>Required
Must be valid PESEL

DNI / NIE of the client</td>
  </tr>
  <tr>
    <td>city</td>
    <td>String</td>
    <td>Required

City</td>
  </tr>
  <tr>
    <td>address</td>
    <td>String</td>
    <td>Required

Street</td>
  </tr>
  <tr>
    <td>house_number</td>
    <td>String</td>
    <td>Required

House number

Ex: 13A</td>
  </tr>
  <tr>
    <td>flat_number</td>
    <td>String</td>
    <td>Optional</td>
  </tr>
  <tr>
    <td>postal_code</td>
    <td>String</td>
    <td>Required

Must match pattern: /^\d{2}-{3}$/

Postal code</td>
  </tr>
  <tr>
    <td>housing_type</td>
    <td>ENUM</td>
    <td>Must be one of following: 
RENTED_ROOM
RENTED_APARTMENT_OR_HOUSE
OWN_HOUSE_OR_APARTMENT
WITH_PARENTS</td>
  </tr>
  <tr>
    <td>lives_at_registered_address</td>
    <td>ENUM</td>
    <td>TRUE
FALSE</td>
  </tr>
  <tr>
    <td>secondary_city</td>
    <td>String</td>
    <td>Required if lives_at_registered_address = FALSE</td>
  </tr>
  <tr>
    <td>secondary_address</td>
    <td>String</td>
    <td>Required if lives_at_registered_address = FALSE</td>
  </tr>
  <tr>
    <td>secondary_house_number</td>
    <td>String</td>
    <td>Required if lives_at_registered_address = FALSE</td>
  </tr>
  <tr>
    <td>secondary_flat_nu.mber</td>
    <td>String</td>
    <td>Required if lives_at_registered_address = FALSE</td>
  </tr>
  <tr>
    <td>secondary_postal_code</td>
    <td>String</td>
    <td>Required if lives_at_registered_address = FALSE</td>
  </tr>
  <tr>
    <td>neto_income</td>
    <td>Integer</td>
    <td>Must be integer

Neto income</td>
  </tr>
  <tr>
    <td>monthly_expenses</td>
    <td>Integer</td>
    <td>Monthly expenses</td>
  </tr>
  <tr>
    <td>occupation</td>
    <td>ENUM</td>
    <td>Required

Must be one of following: EMPLOYED_INDEFINITE_PERIOD
EMPLOYED_SPECIFIED_PERIOD
WRITTEN_CONTRACT_OR_ORDER
ECONOMIC_ACTIVITY
UNEMPLOYED
STUDENT
PENSIONER1
PENSIONER2
FARMER
OTHER
MATERNITY_LEAVE
BENEFITS</td>
  </tr>
  <tr>
    <td>employer</td>
    <td>String</td>
    <td>Required when occupation in list: 
employed_indefinite_period
employed_specified_period
written_contract_or_order
economic_activity

Employer name</td>
  </tr>
  <tr>
    <td>current_job_position</td>
    <td>String</td>
    <td>Required when occupation in list: 
employed_indefinite_period
employed_specified_period
written_contract_or_order

Applicant’s job position</td>
  </tr>
  <tr>
    <td>employer_city</td>
    <td>String</td>
    <td>Required when occupation in list: 
employed_indefinite_period
employed_specified_period
written_contract_or_order

Employer city</td>
  </tr>
  <tr>
    <td>employer_street</td>
    <td>String</td>
    <td>Required when occupation in list: 
employed_indefinite_period
employed_specified_period
written_contract_or_order

Employer street</td>
  </tr>
  <tr>
    <td>employer_house_number</td>
    <td>String</td>
    <td>Required when occupation in list: 
employed_indefinite_period
employed_specified_period
written_contract_or_order

Employer house number + optional appendix

Ex. 12A</td>
  </tr>
  <tr>
    <td>employer_flat_number</td>
    <td>String</td>
    <td>Optional</td>
  </tr>
  <tr>
    <td>employer_postal_code</td>
    <td>String</td>
    <td>Required when occupation in list: 
employed_indefinite_period
employed_specified_period
written_contract_or_order

Employer postal code</td>
  </tr>
  <tr>
    <td>employer_phone</td>
    <td>String</td>
    <td>Required when occupation in list: 
employed_indefinite_period
employed_specified_period
written_contract_or_order

Employer’s phone</td>
  </tr>
  <tr>
    <td>employed_since</td>
    <td>String</td>
    <td>Required when occupation in list: 
employed_indefinite_period
employed_specified_period
written_contract_or_order


Format: YYYY-MM-DD</td>
  </tr>
  <tr>
    <td>business_registration_date</td>
    <td>String</td>
    <td>Required when occupation = economic_activity</td>
  </tr>
  <tr>
    <td>tax_id_number</td>
    <td>String</td>
    <td>Required when occupation = economic_activity

Tax ID number (NIP in PL)</td>
  </tr>
  <tr>
    <td>salary_to_personal_account</td>
    <td>Boolean</td>
    <td>Required when occupation is not unemployed</td>
  </tr>
  <tr>
    <td>remuneration_deadline</td>
    <td>String</td>
    <td>Required when occupation is not unemployed

date, when money is transferred to person

Format: YYYY-MM-DD </td>
  </tr>
  <tr>
    <td>education</td>
    <td>ENUM</td>
    <td>Must be one of following:
NO_EDUCATION
BASIC_SCHOOL
HIGH_SCHOOL
INDUSTRIAL_SCHOOL
BACHELOR
MASTER
PHD</td>
  </tr>
  <tr>
    <td>university_city</td>
    <td>String</td>
    <td>Required when occupation = student</td>
  </tr>
  <tr>
    <td>university_name</td>
    <td>String</td>
    <td>Required when occupation = student</td>
  </tr>
  <tr>
    <td>car</td>
    <td>Enum</td>
    <td>Must be one of following:
NO
YES</td>
  </tr>
  <tr>
    <td>marital_status</td>
    <td>Enum</td>
    <td>Must be one of following:
SINGLE
DIVORCED
MARRIED
WITH_PARTNER
WIDOW</td>
  </tr>
  <tr>
    <td>dependant_count</td>
    <td>Integer</td>
    <td>Required

Amount of dependant persons</td>
  </tr>
  <tr>
    <td>password</td>
    <td>String</td>
    <td>Required

Randomly generated string</td>
  </tr>
  <tr>
    <td>affiliate</td>
    <td>String</td>
    <td>Required</td>
  </tr>
  <tr>
    <td>agree_terms_of_service</td>
    <td>Boolean</td>
    <td>Required

Potwierdzam zapoznanie się i akceptację regulamin serwisu Credy.pl</td>
  </tr>
  <tr>
    <td>agree_data_sharing</td>
    <td>Boolean</td>
    <td>Required

Wyrażam zgodę na udostępnienie  moich danych osobowych w celach marketingowych oraz otrzymywanie od TC i Partnerów informacji handlowej.</td>
  </tr>
  <tr>
    <td>agree_marketing_messages</td>
    <td>Boolean</td>
    <td>Optional

Wyrażam zgodę na przetwarzanie moich danych osobowych w celach marketingowych przez TC i Partnerów.</td>
  </tr>
  <tr>
    <td>timestamp</td>
    <td>Timestamp</td>
    <td>Required

UNIX timestamp</td>
  </tr>
  <tr>
    <td>hash</td>
    <td>String</td>
    <td>Required

SHA 1 hash over all data

SHA1(all request data [except hash and timestamp] + client_api_key + timestamp)

For detailed instruction, see next page (Common attributes)</td>
  </tr>
</table>


**Common attributes**

Hash is calculated over an algorithm SHA1(all request/response data [except hash and timestamp] + client_api_key + timestamp)

client_api_key is provided for each client on TC.

*Example*:

```json
{
    "client_status": "received",
    "rejected_reason": null,
    "lead_id": 123,
    "timestamp": 123454567,
    "hash": " 2027a04a46e9f41daa9625c754504c2c30a5d25e"
}
```


Calculating the verification hash is following.

sha1("client_statusreceivedreject_reasonlead_id123DBLS6jBNMd9yLZj21234567");

Algorithm: sha1(fieldvalue + api key + timestamp);

All boolean values in fieldvalue part must be represented as string (‘true’ or ‘false’).

**Expected response (in JSON)**

<table>
  <tr>
    <td>Field</td>
    <td>Type</td>
    <td>Description</td>
    <td>Required</td>
  </tr>
  <tr>
    <td>client_status</td>
    <td>ENUM</td>
    <td>Possible values: received, rejected</td>
    <td>Yes</td>
  </tr>
  <tr>
    <td>rejected_reason</td>
    <td>ENUM</td>
    <td>['duplicate','wrong_format','invalid_data','blacklisted']

duplicate - Client have already this lead
wrong_format - Received data is in wrong format
invalid_data - request data is invalid
blacklisted - customer is blacklisted in client system
invalid_ip - when endpoint url is blocked for TC</td>
    <td>No</td>
  </tr>
  <tr>
    <td>lead_id</td>
    <td>Integer</td>
    <td>Lead id from client database, when lead is accepted</td>
    <td>No</td>
  </tr>
  <tr>
    <td>timestamp</td>
    <td>Timestamp</td>
    <td>UNIX timestamp</td>
    <td>Yes</td>
  </tr>
  <tr>
    <td>hash</td>
    <td>String</td>
    <td>SHA1 hash over all data</td>
    <td>Yes</td>
  </tr>
</table>


# Versions

- 1.0 (2017-12-19): first publish