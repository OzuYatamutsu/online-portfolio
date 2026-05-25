+++
date = '2023-03-22T15:01:02+02:00'
draft = false
title = 'Accounting automation'
description = "Scripts to automate small business accounting tasks"
+++
## Background

In 2022, I started to take on some software consultancy work as an independent contractor. As the work became more regular, I decided to formally start a small business to represent myself.

In the United States, a small business structured as a subchapter S corporation carries some tax benefits and simplification in some areas, but complication in others. Accurate accounting records, including taxes associated with the company and taxes associated with payroll, must be kept. Taxes must be deposited and filed on set schedules, or a penalty is risked for being out of compliance.

I had a few recurring issues to solve:

- How do I keep accurate accounting records?
- How can I issue and track invoices, paystubs, and requests for reimbursement?
- How do I make sure taxes are withheld accurately, paid, and filed on time?

Prior to starting the company, I spent a few months brushing up on small business accounting before getting to work structuring my accounting system. Eventually, I settled on:

- [GnuCash](https://www.gnucash.org/index.phtml?lang=en_US) to manage the accounts
- [LaTeX](https://www.latex-project.org/) to compile documents such as invoices and paystubs
- Microsoft Excel to track summaries per employee (e.g., YTD earnings, taxes paid, etc.)

![](/images/projects_accounting_01.png)

These all had the benefit of being free, being around for a long time, and having multiple options to access and manipulate data via scripting languages. Once the company was up and running for a few months, I decided to start automating some of the processes that took me the most time. I used the Python programming language due to easily available libraries to interface with all three technologies I used to manage my business.

## The flow of payment

![](/images/projects_accounting_02.png)

In my business, contracted work is done for customers at a fixed rate. At set periods of time, an invoice is issued to bill for the hours worked for the customer. Once the bill is paid, the employee that worked for the customer is entitled to the money that was earned, minus an amount withheld for company expenses. The money that is paid out to the employee is subject to a pre-tax deduction associated with the company retirement plan as well as standard payroll taxes and withholding. Finally, taxes are paid at the end of each month and filed quarterly. 

## Automating invoice document creation

Automating creation of the invoice was the easiest place to start. I wrote the invoice template in the LaTeX language, so all that needed to be done was to wrap a script around it to ask for the numbers to insert into the document, and the invoice is generated in a second or so. 

![](/images/projects_accounting_03.png)

![](/images/projects_accounting_04.png)

## Automating paystub document creation

It was a similar story to create the paystub document, just with different questions and calculations. Because the rates for paystub deductions are constant, they can be calculated on the fly with correct numbers being inserted into the document issued to employees.

![](/images/projects_accounting_05.png)
![](/images/projects_accounting_06.png)

## Automating journal entries

Because GnuCash is open-source and has been around for a long time, there are several libraries to interface with the data outside of the application (such as piecash). Since the existing scripts to generate invoices and paystubs both correspond with making entries in the accounting journal, I added this functionality to both scripts so that the correct entries can be made at the same time the document is created. This saves a huge amount of time making the entries manually, as every entry on the document corresponds to two entries in the journal (due to using double-entry bookkeeping). 

![](/images/projects_accounting_07.png)
![](/images/projects_accounting_08.png)

## Further work

As of April 2023, these were the greatest wins in terms of time saved managing the company's finances. Since the accounting books are accessible via Python API, other work which can be automated in future include:

- Compiling the balance sheet, profit and loss statement, and statement of cash flows to distribute to employees at the end of each quarter
- Automatically emailing invoices/paystubs to customers/employees as they are created
- Automatically filling out quarterly tax forms based on the numbers and employee data in the accounting records
