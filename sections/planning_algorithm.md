How do machines solve this problem?


Pretty much the same way humans do

Come up with a solution, then tweak it until it's good.


How does a machine know what's good?


Rules!

Much more reliable than gut instinct

But certain rules are more important than others when it comes to "goodness"


Scoring

Hard Score - Physically impossible or invalidating

Soft Score - Preferences

Bendable Score


## Data Design


## Solution

The universe as you know it

Houses all data

Commonly the Schedule


## Planning Entity

The thing that will change

Often contains several children (planning variables)

Often a specific slot that can be filled by multiple variables, e.g. Appointment


## Planning Facts

Things that will never change while planning

Often models physical attributes, e.g. Attendees, Rooms, TimeSlots, etc.


![Examples](images/planning_examples.png)


## Moves

Describe how atomic changes can be made

Can often be ignored for standard problems


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