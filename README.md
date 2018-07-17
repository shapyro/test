# JHA Silverlake - Cognos


### Contents
- [FI Action Items](#fiactionitems)
- [Difficulty](#difficulty)
- [Known Fees](#knownfees)
- [Interest Details](#interest)
- [Extracts](#extracts)
- [Posting Files](#postingfiles)
- [Product Setup](#productsetup)

## FI Action Items

* implement XML queries and automate extracts using Cognos
* ensure Menu Xpress Options are created and tested
* if using IFS, ensure IFS drive is shared to Kasasa and removed fromt he MIMIX process at JHA
	* a JHA user will be needed to copy files from the IFS to FIT.


## Difficulty

NA


## Known Fees
 
NA


## Interest

Kasasa performs an interest debit adjustment to accrual

## Extracts
	
Kasasa will provide XML files to be used in Cognos for the FI to implement locally at the institution. The Cognos report writer will generate reports (extracts) to a known location on the FI's network, possibly known as the IFS.  An additional transfer job may be required to move files from the IFS to the appropriate location for Kasasa.

| XML Filename | Extract Filename | Data |
| ------------ | ---------------- | ---- |
| AcctDDA.xml | bvkACCTDDA-en-us.csv | Deposit Accounts |
| AcctLoans.xml | bvkACCTLOANS-en-us.csv | Loan Accounts |
| AcctCDS.xml | bvkACCTCDS-en-us.csv | CDs |
| AtmSurcharges.xml | bvkATMSURCHARGES-en-us.csv | ATM Surcharges |
| CIF.xml | bvkCIFMBR-en-us.csv | Customer Records |
| Estmts.xml | bvkESTMTS-en-us.csv | Electronic Statements |
| LinkedAccounts.xml | bvkLinks-en-us.csv | Linked Accounts |
| Netteller.xml | bvkNETTELLER-en-us.csv | Internet Banking |
| ProductCodeDefsCDS.xml | NA | CD Product Code Definitions |
| ProductCodeDefsDDA.xml | NA | DDA Product Code Definitions |
| ProductCodeDefsLoans.xml | NA | Loan Product Code Definitions |
| RelInfo.xml | bvkRELINFO-en-us.csv | Deposit Accounts |
| TrancodeDefinitions.xml | NA | Transaction Code Definitions |
| TxnsDescriptions.xml | bvkTXNSDESCRIPTIONS-en-us.csv | Transaction Descriptions |
| TxnsHistory.xml | bvkTXNSDDA07-en-us.csv | 7 Days of Transaction History |

**Format:** TAB or PIPE Delimited with Headers


## Posting Files

**How are files posted:** Menu Option buttons must be created in Menu Xpress for the following two files:
- DDXTRNPC
	- Debits to Accrual for Interest
	- General Credits/Debits 
- GLTRNA
	- GL and Settlement postings

**GL/Settlement Accounts:** Kasasa Posting files will provide GL and Settlement data, so these accounts will be need to be provided in the posting file form.


## Product Setup

**Product Code:** Service Charge Code

**Interest Bearing Accounts:** Kasasa interest bearing accounts should be set to the high, tiered rate (APR) on core. Kasasa will be responsible for monitoring the account balance on a daily basis. Kasasa will then calculate the low interest rate and submit an interest debit adjustment on the last business day of the cycle period.  As always, it is very important to zero out interest when switching to/from an interest bearing account.  Additionally, it may be required to change statement codes/logic when converting non-Kasasa accounts.

**Linked Account Method:** Recommended Method - Kasasa Institution would need to use a new User Defined Field on the Checking Account. A SAV account number should be entered as an attribute of a DDA account. If the institution would choose to use a UDF, a CSR would be selecting the value from a list, and then manually enter the linked savings account number that was also being opened with the DDA. One of the Kasasa extract queries will be a Linked Account report. The user defined value could require potential core support for setup at the FI if they are unaware of UDF usage.

