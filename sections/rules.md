First, what's life without rules


```java
for(Order order : orders) {
    int fishCount = 0
    boolean hasNemo = false;
    boolean hasFreshwaterFish = false;
    boolean hasSaltwaterFish = false;
    OrderItem fishTank = null;
    for(OrderItem item: order.items) {
        if(item.product instanceof Fish) {
            fishCount++;
            Fish fish = (Fish) item.product;
            if (!hasFreshwaterFish && fish.fishType = FishType.FRESHWATER){
                hasFreshwaterFish = true;
            }
            if (!hasSaltwaterFish && fish.fishType = FishType.SALTWATER){
                hasSaltwaterFish = true;
            }
            if (!hasNemo && fish.fishBreed = "Clownfish"){
                hasNemo = true;
            }
        }
        if(item.product.type == ProductType.FISH_TANK){
            fishTank = item;
        }
    }
    if (fishCount > 10 && fishTank != null) {
        order.addDiscount(new OrderDiscount(order, fishTank, 0.5D))
    }
    if(hasFreshwaterFish && hasSaltwaterFish) {
        order.addNote(OrderNotes.INCOMPATIBLE_FISH)
    }    
    if(hasNemo) {
        order.addNote(OrderNotes.HAS_NEMO)
    }
}
```


Hard to parse

Prone to error

Hides important details

Will grow in complexity over time


What would a perfect solution look like?


![A Perfect Drools Solution](images/drools_sans_drools.svg)


![A Perfect Drools Solution](images/drools_with_drools.svg)


Declarative, not imperative

Think SQL, Prolog


Rules are great for:

Complex problems

Hard to describe problems

Problems that get input from many sources