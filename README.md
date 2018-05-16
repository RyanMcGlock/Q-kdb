### q-kdb - Exercises
###### Q1) Sorting Elements of an Array by Frequency
###### Count each distinct element in the array and sorted by the highest count
	q)l:12 9 12 4 12 4 9 7 9 12
	q)dictFreq:desc (distinct l)!(count each {where l=x}each distinct l)
	q)raze {x#y}'[value dictFreq;key dictFreq]
	12 12 12 12 9 9 9 4 4 7

###### Q2) Sum EVEN Fibonacci numbers in sequence - 1 1 2 3 5 8 13 21 34 55 89 144 = 2+8+34+144=188
	q)fib:10{x,sum -2#x}/1 1
	q)sum fib[where not fib mod 2]
	188
	
###### Q3) Increasing Sequence Exercise
###### Taking some random list, find an increasing sequence from your first element in your list
###### list of (10 22 9 33 21 50 41 60 80) should equal (10 22 33 50 60 80)
	q)list:10 22 9 33 21 50 41 60 80 
	q)increaseSeq:{
			$[list[x+1]>($[x=0;list[x];max(list[til x+1])]);list[x+1];`]
				}each til count(list)-1 
	q)increaseSeq:list[0],((distinct asc increaseSeq)_((count distinct asc increaseSeq)-1)) 
	q)increaseSeq 
	10 22 33 50 60 80

###### Q4) Arrange Disks 
###### A row of 2n disks of two colours, n dark(1) and n light(0), sequence will be even and start with a dark colour, only allowed one move at a time!
	q)list:1 0 1 1 0 0

	arrangeDisks:{if[not `newList in key`.;newList:list];
		if[not list[0]=/(newList[til `long$((count newList)%2)]);
		
			    if[not `counter in key`.;counter:1];

			    if[newList[x]<>newList[0];
				          newList[x]:list[(where list=list[0])[counter]];
				          newList[(where list=list[0])[counter]]:0;
				          counter+:1
			      ]
		      ]
	      }

	q)arrangeDisks each til `long$((count(list))%2)
	1 1 1 0 0 0

