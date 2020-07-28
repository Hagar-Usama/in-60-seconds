# _Comments_ 

---

## Table of Contents

* [Introduction](#Introduction)
* [Good Comments](#Good-Comments)
* [Bad Comments](#Bad-Comments)
* [References](#References)

---
##  Introduction
 
If our programming languages were expressive enough, or if we had the talent to subtly wield those languages to express our intent, we would not need comments very much—perhaps not at all.

--- 

### Comments Do Not Make Up for Bad Code
 
Clear and expressive code with few comments is far superior to cluttered and complex code with lots of comments. Rather than spend your time writing the comments that explain the mess you’ve made, spend it cleaning that mess.

---

### Explain Yourself in Code
 
```java
// Check to see if the employee is eligible for full benefits
if ((employee.flags & HOURLY_FLAG) && (employee.age > 65))
```
 
vs
 
```java
if (employee.isEligibleForFullBenefits())
```
---

### Good Comments
 
Some comments are necessary or beneficial. However the only truly good comment is the comment you found a way not to write.

---

#### Legal Comments
 
Sometimes our corporate coding standards force us to write certain comments for legal reasons. For example, copyright and authorship statements are necessary and reasonable things to put into a comment at the start of each source file.

--- 

#### Informative Comments
 
It is sometimes useful to provide basic information with a comment. For example, consider this comment that explains the return value of an abstract method:
 
```java
// Returns an instance of the Responder being tested.
protected abstract Responder responderInstance();
```
 
A comment like this can sometimes be useful, but it is better to use the name of the function to convey the information where possible. For example, in this case the comment could be made redundant by renaming the function: `responderBeingTested`.

--- 
#### Explanation of Intent
 
Sometimes a comment goes beyond just useful information about the implementation and provides the intent behind a decision. Example:
 
```java
public int compareTo(Object o)
{
  if(o instanceof WikiPagePath)
  {
    WikiPagePath p = (WikiPagePath) o;
    String compressedName = StringUtil.join(names, "");
    String compressedArgumentName = StringUtil.join(p.names, "");
    return compressedName.compareTo(compressedArgumentName);
  }
  return 1; // we are greater because we are the right type.
}
```

---

#### Clarification
 
Sometimes it is just helpful to translate the meaning of some obscure argument or return value into something that's readable. In general it is better to find a way to make that argument or return value clear in its own right; but when its part of the standard library, or in code that you cannot alter, then a helpful clarifying comment can be useful.

---

## Bad Comments
--- 
### Mumbling
 His mumbling left behind an _enigma_
```java
public void loadProperties()
   {
     try
     {
      String propertiesPath = propertiesLocation +
       ”/” + PROPERTIES_FILE;
      FileInputStream propertiesStream = new
       FileInputStream(propertiesPath);
      loadedProperties.load(propertiesStream);
     }
     catch(IOException e)
     {
       // No properties files means all defaults are loaded
     }
   }

```
---

### Redundant Comments
> If comments are not inforamtive, add no value to your code, just remove them.

 The comment probably takes longer to read than the code itself.
```java
 // Utility method that returns when this.closed is true.  Throws an exception
 // if the timeout is reached.

 public synchronized void waitForClose(final long timeoutMillis)  throws Exception
 {     
      if(!closed)      {       
       wait(timeoutMillis);
      if(!closed)
      throw new Exception("MockResponseSender could not be closed");
      }

```
---
### Misleading Comments
> Code never lies, comments do sometimes

> Comments should desribe what your code **actually** do, but not what you **wish** your code to do.

---

### Mandated Comments
> Do not add a comment for each function or  variable. If they do not need commenting, leave them uncommented.
```java
/**
    * 
    * @param title The title of the CD
    * @param author The author of the CD
    * @param tracks The number of tracks on the CD
    * @param durationInMinutes The duration of the CD in minutes
    */
   public void addCD(String title, String author, 
                      int tracks, int durationInMinutes) {
     CD cd = new CD();
     cd.title = title;
     cd.author = author;
     cd.tracks = tracks;
     cd.duration = duration;
     cdList.add(cd);
   }

```
---

### Journal Commnets
>  Adding a log-like comment isn't a good idea.<br> ⚠ Hey, we have version control now!

```java

 * Changes (from 11-Oct-2001)
 * --------------------------
 * 11-Oct-2001 : Re-organised the class and moved it to new package 
 *               com.jrefinery.date (DG);
 * 05-Nov-2001 : Added a getDescription() method, and eliminated NotableDate 
 *               class (DG);
 * 12-Nov-2001 : IBD requires setDescription() method, now that NotableDate 
 *               class is gone (DG);  Changed getPreviousDayOfWeek(), 
 *               getFollowingDayOfWeek() and getNearestDayOfWeek() to correct 
 
 *               bugs (DG);
 * 05-Dec-2001 : Fixed bug in SpreadsheetDate class (DG);
 * 29-May-2002 : Moved the month constants into a separate interface 
 *               (MonthConstants) (DG);
 * 27-Aug-2002 : Fixed bug in addMonths() method, thanks to N???levka Petr (DG);
 * 03-Oct-2002 : Fixed errors reported by Checkstyle (DG);
 * 13-Mar-2003 : Implemented Serializable (DG);
 * 29-May-2003 : Fixed bug in addMonths method (DG);
 * 04-Sep-2003 : Implemented Comparable.  Updated the isInRange javadocs (DG);
 * 05-Jan-2005 : Fixed bug in addYears() method (1096282) (DG);
```

---

### Noise Comments
```javascript
// Avoid Monkey Patches from Application Insights
// Avoid Monkey Patches from Application Insights
bootstrap.avoidMonkeyPatchFromAppInsights();
// Enable portable support
bootstrap.configurePortable();
// Enable ASAR support
bootstrap.enableASARSupport();
// Load CLI through AMD loader
require('./bootstrap-amd').load('vs/code/node/cli');

```
---

### Scary Noise Comments

```java
   /** The name. */
   private String name;

   /** The version. */
   private String version;

   /** The licenceName. */
   private String licenceName;

   /** The version. */
   private String info;

```

---

### Don't use a comment when you can use a function or a variable

Consider the following stretch of code:
```java
// does the module from the global list <mod> depend on the
// subsystem we are part of?
if (smodule.getDependSubsystems().contains(subSysMod.getSubSystem()))
```
This could be rephrased without the comment as
```java
ArrayList moduleDependees = smodule.getDependSubsystems();
String ourSubSystem = subSysMod.getSubSystem();
if (moduleDependees.contains(ourSubSystem))
```
----

### Position Markers

   In general banners are clutter that should be eliminated.A banner is startling and obvious 
   if you don’t see banners very often. So use them very sparingly, and only when the benefit is significant. 
   If you overuse banners, they’ll fall into the background noise and be ignored.

---

### Closing Brace Comments

   If you find yourself wanting to mark your closing braces, try to shorten your functions instead.
   
```java

    public class wc {
public static void main(String[] args) {
BufferedReader in = new BufferedReader(new InputStreamReader(System.in));
String line;
int lineCount = 0;
int charCount = 0;
int wordCount = 0;
try{ while ((line = in.readLine()) != null) {
lineCount++;
charCount += line.length();
String words[] = line.split("\\W");
wordCount += words.length;
} //while
System.out.println("wordCount = " + wordCount);
System.out.println("lineCount = " + lineCount);
System.out.println("charCount = " + charCount);
} // try
catch (IOException e) {
System.err.println("Error:" + e.getMessage());
} //catch
} //main
}

```
---

### Attributions and Bylines
/* Added by Rick */
Source code control systems are very good at remembering who added what, when.
There is no need to pollute the code with little bylines.
Again, the source code control system is a better place for this kind of information.

----

### Commented out Code
  ```java
  InputStreamResponse response = new InputStreamResponse();
response.setBody(formatter.getResultStream(), formatter.getByteCount());
// InputStream resultsStream = formatter.getResultStream();
// StreamReader reader = new StreamReader(resultsStream);
// response.setContent(reader.read(formatter.getByteCount()));
```

Others who see that commented-out code won’t have the courage to delete it. They’ll think
it is there for a reason and is too important to delete. 

Good source code control systems  will remember the code for us. We don’t have to comment it out any more. Just
delete the code. We won’t lose it. Promise.

---

### HTML Comments
> HTML in source code comments is an abomination.
> It makes the comments hard to read in the one place where they should be easy to
read.

```java
/**
* Task to run fit tests.
* This task runs fitnesse tests and publishes the results.
* <p/>
* <pre>
* Usage:
* &lt;taskdef name=&quot;execute-fitnesse-tests&quot;
* classname=&quot;fitnesse.ant.ExecuteFitnesseTestsTask&quot;
* classpathref=&quot;classpath&quot; /&gt;
* OR
* &lt;taskdef classpathref=&quot;classpath&quot;
* resource=&quot;tasks.properties&quot; /&gt;
* <p/>
* &lt;execute-fitnesse-tests
* suitepage=&quot;FitNesse.SuiteAcceptanceTests&quot;
* fitnesseport=&quot;8082&quot;
* resultsdir=&quot;${results.dir}&quot;
* resultshtmlpage=&quot;fit-results.html&quot;
* classpathref=&quot;classpath&quot; /&gt;
* </
```
---

### Nonlocal Information
If you must write a comment, then make sure it describes the code it appears near. Don’t
offer systemwide information in the context of a local comment.
```java
/**
* Port on which fitnesse would run. Defaults to <b>8082</b>.
*
* @param fitnessePort
*/
public void setFitnessePort(int fitnessePort)
{
this.fitnessePort = fitnessePort;
}
```
---

### Too Much Information
Don’t put interesting historical discussions or irrelevant descriptions of details into your
comments.

```java
/*
RFC 2045 - Multipurpose Internet Mail Extensions (MIME)
Part One: Format of Internet Message Bodies
section 6.8. Base64 Content-Transfer-Encoding
The encoding process represents 24-bit groups of input bits as output
strings of 4 encoded characters. Proceeding from left to right, a
24-bit input group is formed by concatenating 3 8-bit input groups.
These 24 bits are then treated as 4 concatenated 6-bit groups, each
of which is translated into a single digit in the base64 alphabet.
When encoding a bit stream via the base64 encoding, the bit stream
must be presumed to be ordered with the most-significant-bit first.
That is, the first bit in the stream will be the high-order bit in
the first 8-bit byte, and the eighth bit will be the low-order bit in
the first 8-bit byte, and so on.
*/
```
---

### Inobvious Connection
The connection between a comment and the code it describes should be obvious.
> You’d like the reader to be able to look at the comment and the code and understand what the comment is talking about.
```java
/*
* start with an array that is big enough to hold all the pixels
* (plus filter bytes), and an extra 200 bytes for header info
*/
this.pngBytes = new byte[((this.width + 1) * this.height * 3) + 200];
```
---

### Function Headers
Short functions don’t need much description. A well-chosen name for a small function that
does one thing is usually better than a comment header.

---

### Java docs in non public code
> As useful as javadocs are for public APIs, they are anathema to code that is not intended
for public consumption
* Bad Comment example
```java
/**
* This class Generates prime numbers up to a user specified
* maximum. The algorithm used is the Sieve of Eratosthenes.
* <p>
* Eratosthenes of Cyrene, b. c. 276 BC, Cyrene, Libya --
* d. c. 194, Alexandria. The first man to calculate the
* circumference of the Earth. Also known for working on
* calendars with leap years and ran the library at Alexandria.
* <p>
* The algorithm is quite simple. Given an array of integers
* starting at 2. Cross out all multiples of 2. Find the next
* uncrossed integer, and cross out all of its multiples.
* Repeat untilyou have passed the square root of the maximum
* value.
*
* @author Alphonse
* @version 13 Feb 2002 atp
*/
import java.util.*;
public class GeneratePrimes
{
/**
* @param maxValue is the generation limit.
*/
public static int[] generatePrimes(int maxValue)
{
if (maxValue >= 2) // the only valid case
{
// declarations
int s = maxValue + 1; // size of array
boolean[] f = new boolean[s];
int i;
// initialize array to true.
for (i = 0; i < s; i++)
f[i] = true;
// get rid of known non-primes
f[0] = f[1] = false;
// sieve
int j;
for (i = 2; i < Math.sqrt(s) + 1; i++)
{
if (f[i]) // if i is uncrossed, cross its multiples.
{
for (j = 2 * i; j < s; j += i)
f[j] = false; // multiple is not prime
}
}
// how many primes are there?
int count = 0;
for (i = 0; i < s; i++)
{
if (f[i])
count++; // bump count.
}
int[] primes = new int[count];
// move the primes into the result
for (i = 0, j = 0; i < s; i++)
{
if (f[i]) // if prime
primes[j++] = i;
}
return primes; // return the primes
}
else // maxValue < 2
return new int[0]; // return null array if bad input.
}
}

```
---

* Refactored code
```java
/**
* This class Generates prime numbers up to a user specified
* maximum. The algorithm used is the Sieve of Eratosthenes.
* Given an array of integers starting at 2:
* Find the first uncrossed integer, and cross out all its
* multiples. Repeat until there are no more multiples
* in the array.
*/
public class PrimeGenerator
{
private static boolean[] crossedOut;
private static int[] result;
public static int[] generatePrimes(int maxValue)
{
if (maxValue < 2)
return new int[0];
else
{
uncrossIntegersUpTo(maxValue);
crossOutMultiples();
putUncrossedIntegersIntoResult();
return result;
}
}
private static void uncrossIntegersUpTo(int maxValue)
{
crossedOut = new boolean[maxValue + 1];
for (int i = 2; i < crossedOut.length; i++)
crossedOut[i] = false;
}
private static void crossOutMultiples()
{
int limit = determineIterationLimit();
for (int i = 2; i <= limit; i++)
if (notCrossed(i))
crossOutMultiplesOf(i);
}
private static int determineIterationLimit()
{
// Every multiple in the array has a prime factor that
// is less than or equal to the root of the array size,
// so we don't have to cross out multiples of numbers
// larger than that root.
double iterationLimit = Math.sqrt(crossedOut.length);
return (int) iterationLimit;
}
private static void crossOutMultiplesOf(int i)
{
for (int multiple = 2*i;
multiple < crossedOut.length;
multiple += i)
crossedOut[multiple] = true;
}
```
--- 
## References
* Clean Code - ch4
* [Five code comments you should stop writing // and one you should start](https://www.freecodecamp.org/news/5-comments-you-should-stop-writing-and-1-you-should-start-4d66a367cd2c/)
* [Comments In Your Code](https://medium.com/better-programming/comments-in-your-code-730cfd1dde02)
* [Clean Code – Comments and Formatting](https://www.todaysoftmag.com/article/1120/clean-code-comments-and-formatting)
* [Clean Code Slides](https://www.slideshare.net/arturoherrero/clean-code-8036914)