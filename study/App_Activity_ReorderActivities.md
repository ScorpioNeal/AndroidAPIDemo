###App/Activity/ReorderActivities###
####Activity重新排序####

	* intent.addFlags(Intent.FLAG_ACTIVITY_REORDER_TO_FRONT);
	 
	If set in an Intent passed to Context.startActivity(), this flag will cause the launched activity to be brought to the front of its task's history stack if it is already running. 

	For example, consider a task consisting of four activities: A, B, C, D. If D calls startActivity() with an Intent that resolves to the component of activity B, then B will be brought to the front of the history stack, with this resulting order: A, C, D, B. This flag will be ignored if FLAG_ACTIVITY_CLEAR_TOP is also specified. 

	即如果添加了FLAG_ACTIVITY_CLEAR_TOP 
    那么就是A,B,C,D -> A, B
    不添加的时候是A,B,C,D -> A, C, D, B  ?? Is that correct?
