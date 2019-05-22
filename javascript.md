The find() method executes the function once for each element present in the array:

If it finds an array element where the function returns a true value, find() returns the value of that array element (and does not check the remaining values)
Otherwise it returns undefined
Note: find() does not execute the function for empty arrays.

Note: find() does not change the original array.
- .filter() -- The filter() method creates an array filled with all array elements that pass a test (provided as a function).

Note: filter() does not execute the function for array elements without values.

Note: filter() does not change the original array.
- checkedTodo.complete = !checkedTodo.complete -- Acts as a switch or a flag that changes back and forth from complete to Not Complete. Kind of like changing back and forth from true and false.
