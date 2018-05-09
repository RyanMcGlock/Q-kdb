### q-kdb - Exercises
###### Q1) Increasing Sequence Exercise
###### Taking some random list, find an increasing sequence from your first element in your list
###### list of (10 22 9 33 21 50 41 60 80) should equal (10 22 33 50 60 80)
	q)list:10 22 9 33 21 50 41 60 80 
	q)increaseSeq:{
			$[list[x+1]>($[x=0;list[x];max(list[til x+1])]);list[x+1];`]
				}each til count(list)-1 
	q)increaseSeq:list[0],((distinct asc increaseSeq)_((count distinct asc increaseSeq)-1)) 
	q)increaseSeq 
	10 22 33 50 60 80

###### Q2) Arrange Disks 
###### A row of 2n disks of two colours, n dark(1) and n light(0), sequence will be even and start with a dark colour
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

