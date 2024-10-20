# Simple modules I made

## YAWF and PITCHF
- This module adds three variables to the game: YAWF, PITCHF and CARDINALYAWF. They are coordinates of vision, with three decimal places of precision.
- Similarly to XPOSF, which adds three decimal places to XPOS, YAWF adds three decimal places to YAW. And so on for PITCHF and CARDINALYAWF.

## BetterPOP module
- Modifies the `pop` action, adding a third parameter to it:

`[outvar] = POP(<array[]>,[outvar],[index])`

- With it, the user can retrieve any input from the array, not only the last one. Also, `[index]` supports negative values, so `-1` would make it return the last item of the list.
- It gets the data from the given position of the array, and removes that element, shifting the array (it's different from `unset(&array[index])` which would keep an empty item in the list.
- Example of usage:
```php
split("-","a-b-c-d-e",&array[]); // creates an array with [a, b, c, d, e] ;
pop(&array[],&out,2); // retrieves the value from the index 2 of &array[], and shifts the array "to the left" in order to not keep that position empty;
log("output variable is: %&out%"); // will log "output variable is: c", since "c" is in the index number 2 ;

join("-",&array[],&input); // glues &array[] back together, so the user can read what changed from the "a-b-c-d-e" from the first action; 
log("the array was now composed of %&input%"); // will log "the array was now composed of a-b-d-e", since the index 2 was removed;

// alternative syntax, using the return method;
&out = pop(&array[],,2);
join("-",&array[],&input);
log("output variable is: %&out%"); // will log "output variable is: d";
log("the array was now composed of %&input%"); // will log "the array was now composed of a-b-e";
```
