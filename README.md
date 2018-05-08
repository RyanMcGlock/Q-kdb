### q-kdb - Exercises
###### Q1) Increasing Sequence Exercise
###### Taking some random list, find an increasing sequence from your first element in your list
###### list of (10 22 9 33 21 50 41 60 80) should equal (10 22 33 50 60 80)

```python
q)list:10 22 9 33 21 50 41 60 80 <br />
q)increaseSeq:{$[list[x+1]>($[x=0;list[x];max(list[til x+1])]);list[x+1];`]}each til count(list)-1 <br />
q)increaseSeq:list[0],((distinct asc increaseSeq)_((count distinct asc increaseSeq)-1)) <br />
q)increaseSeq <br />
10 22 33 50 60 80
```
###### Q2)

