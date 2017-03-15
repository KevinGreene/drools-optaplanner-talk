Reservations?


Rules aren't great for business stakeholders

(not as much as marketing teams suggest)


Rules still require thought and discipline up front

(sometimes even more so)


Rules can sometimes be hard to evaluate at first

```drools
rule "Apply more than 3 years seniority discount"
when
    $c: Customer(seniority > 3)
then
    modify($c){
        setDiscount($c.getDiscount()+0.1),
        addDiscountReason("Seniority greater than 3 years")
    }
end```

Can you spot the error?


IDE support isn't fantastic

(highlight.js was modified by a colleague for this talk)

(Eclipse is actually pretty great)