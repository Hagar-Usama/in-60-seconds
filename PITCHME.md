

# //_Comments_ 
---

 
## Table of Contents

* [Good Comments](#Good-Comments)
* [Bad Comments](#Bad-Comments)
* [References](#References)


---
## Good Comments


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
> If comments are not inforamtives, add no value to your code, just remove them.

 The comment probably takes longer to read than the code itself.
 


```java
 // Utility method that returns when this.closed is true.  Throws an exception
 // if the timeout is reached.

 public synchronized void waitForClose(final long timeoutMillis)  throws Exception   {     
      if(!closed)      {       
       wait(timeoutMillis);
      if(!closed)
      throw new Exception("MockResponseSender could not be closed");      }

```

--- 

### Misleading Comments
> Code never lies, comments do sometimes

> Comments should desribe what your code **actualy** do, but not what you **wish** your code to do.

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


* Stating the Obvious
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


## References
* Clean Code - ch4
* [Five code comments you should stop writing // and one you should start](https://www.freecodecamp.org/news/5-comments-you-should-stop-writing-and-1-you-should-start-4d66a367cd2c/)
* [Comments In Your Code](https://medium.com/better-programming/comments-in-your-code-730cfd1dde02)
* [Clean Code – Comments and Formatting](https://www.todaysoftmag.com/article/1120/clean-code-comments-and-formatting)
* [Clean Code Slides](https://www.slideshare.net/arturoherrero/clean-code-8036914)
