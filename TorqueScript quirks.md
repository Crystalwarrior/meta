This is an attempt to cover as many hidden features and quirks of the TorqueScript language as possible, to assist reviewers in identifying suspicious code.

#### TorqueScript returns the last value

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

#### Logic acts unpredictably with constants

`!0.7` is not the same as `$a=0.7;` followed by `!$a`. The negation operator only takes the integer part of a value into account if the value is a constant rather than a variable (or, seems to actually round it in the opposite case - not quite sure).

    ==> $a = 0.7;
    ==> echo(!$a);
    1 // 0.7 is interpreted as 0
    ==> echo(!!$a);
    0
    
    ==> echo(!0.7);
    0 // 0.7 is interpreted as 1
    ==> echo(!!0.7);
    1

#### Very allowing string -> number casting

TorqueScript's method for casting a string into a number can allow a lot of unexpected behavior to occur. An empty string or a string that begins with a non-numeric character is interpreted as the value 0. Other strings simply are stripped of all non-numeric characters.

    ==> echo("" + 2);
    2 // Empty string parsed as 0 (0 + 2)
    ==> echo("foo" + 6);
    6 // String starting with non-numeric parsed as 0 (0 + 6)
    ==> echo("32 foo" + 3);
    35 // Non-numeric character stripped resulting in 32 (32 + 3)

#### Surprising object reference lookup

When referencing an object, the value is casted to a number (see above). If the result is 0, it'll look up the name from the original value (can contain any non-null characters). Otherwise, it'll look it up by ID. This can be misleading since "32 foo" will lookup by the ID 32, and "foo 32" will lookup by the name "foo 32".

    ==> $b = new ScriptObject(MyObject.getID() @ "test");
    ==> echo($b.getName());
    3000test
    ==> echo("3000test".getName());
    MyObject
    
    // Assume that MainMenuGui has an ID of 4552
    ==> "4552 is not my favorite number".delete();
    ==> echo(isObject(MainMenuGui));
    0 // no longer exists
