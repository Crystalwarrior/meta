This is an attempt to cover as many hidden features and quirks of the TorqueScript language as possible, to assist reviewers in identifying suspicious code.

###### TorqueScript returns the last value

Even with a `return;` being the last statement in a scope, *script-defined functions always return the last value* without an explicit return statement containing a value.

    function test()
    {
        getDateTime();
        
        // The presence of this line does not affect the output.
        // return;
    }
    
    ==> echo(test());
    02/11/14 19:58:50

Watch out for unexpected return values (either intentionally or unintentionally).

###### Logic acts unpredictably with constants

`!0.7` is not the same as `$a=0.7;` followed by `!$a`. The negation operator only takes the integer part of a value into account if the value is a constant rather than a variable (or, seems to actually round it in the opposite case - not quite sure).

    ==> $a = 0.7;
    ==> echo(!$a);
    1               // 0.7 is interpreted as 0
    ==> echo(!!$a);
    0
    
    ==> echo(!0.7);
    0               // 0.7 is interpreted as 1
    ==> echo(!!0.7);
    0

###### Object ID references ignore non-numeric characters

When referring to an object, such as by a method call, any characters in the ID which are not one of 0123456789 will be entirely ignored (unless it's the first character).

    // Assume that MainMenuGui has an ID of 4552
    ==> "4552 is not my favorite number".delete();
    ==> echo(isObject(MainMenuGui));
    0 // no longer exists
