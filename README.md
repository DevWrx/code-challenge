# DevWrx Coding Challenge

We're glad you're considering a position with DevWrx.  As part of our
process for matching great people with great work we've designed a
simple coding challenge that will help our technical interviewers get a
sense for your skills and experience.  Please follow the instructions
below to complete the challenge.

## The Process

1. Please fork this repository to your own Github account.  If you do
   not have a Github account you may submit your work in a zip file via
email (but a git repository is preferred).

2. Read the specification below and write code that satisfies the spec as
   closely as possible.  You may use any of the following languages to
develop your solution: Ruby, Python, JavaScript, Java, C#, or Obj-C.
For the purpose of this exercise, please avoid using any external
libraries (other than the language's standard library).  Also, do not
utilize any server or storage dependencies, i.e. no databases.

3. Once complete, please send the link to your forked repository back to
   the DevWrx talent representative that you have been working with.
You may also submit using a zip file if necessary.

4. A DevWrx technical interviewer will review your submission and may
   have questions about your solution during your phone screen.

## Specifications

You have been tasked with building a loan management module for use at
your company.  At a high level, the module should be able to do the following:

1. Take a loan application and make a determination whether or not an
   individual can be granted a loan.  If they are eligible, determine
the appropriate interest rate and credit limit for the loan.

2. Create a new loan based on the results of the application process.
   The loan should include details such as the amount of the loan, the
interest rate, and the maturity date.

3. Accept payments for the loan which include the payment amount and the
   date at which the payment should be applied.

4. Calculate the loan balance on any past, current, or future date.

5. Calculate the loan payoff amount at any past, current, or future
   date.

6. Pay-off a loan which prevents further payments from being applied.

You may use any object model to construct the internals of this system,
but the following public API should be exposed.

_The examples here are in JavaScript but the syntax of your solution
will vary based on the language you chose._

### Underwriting a Loan

```javascript
var loanApplication = new LoanApplication();
loanApplication.creditScore = 725;
loanApplication.amountRequested = 10000;

var underwriter = new Underwriter();
var loanOffer = underwriter.evaluate(loanApplication);
```

The `LoanOffer` object includes details on the interest rate and loan
amount allowed based on the underwriting process.  The following table
describes how underwriting determines the credit limit and interest rate
for loan offers.

<table>
  <thead>
    <tr>
      <th>Credit Score</th>
      <th>Interest Rate</th>
      <th>Max Loan Amount</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>&lt; 400</td>
      <td>N/A</td>
      <td>Rejected</td>
    </tr>
    <tr>
      <td>401 - 600</td>
      <td>5.75%</td>
      <td>$8,000</td>
    </tr>
    <tr>
      <td>601 - 700</td>
      <td>4.25%</td>
      <td>$12,000</td>
    </tr>
    <tr>
      <td>701 - 800</td>
      <td>3.8%</td>
      <td>$18,000</td>
    </tr>
    <tr>
      <td>&gt; 801</td>
      <td>2.14%</td>
      <td>$25,000</td>
    </tr>
  </tbody>
</table>

### Issue a New Loan

```javascript
var loan = new Loan();
loan.amount = 10000;
loan.interest_rate = 2.27;

// The maturity date is the date at which all payments should
// be complete and the loan paid off.  Loan interest compounds
// monthly so this date is used to determine the payment amount.
loan.maturity_date = new Date(2020,1,1);
```

### Apply a Payment

```javascript
loan.applyPayment({ amount: 300, date: new Date(2016, 1, 1) });
```

### Query the Loan for Details




## Additional Notes

* Please include any instructions for building or compiling your
  project.
* The code should be runnable from a REPL of some kind.  In Ruby or
  Python this can be the language REPL or in the case of a Java, .NET,
or Obj-C it could be the IDE's debugging environment.
* Unit tests are not absolutely necessary, but they do help in
  documenting your thought process.
* Please do not share your work with others or have anyone else assist
  you in writing your solution.
