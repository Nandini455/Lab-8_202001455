# Lab-8_202001455

**Name: Nandini Manish Parekh**  
**ID: 202001455**
<br>

# Lab 8: Unit Testing with jUnit
<br><br>

**1. Create a new Eclipse project, and within the project create a package.**
<br>      Created a project in Ecliplse and named the package as **JUnit**.
<br><br><br>
**2. Create a class for a Boa.**
<br>      package JUnit;
 <br>public class Boa {
<br>  private String name;
<br>private int length; // the length of the boa, in feet
<br>private String favoriteFood;
<br>public Boa (String name, int length, String favoriteFood){
<br>this.name = name;
<br>this.length = length;
<br>this.favoriteFood = favoriteFood;
<br>}
<br>// returns true if this boa constrictor is healthy
<br>public boolean isHealthy(){
<br>return this.favoriteFood.equals(&quot;granola bars&quot;);
<br>}
<br>// returns true if the length of this boa constrictor is
<br>// less than the given cage length
<br>public boolean fitsInCage(int cageLength){
<br>return this.length &lt; cageLength;
<br>}
<br>}
<br>
![image](https://user-images.githubusercontent.com/83688003/233329147-b1002e94-769c-4a44-aa68-451f03d2eb51.png)

<br><br>
**3. Follow the instructions in the JUnit tutorial in the section “Creating a JUnit
Test Case in Eclipse”. You’ll be creating a test case for the class Boa. When
you’re asked to select test method stubs, select both isHealthy() and
fitsInCage(int).**
<br>**Code:**
<br>@Testpublic void test() {
<br>Boa boa = new Boa(&quot;Benny&quot;,5,&quot;granola bars&quot;);
<br>assertTrue(boa.isHealthy());
<br>}
<br>@Test
<br>public void testIsHealthyWithFavoriteFoodNotGranolaBars() {
<br>Boa boa = new Boa(&quot;Benny&quot;, 5, &quot;mice&quot;);
<br>assertFalse(boa.isHealthy());
<br>}
<br>@Test
<br>public void testFitsInCageWhenLengthLessThanCageLength() {
<br>Boa boa = new Boa(&quot;Benny&quot;, 5, &quot;granola bars&quot;);
<br>assertTrue(boa.fitsInCage(10));
<br>}
<br>@Test
<br>public void testFitsInCageWhenLengthGreaterThanCageLength() {
<br>Boa boa = new Boa(&quot;Benny&quot;, 20, &quot;granola bars&quot;);
<br>assertFalse(boa.fitsInCage(10));
<br>}
<br>
<br><br>
**4. Now it’s time to write some unit tests. Notice that the BoaTest class that
JUnit created for you contains stubs for several methods. The first stub (for
the method setUp()) is annotated with @Before. The @Before annotation
denotes that the method setUp() will be run prior to the execution of each test
method. setUp() is typically used to initialize data needed by each test.
Modify the setUp() method so that it creates a couple of Boa objects, as
follows:**
**<br>
<br>@Before
<br>public void setUp() throws Exception {
<br>jen = new Boa("Jennifer", 2, "grapes");
<br>ken = new Boa ("Kenneth", 3, "granola bars");
<br>}
<br>**

**Code:**
<br>private Boa jen;
<br>private Boa ken;
<br>@Before
<br>public void setUp() throws Exception {
<br>jen = new Boa(&quot;Jennifer&quot;, 2, &quot;grapes&quot;);
<br>ken = new Boa (&quot;Kenneth&quot;, 3, &quot;granola bars&quot;);
<br>}
<br>
<br><br>
**5. JUnit also provided stubs for two test methods, each annotated with @Test.
Work on the testIsHealthy() method first. The purpose of this method is to
check that the isHealthy() method in the Boa class behaves the way it’s
supposed to. In the JUnit tutorial, read the section on “Writing Tests”. Modify
the testIsHealthy() method so that it checks the results of activating the
isHealthy() method on the two Boa objects you created in setup(). <br>
Likewise, modify the testFitsInCage() method to test the results of that
method. Make sure your test is robust; it should check the results when the
cage length is less than the length of the boa, when the cage length is equal to
the length of the boa, and when the cage length is greater than the length of
the boa. Should you write tests for both jen and ken?<br>**
<br>
**Code:<br>**
@Test<br>
public void testIsHealthy() {<br>
Boa jen = new Boa(&quot;Jen&quot;, 5, &quot;granola bars&quot;);<br>
Boa ken = new Boa(&quot;Ken&quot;, 6, &quot;mice&quot;);<br>
assertTrue(jen.isHealthy());<br>
assertFalse(ken.isHealthy());<br>
}<br>
@Test<br>
public void testFitsInCage() {<br>
Boa jen = new Boa(&quot;Jen&quot;, 5, &quot;granola bars&quot;);<br>
Boa ken = new Boa(&quot;Ken&quot;, 6, &quot;mice&quot;);<br>
assertTrue(jen.fitsInCage(6));<br>
assertTrue(jen.fitsInCage(5));<br>
assertFalse(jen.fitsInCage(4));<br>
assertTrue(ken.fitsInCage(7));<br>
assertTrue(ken.fitsInCage(6));<br>
assertFalse(ken.fitsInCage(5));<br>
}<br>
<br>
<br>
**6. Now you can run your tests. Read the section “Running Your Test Case” in
the tutorial. Did you get a green bar in the JUnit pane? If you got a red bar,
use the output in the JUnit pane to determine which test(s) failed. Fix your
tests, and try running the test case again. <br>
It’s important to note that a red bar doesn’t necessarily mean that the test case
is written incorrectly; it could be that the method that’s being tested isn’t
correct. In fact, that’s what unit testing is supposed to do – help us find errors
in our code. When a test fails, you need to determine if the error is in the test
case itself or in the code it’s testing. <br>**
Yes I got the green bar in the JUnit pane.
<br>
<br><br>
**7. Add a new method to the Boa class, with this purpose and signature: <br>
// produces the length of the Boa in inches<br>
public int lengthInInches(){<br>
// you need to write the body of this method<br>
}<br>
Add a new test case to the BoaTest class that tests the lengthInInches()
method. Make sure you annotate the new test method with @Test. Run your
tests.<br>**
<br>
**Added Function: <br>**
public int lengthInInches(){<br>
return this.length*12;<br>
// you need to write the body of this method<br>
}<br>
<br>
**Test Case for this function:<br>**
@Test<br>
public void testLengthInInches() {<br>
Boa boa = new Boa(&quot;John&quot;, 5, &quot;grapes&quot;);<br>
int expectedLengthInInches = 60;<br>
int actualLengthInInches = boa.lengthInInches();<br>
assertEquals(expectedLengthInInches, actualLengthInInches);<br>
}<br>
<br>
