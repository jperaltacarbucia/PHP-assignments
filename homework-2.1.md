# Homework 2.1 - Ever wonder what all these signs say?

For Homework 1.1, you found a nice project on Github, forked it into your own account, and cloned it into your Cloud 9 IDE account. For this assignment, pick one or more PHP files from your project (you DID pick a PHP project, didn't you?) and identify some of the following items of PHP grammar and vocabulary that we talked about in class, including but not limited to:

<<<<<<< HEAD
* Variables: `$name`
* Constants: `E_USER_WARNING`, `MY_AWESOME_CONSTANT`
* Arithmetic operators: addition (+), subtraction (-)
* Functions: `array_slice()`, `do_something_amazing()`

When you find one, identify the file and line number in this file, below the instrcutions per the example below. Try to make the indentation match the original file (yes, copy and paste), even if that means there's NO indentation. Crazy PHPers.

You don't have to identify EVERYTHING in a given line or even in a single file, but you may get extra points if you're thorough or make a survey of more than one file... And you might get docked if you make too much work for me. I at least want to see about 50 lines of code.

When you're done editing this file, save it, commit it, and push it to your "assignments" repo, called "origin". You remember how to push, right?

## Your work should look like this...

`path/to/file.php:3`
=======
* Variables: $name
* Constants: E_USER_WARNING, MY_AWESOME_CONSTANT
* Arithmetic operators: addition (+), subtraction (-)
* Functions: array_slice(), do_something_amazing()

When you find one, identify the file and line number in this file, below the instrcutions per the example below. Try to make the indentation match the original file (yes, copy and paste), even if that means there's NO indentation. Crazy PHPers.

You don't have to identify EVERYTHING in a given line or even in a single file, but you may get extra points if you're thorough or make a survey of more than one file... And you might get docked if you make too much work for me. ;)

When you're done editing this file, save it, commit it, and push it to your forked version of the "assignments" repo. Then open a pull request back to the original. YOU WILL NOT GET CREDIT IF YOU DO NOT OPEN A PULL REQUEST!

my_github_user/my_repository/path/to/file.php:3
>>>>>>> upstream/master
```php
    if ( MY_AWESOME_CONSTANT )
    // Constant: MY_AWESOME_CONSTANT
```

<<<<<<< HEAD
`path/to/file.php:42`
=======
my_github_user/my_repository/path/to/file.php:42
>>>>>>> upstream/master
```php
    $name = do_something_amazing() + 1;
    // Variable: $name
    // Function: do_something_amazing()
<<<<<<< HEAD
    // Literal: 1 (integer)
```

## Now get to it!


//Copied Code--->

<?

    //make sure we have a version of the latest zip file on disk
    $basefilename = "jsGameSoup-v$revno.zip";
    $filename = "cache/" . $basefilename;
    if (!file_exists($filename)) {
        if (!is_dir("cache")) {
            mkdir("cache");
        }
        $ziplog = `zip = -r '$filename' . --exclude .git`;
    }
?>

// End.



// The dashed lines "//"  means comments for the programmer to see.

// "$basefilename" is a variable; we can tell by the dollar sign

// "mkdir("cache")" is a function; we can tell by the name and then the "()"

// "if (!file_exists($filename))" is a function with an if statement

// "cache/" . $basefilename;" is a literal; we can tell by what is inside the variable
=======
```

al_the_x/some_awesome_project/path/to/some/file.php:42
```php
 if ( PHP == 'awesome' ) {
 // Constant: PHP
 // Comparison: ==
 // String: 'awesome'
```
>>>>>>> upstream/master
