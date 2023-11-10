The lease repayments are based on monthly fixed installments which increase every annum. I.e. the same amount is paid for 12 months, then a new amount is calculated based on a fixed escalation rate.



Monthly repayments calculated with a target IRR. This calculation is meant to approximate the targeted IRR as close as possible while being date agnostic.



i = \text{Annual rate increase}
\\
r = \text{Adjusted monthly IRR}
\\
N = \text{Number of terms (months)}
\\
principal=\text{Cost - Deposit}installment_0=\text{Initial monthly installment}
\\The IRR is converted to a monthly interested by using a compound conversion from annual interest rate to monthly interest rate

i = (IRR + 1)^{\frac{1}{12}} - 1
\\


installment_0 =  \frac{principal}{\sum_{a=0}^{\left\lfloor \frac{N}{12} \right\rfloor -1}
{\sum_{n=12a}^{12a + 11}
\frac{(1+i)^a}{(1+r)^n}
 }
}
\\
installment_0 = \frac{principal}{\frac{1 - (\frac{1}{1+r})^{12}}{1 - \frac{1}{1+r}} \cdot \frac{1 - (\frac{1+i}{(1+r)^{12}})^{\left\lfloor \frac{N}{12} \right\rfloor}}{1 - \frac{1+i}{(1+r)^{12}}}}
\\







*****

[[category.storage-team]] 
[[category.confluence]] 
