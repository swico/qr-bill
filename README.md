# QR-Bill

Supporting material for the introduction of the [QR bill](https://www.swiss-qr-invoice.org) in Switzerland.

## Sample invoices

| ERP         | Version | Sample file                                                                         | Format | Date added |
| ----------- |:-------:| :---------------------------------------------------------------------------------- | :----: | ---------- |
| Messerli    | ?       | [sample-0001-messerli-informatik.pdf](invoices/sample-0001-messerli-informatik.pdf) |  PDF   | 2019-11-05 |
| _synthetic_ |         | [sample-0002-swico-synthetic.png](invoices/sample-0002-swico-synthetic.png)         |  PNG   | 2019-11-07 |
| Run my Accounts | 2.8.52  | [sample-0003-run-my-accounts.pdf](invoices/sample-0003-run-my-accounts.pdf) | PDF | 2019-12-05 |
| Crésus | 13.0-preview | [sample-0004-cresus.pdf](invoices/sample-0004-cresus.pdf) | PDF | 2019-12-12 |
| Crésus | 13.0-preview | [sample-0005-cresus.pdf](invoices/sample-0005-cresus.pdf)<br/>contains multiple VAT rates | PDF | 2019-12-12 |

## QR-Bill Validator

Swico provides a [dedicated QR-code validator](https://www.swiss-qr-invoice.org/validator),
which can be used to validate not only the plain payload of the QR-code, but also the
syntax of the additional structured payment information (also known as **Swico-String**).

It accepts either plain text files which represent the payload of the QR-code, or image
files (PNG format) which contain the QR-code to analyse. You can also upload a PDF and
it will try to identify and extract the first valid QR-code.

[![Swico QR Validator](web/figure-qr-validator-1.png)](https://www.swiss-qr-invoice.org/validator)

## Sample values

### QR-IBAN

Spaces in the _QR-IBAN_ must be removed when stored in the QR-code payload.

- `CH44 3199 9123 0008 8901 2` &rarr; fictitious QR-IID.
- `CH78 3000 0000 1001 5000 6` &rarr; PostFinance QR-IID, fictitious account number.
- `CH05 3000 5230 5042 2318 T` &rarr; UBS, fictitious account number  with invalid checksum.  
  Source: [clearit 79](https://www.six-group.com/interbank-clearing/dam/downloads/de/clearit/79/edition.pdf).
- `CH06 3000 5230 5042 2318 T` &rarr; UBS, fictitious account number (same as above, with correct checksum).
- `CH51 3000 0001 2500 9034 2` &rarr; PostFinance, fictious account number 250090342.  
  Source: [Neues von PostFinance Nr. 2 November 2019](https://www.postfinance.ch/content/dam/pfch/doc/cust/software/magbiz_shh_1911_de.pdf).
- `CH80 0078 8000 0506 6413 3` &rarr; BCGE, sample 1, fictious IBAN for Jean-Jacques Genevois.
- `CH05 3078 8000 0506 6413 3` &rarr; BCGE, sample 1, matching QR-IBAN for Jean-Jacques Genevois.
- `CH53 0078 8000 0506 6413 4` &rarr; BCGE, sample 2, fictious IBAN for Jean-Jacques Genevois.
- `CH75 3078 8000 0506 6413 4` &rarr; BCGE, sample 2, QR-IBAN for Jean-Jacques Genevois.
- `CH58 0078 8000 Z321 8002 5` &rarr; BCGE, sample 3, fictious IBAN for Jean-Jacques Genevois.
- `CH84 3078 8000 Z321 8002 5` &rarr; BCGE, sample 3, QR-IBAN for Jean-Jacques Genevois.
- `CH79 0078 8000 C330 1425 5` &rarr; BCGE, sample 4, fictious IBAN for Jean-Jacques Genevois.
- `CH08 3078 8000 C330 1425 5` &rarr; BCGE, sample 4, QR-IBAN for Jean-Jacques Genevois.

### QR-IIDs

- German: [Test-Bankenstamm mit QR-IIDs](https://www.paymentstandards.ch/de/shared/communication-grid/bankenstamm.html).
- French: [Fichier des banques de test avec QR-IID](https://www.paymentstandards.ch/fr/shared/communication-grid/bankenstamm.html).

### QR-Reference (QRR)

Spaces in the _QR reference_ must be removed when stored in the QR-code payload.

- `21 0000 0003 13947 14300 09017` &rarr; taken from [clearit 79](https://www.six-group.com/interbank-clearing/dam/downloads/de/clearit/79/edition.pdf)

### Structured Creditor Reference (SCOR)

Spaces in the _structured creditor reference_ must be removed when stored in the QR-code payload.

- `RF48 5000 0567 8901 2345` &rarr; taken from [clearit 79](https://www.six-group.com/interbank-clearing/dam/downloads/de/clearit/79/edition.pdf)
