How do machines solve this problem?


Pretty much the same way humans do

Come up with a solution, then tweak it until it's good.


How does a machine know what's good?


Rules!

(much more reliable than gut instinct)


## Data Design


## Solution

The universe as you know it

Houses all data


## Planning Entity

The thing that will change

Often contains several children


## Planning Variable

The aspects of the planning entity that will change


## Planning Facts

Things that will never change while planning


![Examples](images/planning_examples.png)


## Moves

How does data change?

Can often be ignored for standard problems

// Atomic changes to the existing solution
// Maybe reference Chess or N-Queens, as they are straightforward?


## Rules

```drools
rule "Students be scheduled for a session"
    when
        $student: Student()
        not TutoringSession(student == $student)
    then
        scoreHolder.addHardConstraintMatch(kcontext, -100);
end
```


Soft Constraint Match Example


# Real Examples!