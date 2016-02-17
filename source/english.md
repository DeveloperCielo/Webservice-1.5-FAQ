---
title: Frequently Asked Questions

toc_footers:
  - <a href='/Webservice-1.5/'>Webservice Manual 1.5</a>
  - <a href='/Webservice-1.5-Processamento-em-lote/'>Batch Processing</a>

search: true
---

# Frequently Asked Questions

## How does the solution Web service 1.5 Cielo works?

The Web service solution Cielo e-commerce platform was developed with XML technology, which is market standard and independent of the technology used by our customers. Thus, it is possible to integrate it using various programming languages, such as ASP, ASP. Net,  Java, PHP, Ruby, Python, etc.

## It takes some proprietary software, such as DLLs, to integrate?

No. The lack of proprietary applications is one of the features of the solution: It's not necessary to install applications on the virtual store environment **under any circumstances**.

## What kind of content is sent in integration?

The integration is accomplished through available services such as Web Services. The employee model is quite simple: there is a unique URL (endpoint) which receives POSTs via HTTPs and depending on the submitted XML format, an operation is performed.

## As the Web service Cielo know that the request is from my store?

All requests Cielo Web Service **must contain the merchant authentication node**, composed by the number of credential and access key provided by Cielo at the time of affiliation.

## What is a transaction?

The central element of Cielo E-commerce is the transaction created from an HTTP request to the Web service Cielo. The unique ID of a transaction in Cielo is done through the TID field, which is present in the return of authorization messages. This field is essential to consult, catches and cancellations.

## What types of errors can occur during integration?

When the transaction is invalid, we can classify errors into two types:

•	**Syntactical errors:** occur when the XML message does not respect the rules defined in ecommerce.xsd file. For example, a letter in a number field or the absence of a required value;

•	**Semantic errors:** occur when a request requesting an operation not supported for a given transaction. For example, try to capture an unauthorized transaction, or even cancel a transaction already canceled.

Error messages always bring additional information to facilitate troubleshooting.

## How do I direct authorization?

Direct authorization is characterized as a transaction where there is no carrier authentication, either by choice (and risk) of the retailer, either because the flag or issuer is not supported. The direct authorization may be done in two ways: traditional (with card data) or via a token.

## How I do a recurring authorization?

The applicant authorization may be made in two ways: by sending a pre-registered token, or through a card. A recurring transaction is practically the same as traditional transaction, the changes consist of the issuer rules and the flag used to authorize or deny a transaction. Another difference is related to Renova Easy.

###Is it possible to capture a moment after authorization?

A transaction authorized only generates credit for the shop if it is captured. So every sale that the retailer wants to carry out will need to perform the capture (or confirmation) of the transaction.

For sales in Credit mode, this confirmation can occur in two stages:

•	Immediately after authorization (total catch);
•	Subsequent to authorization (total or partial capture).

In the first case, it is not necessary to send a capture request because it is done automatically by Cielo after transaction authorization. For that, it needs to configure the transaction request by setting the "true" value for the TAG, as seen in "Creating a transaction" section.

In the second case, you must make a "subsequent capture" through a new request to Cielo Web service to confirm the transaction and receive the value of the sale.

<aside class="warning"><strong>Atenção!</strong>: In the debit mode there is no such option: all authorized debit transaction is captured automatically.</aside>

## Can I cancel a transaction?

The cancellation is used when the tenant decides not to carry out a purchase order, either due to insufficient stock, for withdrawal of purchase by the consumer, or any other reason. Its use mainly necessary to make up the transaction is captured,  it will debit the carrier bill, if it is not canceled.

<aside class="notice">If the transaction is only allowed and the store wants to cancel it, the cancellation request is not necessary because after the deadline capture expires, it is automatically canceled by the system.</aside>

## There is a testing environment for integration?

Integration testing should be performed prior to approval for development (coding) of the solution. Para isso, deve-se considerar o seguinte ambiente como EndPoint do Webservice: [https://qasecommerce.cielo.com.br/servicos/ecommwsec.do](https://qasecommerce.cielo.com.br/servicos/ecommwsec.do)

To facilitate the development available for testing two keys, one for each integration mode. Based on the initial settings made during its accreditation, choose the correct data to perform the tests:

|NUMBER OF COMMERCIAL ESTABLISHMENT|KEY TESTS|
|--------------------------------|---------------|
|1006993069|25fbb99741c739dd84d7b06ec78c9bac718838630f30b112d033ce2e621b34f3|

<aside class="notice">The test environment should only be used by testing establishments listed in the table above. The use of original property will generate data not possible to trace transactions, generating incorrect results. In the test environment, use the credentials for testing, the production environment, use the original property data.</aside>

## Is there any rule for reading cards?

Reading the card data in their own environment is controlled by rules defined by the security program imposed by the card brands.

For Visa, this program is known as AIS (Account Information Security) PCI. For more information visit: [www.cielo.com.br](www.cielo.com.br) > Services> Security Services> AIS - Safety Program Information, or contact us.

MasterCard for the security program is the SDP (Site Data Protection) PCI. For more information visit: [http://www.mastercard.com/us/sdp/index.html](http://www.mastercard.com/us/sdp/index.html), or contact us.

Furthermore, once the requirements are met, at the time of e-commerce accreditation should be mentioned the choice of reading the card in the store.

