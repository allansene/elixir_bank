Balances
========

A checking account from a bank allows for putting (deposits, salaries, credits)
or taking (purchases, withdrawals, debits) money at any given time.

You can also check what is your current balance or your account statement,
containing all operations that happened between two dates, along with the
account's daily balance.

While you should only be able to take an amount of money that was put there
previously, some banks give you a "free" credit line, so it can lend you some
money instantly, at a "reasonable" interest rate.

This exercise consists in implementing those basic features of a checking account:

- First step: adding the operations on that checking account

  Create a HTTP service in which you can add an operation to a given checking
  account, identified by the account number. This operation will contain the
  account number, a short description, a amount and the date it happened. Keep
  in mind you have to support both credit and debit operations, i.e, both
  putting and taking money out of the account.
  E.g:
    Deposit 1000.00 at 15/10
    Purchase on Amazon 3.34 at 16/10
    Purchase on Uber 45.23 at 16/10
    Withdrawal 180.00 at 17/10

  Deposits can take days to be acknowledged properly, so you should support
  insertion in any date order.

- Second step: Get the current balance

  Create a HTTP endpoint which returns the current balance of a given account.
  This balance is the sum of all operations until today, so the customer can
  know how much money they still have.

  E.g: for the sample above, the customer would have
  1000.00 - 3.34 - 45.23 - 180.00 = 771.43

- Third step: Get the bank statement

  Create a HTTP endpoint which returns the bank statement of a period of dates.
  This statement will contain the operations of each day and the balance at the
  end of each day.

  E.g:
  15/10:
  - Deposit 1000.00
  Balance: 1000.00

  16/10:
  - Purchase on Amazon 3.34
  - Purchase on Uber 45.23
  Balance: 951.43

  17/10:
  - Withdrawal 180.00
  Balance: 771.43

- Fourth step: Compute periods of debt.

  Create a HTTP endpoint which returns the periods which the account's balance
  was negative, i.e, periods when the bank can charge interest on that account.

  E.g: if we have two more operations (current balance is 771.43):
  Purchase of a flight ticket 800.00 at 18/10
  Deposit 100.00 at 25/10

  The endpoint would return:
  - Principal: 28.57
    Start: 18/10
    End: 24/10

  This endpoint should return multiple periods, if applicable, and omit the "End:"
  date if the account's balance is currently negative.

All HTTP endpoints should accept and return JSON payloads as requests and
responses. There is no need for HTML visualizations.

You should deliver a git repository, or a link to a shared private repository on
github, bitbucket or similar, with your code and a short README file outlining
the solution and explaining how to build and run the code. You should deliver
your code in a functional programming language — Clojure, Common Lisp, Scheme,
Haskell, ML, F# and Scala are acceptable — and we'll analyse the structure and
readability of the code-base. There is no problem  in using libraries, for instance for
testing or network interaction, but please avoid delegating any core business logic to external libraries or tools 
(like databases). 

We expect production-grade code. 

Don't shy away from asking questions whenever you encounter a problem.  Also,
please do get in touch at any moment if you believe the timeframe is
unrealistic.
