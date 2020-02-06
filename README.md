# QR-Bill

Supporting material for the introduction of the [QR bill](https://www.swiss-qr-invoice.org) in Switzerland.

## Sample invoices

| ERP               |   Version    | Sample file                                                                                                                           | Format | Date added |
| ----------------- | :----------: | :------------------------------------------------------------------------------------------------------------------------------------ | :----: | ---------- |
| Messerli          |      ?       | [sample-0001-messerli-informatik.pdf](invoices/sample-0001-messerli-informatik.pdf)                                                   |  PDF   | 2019-11-05 |
| _synthetic_       |              | [sample-0002-swico-synthetic.png](invoices/sample-0002-swico-synthetic.png)                                                           |  PNG   | 2019-11-07 |
| Run my Accounts   |    2.8.52    | [sample-0003-run-my-accounts.pdf](invoices/sample-0003-run-my-accounts.pdf)                                                           |  PDF   | 2019-12-05 |
| Crésus            | 13.0-preview | [sample-0004-cresus.pdf](invoices/sample-0004-cresus.pdf)                                                                             |  PDF   | 2019-12-12 |
| Crésus            | 13.0-preview | [sample-0005-cresus.pdf](invoices/sample-0005-cresus.pdf)<br/>contains multiple VAT rates                                             |  PDF   | 2019-12-12 |
| BCGE _sample_     |     n/a      | [sample-0006-bcge-vierge.jpg](invoices/sample-0006-bcge-vierge.jpg)<br/>QR-bill, QRR, no amount, no payer                             |  JPEG  | 2020-01-08 |
| BCGE _sample_     |     n/a      | [sample-0007-bcge-complete.jpg](invoices/sample-0007-bcge-complete.jpg)<br/>QR-bill, plain IBAN, with payer                           |  JPEG  | 2020-01-08 |
| Sage 200          |     n/a      | [sample-0008-sage200.pdf](invoices/sample-0008-sage200.pdf)<br/>multiple payment conditions including<br/>5% discount and 2% discount |  PDF   | 2020-01-14 |
| Abacus Immobilien |     n/a      | [sample-0009-abacus-immobilien.pdf](invoices/sample-0009-abacus-immobilien.pdf)<br/>contains multiple invoices                        |  PDF   | 2020-02-01 |
| Proffix           |     n/a      | [sample-0010-proffix.pdf](invoices/sample-0010-proffix.pdf)                                                                           |  PDF   | 2020-02-06 |

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
- `CH78 3000 0000 1001 5000 6` &rarr; PostFinance, fictitious (invalid) account number.
- `CH05 3000 5230 5042 2318 T` &rarr; UBS, fictitious account number with invalid checksum.  
  Source: [clearit 79](https://www.six-group.com/interbank-clearing/dam/downloads/de/clearit/79/edition.pdf).
- `CH06 3000 5230 5042 2318 T` &rarr; UBS, fictitious account number (same as above, with correct checksum).
- `CH51 3000 0001 2500 9034 2` &rarr; PostFinance, fictious virtual account number 1 for 25-009034-2.  
  Source: [Neues von PostFinance Nr. 2 November 2019](https://www.postfinance.ch/content/dam/pfch/doc/cust/software/magbiz_shh_1911_de.pdf).
- `CH30 3000 0001 2500 9072 0` &rarr; PostFinance, fictious virtual account number 1 for 25-9072-0.  
  `CH82 3000 0002 2500 9072 0` &rarr; PostFinance, fictious virtual account number 2 for 25-9072-0.  
  Source: [Virtual accounts as replacement for ISR subscriber numbers](https://www.postfinance.ch/content/dam/pfch/doc/cust/download/Factsheet_04_en.pdf)
- `CH80 0078 8000 0506 6413 3` &rarr; BCGE, sample 1, fictious IBAN for Jean-Jacques Genevois.
- `CH05 3078 8000 0506 6413 3` &rarr; BCGE, sample 1, matching QR-IBAN for Jean-Jacques Genevois.
- `CH53 0078 8000 0506 6413 4` &rarr; BCGE, sample 2, fictious IBAN for Jean-Jacques Genevois.
- `CH75 3078 8000 0506 6413 4` &rarr; BCGE, sample 2, QR-IBAN for Jean-Jacques Genevois.
- `CH58 0078 8000 Z321 8002 5` &rarr; BCGE, sample 3, fictious IBAN for Jean-Jacques Genevois.
- `CH84 3078 8000 Z321 8002 5` &rarr; BCGE, sample 3, QR-IBAN for Jean-Jacques Genevois.
- `CH79 0078 8000 C330 1425 5` &rarr; BCGE, sample 4, fictious IBAN for Jean-Jacques Genevois.
- `CH08 3078 8000 C330 1425 5` &rarr; BCGE, sample 4, QR-IBAN for Jean-Jacques Genevois.
- `CH50 3100 0012 3456 7800 9` &rarr; CS, fictious QR-IBAN for `CH56 0483 5012 3456 7800 9`.

### How are QR-IBANs built?

#### BCGE (QR-IID 30788)

- Format `CHxx 30788000 aaaa aaaa a`.
- One-to-one correspondance between QR-IBAN and IBAN.
- `aaaa aaaa a` matches customer IBAN `CHxx 0078 8000 aaaa aaaa a`.

#### PostFinance (QR-IID 30000)

See [04 Virtual accounts (PDF)](https://www.postfinance.ch/content/dam/pfch/doc/cust/download/Factsheet_04_en.pdf)
found on PostFinance's dedicated [QR bill information site](https://www.postfinance.ch/en/business/products/accounts-receivable-solutions/qr-bills.html).

PostFinance provides [its own test platform](https://testplattform.postfinance.ch/).

- Format `CHxx 3000 0nnn aaaa aaaa a`
- Up to 999 QR-IBAN for a given account.
- `nnn` collection prefix, can be chosen by customer (`001`, `002`, etc.).
- `aaaa aaaa a` has to match customer account number `aa-aaaaaa-a`.

#### Credit Suisse (QR-IID 31000)

- Format `CHxx 3100 00aa aaaa aaaa a`.
- One-to-one correspondance between QR-IBAN and IBAN.

### QR-IIDs

- German: [Test-Bankenstamm mit QR-IIDs](https://www.paymentstandards.ch/de/shared/communication-grid/bankenstamm.html).
- French: [Fichier des banques de test avec QR-IID](https://www.paymentstandards.ch/fr/shared/communication-grid/bankenstamm.html).

### QR-Reference (QRR)

Spaces in the _QR reference_ must be removed when stored in the QR-code payload.

- `21 0000 0003 13947 14300 09017` &rarr; taken from [clearit 79](https://www.six-group.com/interbank-clearing/dam/downloads/de/clearit/79/edition.pdf)

### Structured Creditor Reference (SCOR)

Spaces in the _structured creditor reference_ must be removed when stored in the QR-code payload.

- `RF48 5000 0567 8901 2345` &rarr; taken from [clearit 79](https://www.six-group.com/interbank-clearing/dam/downloads/de/clearit/79/edition.pdf)
