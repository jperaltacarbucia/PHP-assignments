class MyTestCase extends TestCase
{
  public function SetUp()
  {
    // Code to perform set up for test case.
  }
  
  public function Run()
  {
    // Code to perform the test case.
    $this->AssertEquals('hello', 'there', 'Should fail!');
    $this->AssertEquals('howdy', 'howdy', 'Should pass!');
  }

  public function TearDown()
  {
    // Code to tidy up afterwards.
  }
}

PHPUnit - http://php-unit-test.batcave.net/  

------------------------------------------------------------------------------------------------------
The rule of thumb which is applicable across most languages (all that I vaguely know) is that an assert is used to assert that a condition is always true whereas an if is appropriate if it is conceivable that it will sometimes fail.

In this case, I would say that assert is appropriate (based on my weak understanding of the situation) because records should always be set before the given method is called. So a failure to set the record would be a bug in the program rather than a runtime condition. Here, the assert is helping to ensure (with adequate testing) that there is no possible program execution path that could cause the code that is being guarded with the assert to be called without records having been set.

The advantage of using assert as opposed to if is that assert can generally be turned off in production code thus reducing overhead. The sort of situations that are best handled with if could conceivably occur during runtime in production system and so nothing is lost by not being able to turn them off.

In favor - http://stackoverflow.com/questions/4516419/should-i-be-using-assert-in-my-php-code

-------------------------------------------------------------------------------------------------------

http://readwrite.com/2008/08/13/12_unit_testing_tips_for_software_engineers#awesm=~old4iKN6lS1eUC

http://www.thoughtworks.com/insights/articles/test-assertions

--------------------------------------------------------------------------------------------------------

Pros and Cons

http://stackoverflow.com/questions/771011/what-are-the-pros-and-cons-of-automated-unit-tests-vs-automated-integration-test

http://readwrite.com/2008/08/13/12_unit_testing_tips_for_software_engineers#awesm=~old4iKN6lS1eUC or http://engronline.ee.memphis.edu/eece3220/chap9/sld035.htm

---------------------------------------------------------------------------------------------------------

Unit testing is no guarantee for quality (con)
Unit testing can be really cumbersome to use and more time can be spent finding a test than solving the problem. Like for example: How do you test an app that reads from sys.stdin? (con)
Unit testing only helps with bugs you’ve anticipated or found

http://swizec.com/blog/the-ten-pros-and-cons-of-unit-testing/swizec/679

----------------------------------------------------------------------------------------------------------

Testing Frameworks

PHPUnit
http://phpunit.de/manual/current/en/index.html

SimpleTest
http://www.simpletest.org/

PHP Unit Testing
http://php-unit-test.sourceforge.net/