Anatomy of a Rule


```drools
rule "Human Readable Description"
when
  LHS
then
  RHS
end
```

(If you would like this in tests, try Spock!)


Back to the Pet Shop


```drools
rule "warn if purchasing freshwater and saltwater fish"
    when:
        $saltwaterFish: Fish(fishType == FishType.SALTWATER)
        $freshWaterFish: Fish(fishType == FishType.FRESHWATER)
        $order: Order(notes not contains OrderNote.INCOMPATIBLE_FISH)
        exists OrderItem(order == $order, product == $saltwaterFish)
        exists OrderItem(order == $order, product == $freshWaterFish)
    then:
        modify($order){
            addNote(OrderNote.INCOMPATIBLE_FISH);
        }
end
```


```drools
rule "buy ten fish get a tank half off"
  when:
    $order: Order()
    $reason: eval(drools.getRule().getName())
    not OrderDiscount(order == $order,
                      reason == $reason)
    Number(intValue >= 10) from accumulate(
        $item: OrderItem(order == $order, 
                         product.type == ProductType.FISH)
        sum($item.getQuantity()))

    $tankITem: OrderItem(order == $order,
                         product.type == ProductType.FISH_TANK)
    then:
        OrderDiscount discount = new OrderDiscount($order, $tankItem, 0.5, $reason);
        insert(discount);
end
```


```drools
rule "warn if purchasing clownfish"
    when:
        $fishBreed: FishBreed(name == "Clownfish")
        $nemo: Fish(fishBreed == $fishBreed)
        $order: Order(notes not contains OrderNote.HAS_NEMO)
        exists OrderItem(order == $order, product == $nemo)
    then:
        modify($order){
            addNote(OrderNote.HAS_NEMO);
        }
end
```


```drools
rule "warn if purchasing blue tang"
    when:
        $fishBreed: FishBreed(name == "Blue Tang")
        $dory: Fish(fishBreed == $fishBreed)
        $order: Order(notes not contains OrderNote.HAS_DORY)
        exists OrderItem(order == $order, product == $dory)
    then:
        modify($order){
            addNote(OrderNote.HAS_DORY);
        }
end
```


Now that we've seen them...

"I could implement a simpler solution"


But when the shop needs to add coupons that expire...

```drools
rule "buy ten fish get a tank half off"
  date-expires   "20.03.2017 16:00"
  when:
...
  then:
...
end
```


When the shop decides that the incompatible fish example needs to fire before everything else...

```drools
rule "warn if nemo"
  salience -10
  when:
...
  then:
...
end
```


When you have 30 different types of discounts with complex requirements...

(left as excercise)


Lots of other features like:

* Declaring types in drools
* Extending types with traits
* Cron-like timers