# Request for Quotes
## Description:

In Mexico, before starting a contracting process, it's mandatory to make quotes (among at least three possible suppliers) when the contract is meant to be awarded to a single supplier without competition. However, it is also possible to make these quotations in others procurement methods. The request for quotations is a process that is done in the planning stage before publishing any notice.

The "General technical guidelines for the publication, homologation and standardization of the information of the obligations established in title five and in section IV of article 31 of the General Law on Transparency and Access to Public Information, which must be disseminated by the subjects obliged in the Internet portals and in the National Transparency Platform" (page 108), consider the mandatory publication of certain information on quotation process.

In particular, the guidelines include the publication of the following information:
Name of the possible suppliers participating in the quotations.
Amount of the quotations.

Field yes / no to indicate if quotes are made in the procurement process.

Thus, with the aim of match the Open Contracting Data Standard (OCDS) with the transparency obligations in Mexico, and therefore, with the Transparency Obligations Portals System (SIPOT) administered by the National Institute of Transparency, Access to Information and Protection of Personal Data (INAI), we consider necessary to develop an extension that includes the information related to the quotation process.

In this context, the Public Service Secretariat (SFP) considers the inclusion of additional attributes to those established by the regulations in transparency, since the CompraNet system consider the generation of other information that can serve as a basis for a better understanding of the quotations processes.

## Proposal:

Add an array to the planning object. This array must contain the following attributes:

### Party Roles
- invitedSupplier
- issuingSupplier

### Schema
- Planning {object} 
  - hasQuotes (boolean, null)
  - requestsForQuotes [array]
    - requestForQuotes {object}
      - id (string, integer)
      - title (string, null)
      - description (string, null)
      - period {object} 
        - $ref : #/definitions/Period
      - items [array] 
        - $ref : #/definitions/Item
      - invitedSuppliers [array]
        - $ref : #/definitions/OrganizationReference
      - quotes [array] 
        - Quote {object}
          - id (string, integer)
          - description (string, null)
          - date (string, null) (date-time)
          - items [array]
            - $ref : #/definitions/Item
          - value {object}
            - $ref : #/definitions/Value
          - quotePeriod {object}
            - $ref : #/definitions/Period
          - issuingSupplier {object}
            - $ref : #/definitions/OrganizationReference


## Defining texts:


**Cod** | **Title** | **Description**
--|--|--
hasQuotes | Has quotes? | A true/false field to indicate whether any quotes were received during the planning process.
requestsForQuotes | Requests for quotes | A list of requests for quotes related to the planning process.
requestForQuotes | Request for quotes | A request for quotes (RFQ) is a type of procurement solicitation in which a buyer asks invited suppliers to offer an estimated price for particular goods or services.
id | Request ID | A local identifier for this request, unique within this block.
title | Title | The request for quotes title.
description | Description | The text sent to the invited suppliers in order to participate in the quotation process.
period | Period to receive quotes | The period between the date when the request for quotes was made and the end date to receive the quotes.
invitedSuppliers | Invited suppliers | A list of invited suppliers asked to send quotes.
items | Items to be quoted | The goods and services to be quoted, broken into line items wherever possible. Items should not be duplicated, but a quantity of 2 specified instead.
quotes | Quotes | A list of quotes received from invited suppliers.
quotes | Quote | A quote is a fixed price offered by a invited supplier for particular goods or services.
id | Quote ID | A local identifier for this quote, unique within this block.
description | Description | Quote description. Terms and conditions for the quote.
date | Quote date | The date of the quote. This is the date when the quote was received.
items | Items quoted | The goods and services quoted, broken into line items wherever possible. Items should not be duplicated, but a quantity of 2 specified instead.
value | Quote value | The total value of this quote.
quotePeriod | Quote period | The period on which this quote is valid.
issuingSupplier | Issuing supplier | The supplier that sent a quote.

## Issues 

Report issues for this extension in the [standard repository](https://github.com/open-contracting/standard/issues/599) of the Open Contracting Partnership.
