# 3. Write Selenium script to demonstrate Selenium WebDriver basic commands
```
packagecom.test;
importorg.openqa.selenium.*;
importorg.openqa.selenium.WebDriver;
importorg.openqa.selenium.chrome.ChromeDriver;
public class commands {
public static void main(String[] args) throws InterruptedException {
WebDriver driver=new ChromeDriver();
driver.get("https://www.google.com/");
driver.manage().window().maximize();
String title =driver.getTitle();
System.out.println(title);
Thread.sleep(1000);
WebElement t=driver.findElement(By.tagName("textarea"));
t.sendKeys("youtube");
t.submit();
driver.findElement(By.xpath("//h3[contains(text(),'YouTube')]")).click();
driver.navigate().refresh();
String url=driver.getCurrentUrl();
System.out.println(url);
driver.manage().window().fullscreen();
driver.navigate().back();
Dimension d=new Dimension(300,650);
driver.manage().window().setSize(d);
Thread.sleep(2000);
driver.close();
}
}
```


# 4. Write Selenium script to demonstrate Selenium WebDriver locators
```
package Automation;
importjava.util.concurrent.TimeUnit;
importorg.openqa.selenium.By;
importorg.openqa.selenium.WebDriver;
importorg.openqa.selenium.WebElement;
importorg.openqa.selenium.chrome.ChromeDriver;
public class locators {
public static void main(String[] args) throws InterruptedException {
WebDriver driver=new ChromeDriver();
driver.navigate().to("https://artoftesting.com/samplesiteforselenium");
driver.manage().window().maximize();
driver.manage().timeouts().implicitlyWait(5,TimeUnit.SECONDS);
String sampleText=driver.findElement(By.id("idOfDiv")).getText();
System.out.println(sampleText);
Thread.sleep(3000); 
driver.findElement(By.linkText("This is a link")).click();
driver.navigate().back();
driver.findElement(By.name("firstName")).sendKeys("Hi");
driver.findElement(By.name("firstName")).clear();
driver.findElement(By.xpath("//button[@id='idOfButton']")).click();
Thread.sleep(3000); 
driver.findElement(By.cssSelector("#female")).click();
driver.findElement(By.className("Automation")).click();
Thread.sleep(3000); 
WebElement image=driver.findElement(By.tagName("img"));
System.out.println(image.getAttribute("alt"));
driver.findElement(By.partialLinkText("Tutorial")).click();
driver.quit();
}
}
```

# 5. Write a script to demonstrate Gmail login using Selenium WebDriver
● Launch the browser and open “Gmail.com”.
● Verify the title of the page and print the verification result.
● Enter the username and Password.
● Click on the Sign in button.
● Wait for 10 seconds
● Close the web browser

```
package Automation;
importjava.time.Duration;
importjava.util.concurrent.TimeUnit;
importorg.openqa.selenium.By;
importorg.openqa.selenium.WebDriver;
importorg.openqa.selenium.chrome.ChromeDriver;
importorg.openqa.selenium.support.ui.ExpectedConditions;
importorg.openqa.selenium.support.ui.WebDriverWait;
public class gmail {
public static void main(String[] args) throws InterruptedException {
WebDriver driver=new ChromeDriver();
driver.manage().window().maximize();
driver.navigate().to("https://gmail.com/");
String expectedTitle="Gmail";
String actualTitle=driver.getTitle();
System.out.println(actualTitle);
driver.manage().timeouts().implicitlyWait(5,TimeUnit.SECONDS);
Thread.sleep(5000);
if(actualTitle.equals(expectedTitle))
{
System.out.println("Title is matching");
}
else {
System.out.println("Title is not matching");
}
driver.findElement(By.id("identifierId")).sendKeys("rlsbcademo2024@gmail.com");
driver.findElement(By.xpath("//span[normalize-space()='Next']")).click();
WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(30));
wait.until(ExpectedConditions.elementToBeClickable(By.cssSelector("input[name='P
asswd']")));
driver.findElement(By.cssSelector("input[name='Passwd']")).sendKeys("rlsbca123");
driver.findElement(By.xpath("//span[normalize-space()='Next']")).click();
Thread.sleep(3000);
System.out.println("Gmail login successful");
driver.close();
}
}


```


# 6. Write a script to add an item to cart of Amazon using Window handles method 
```
using Selenium WebDriver
package Selenium;
importjava.util.ArrayList;
importjava.util.concurrent.TimeUnit;
importorg.openqa.selenium.By;
importorg.openqa.selenium.WebDriver;
importorg.openqa.selenium.WebElement;
importorg.openqa.selenium.chrome.ChromeDriver;
public class amazon {
public static void main(String[] args) throws InterruptedException {
WebDriver driver = new ChromeDriver();
driver.get("https://www.amazon.in/");
driver.manage().window().maximize();
driver.manage().timeouts().implicitlyWait(10, TimeUnit.SECONDS);
driver.manage().deleteAllCookies();
Thread.sleep(2000);
WebElement searchbox = driver.findElement(By.id("twotabsearchtextbox"));
searchbox.sendKeys("samsung tv");
searchbox.submit();
Thread.sleep(2000);
driver.findElement(By.xpath("//span[contains(text(),'Samsung 80 cm (32 
inches) HD Ready Smart LED TV UA')]")).click();
Thread.sleep(2000);
ArrayList<String> wid = new 
ArrayList<String>(driver.getWindowHandles());
driver.switchTo().window(wid.get(1));
driver.findElement(By.xpath("//input[@id='add-to-cart-button']")).click();
Thread.sleep(2000);
System.out.println("Thank you for shopping");
driver.quit();
}
}
```


# 7. Black Box testing: (Functional Testing) Write a selenium script to test total number 
```
of objects present on the web page
packageSeleniumWebDriver;
importjava.util.List;
importjava.util.concurrent.TimeUnit;
importorg.openqa.selenium.By;
importorg.openqa.selenium.WebDriver;
importorg.openqa.selenium.WebElement;
importorg.openqa.selenium.chrome.ChromeDriver;
public class noOfObjects {
public static void main(String[] args) {
WebDriver driver = new ChromeDriver();
driver.manage().window().maximize();
driver.get("http://webdriveruniversity.com/Dropdown-CheckboxesRadioButtons/index.html");
driver.manage().timeouts().implicitlyWait(10, TimeUnit.SECONDS);
List<WebElement> checkboxes = 
driver.findElements(By.xpath("//input[@type='checkbox']"));
System.out.println(checkboxes.size() + " Number of CheckBoxes");
List<WebElement> dropdown = driver.findElements(By.tagName("select"));
System.out.println(dropdown.size() + " Number of DropDown Menus");
List<WebElement>radioBtns = driver.findElements(By.xpath("//input[@type='radio']"));
System.out.println(radioBtns.size() + " Number of Radio Buttons");
driver.close();
}
}
```

# 8. Black Box testing: (Load Testing) Design a web page to get the count of visitors who visit your web page  
```
<?php 
$countFile = 'visitor_count.txt'; 
// Function to increment the count and retrieve the updated value function incrementVisitorCount() { global $countFile; $count = 1; if (file_exists($countFile)) { 
$count = intval(file_get_contents($countFile)); 
$count++; } file_put_contents($countFile, $count); return $count; 
} 
$visitorCount = incrementVisitorCount(); 
?> 
<!DOCTYPE html> 
<html> 
<head> 
<title>Visitor Count Page</title> 
</head> 
<body> 
<h1>Welcome to the Visitor Count Page</h1> 
<p>Number of Visitors:</p> 
<div id="counter"><?php echo $visitorCount; ?></div> 
</body> 
</html> 
```

# 9. Black Box testing: (Functional Testing) Write a selenium script to test total number of objects present on the web page 
```
packageSeleniumWebDriver; importjava.util.List; importjava.util.concurrent.TimeUnit; importorg.openqa.selenium.By; importorg.openqa.selenium.WebDriver; importorg.openqa.selenium.WebElement; importorg.openqa.selenium.chrome.ChromeDriver; 
 
public class noOfObjects { 
	 	public static void main(String[] args) { 
 	 	WebDriver driver = new ChromeDriver();  	 	driver.manage().window().maximize(); 
	 	 	driver.get("http://webdriveruniversity.com/Dropdown-Checkboxes-
RadioButtons/index.html"); 
 	 	// Get count of CheckBoxes present  	 	List<WebElement> checkboxes = 
driver.findElements(By.xpath("//input[@type='checkbox']")); 
	 	 	System.out.println(checkboxes.size() + " Number of CheckBoxes"); 
	 	 	// Get count of Dropdown menus 
	 	 	List<WebElement> dropdown = driver.findElements(By.tagName("select")); 
	 	 	System.out.println(dropdown.size() + " Number of DropDown Menus"); 
 	 	// Get count no’ of radio buttons  	 	List<WebElement>radioBtns = 
driver.findElements(By.xpath("//input[@type='radio']")); 
	 	 	System.out.println(radioBtns.size() + " Number of Radio Buttons"); 
	 	 	driver.close(); 
	 	} 
} 

```

# 10. Black Box testing: (Functional Testing) Write and test a program to get the number of list items in a list / combo box 
# Drop.html
```
<html> 
<title>Write and test a program to get the number of list items in a list / combo box. </title> 
<body> 
<label>Select a Programming Language:</label> 
<select name="language" id="language"> 
<option value="javascript">JavaScript</option> 
<option value="python">Python</option> 
<option value="c++" disabled>C++</option> 
<option value="java" selected>Java</option> 
</select> 
</body> 
</html> 
```

```
packageSeleniumWebDriver; importjava.util.List; importorg.openqa.selenium.By; importorg.openqa.selenium.WebDriver; importorg.openqa.selenium.WebElement; importorg.openqa.selenium.chrome.ChromeDriver; importorg.openqa.selenium.support.ui.Select; public class drop { 
	 	public static void main(String[] args) { 
 	 	WebDriver driver = new ChromeDriver();  	 	driver.manage().window().maximize(); 
	 	 	// URL launch 
	 	 	driver.get("F:\\drop.html"); 
	 	 	// Identify list 
	 	 	Select items = new Select(driver.findElement(By.name("language"))); 
	 	 	List<WebElement>mylist = items.getOptions(); 
System.out.println("Number of items = " + mylist.size()); 
	 	 	driver.quit(); 
	 	} 
} 

```

# 11. Demonstrate how to handle Window Pop Up in Selenium WebDriver 
```
package test; 
 
import java.util.concurrent.TimeUnit; import org.openqa.selenium.Alert; import org.openqa.selenium.By; import org.openqa.selenium.WebDriver; import org.openqa.selenium.chrome.ChromeDriver; 
 
public class popUp { 
 
	 	public static void main(String[] args) throws InterruptedException { 
 	 	WebDriver driver = new ChromeDriver();  	 	driver.navigate().to("https://ksrtc.in/");  	 	driver.manage().window().maximize(); 
	 	 	driver.manage().timeouts().implicitlyWait(5, TimeUnit.SECONDS); 
	 	 	Thread.sleep(3000); 
 	 	 
	 	 	driver.findElement(By.id("submitSearch")).click(); 
 	 	 
	 	 	Alert simpleAlert = driver.switchTo().alert(); 
	 	 	String alertMessage= driver.switchTo().alert().getText(); 
 	 	System.out.println(alertMessage);  	 	Thread.sleep(2000); 
	 	 	simpleAlert.accept(); 
 	 	 	 
	 	 	driver.close(); 
	 	}
} 
```

#  12. Write and test a program to count number of Check boxes on the page checked and unchecked  
```
Checkbox.html 
<html> 
<body> 
<h2>Choose your Hobbies</h2> 
<input type="checkbox" name="hobby" value="Reading"> Reading<br> 
<input type="checkbox" name="hobby" value="Swiming"> Swiming<br> 
<input type="checkbox" name="hobby" value="Travelling"> Travelling<br> 
<input type="checkbox" name="hobby" value="Hiking"> Hiking<br> 
<input type="checkbox" name="hobby" value="Dancing"> Dancing<br> 
<br><br> 
</body> 
</html> 
 ```
# Selenium script 
```
package com.testing; 
 
import java.util.List; 
 
import org.openqa.selenium.By; import org.openqa.selenium.WebDriver; import org.openqa.selenium.WebElement; import org.openqa.selenium.chrome.ChromeDriver; 
 
public class checkbox { 
 
	 	public static void main(String[] args) throws InterruptedException { 
 	 	 
	 	 	WebDriver driver = new ChromeDriver(); 
 	 	driver.get("F:\\2023-24\\Odd\\Software Engineering and Testing\\SE and Testing Lab\\Checkbox.html"); 
 
 	 	driver.manage().window().maximize();
Thread.sleep(3000); 
 	 	driver.findElement(By.xpath("/html/body/input[1]")).click();
driver.findElement(By.xpath("/html/body/input[3]")).click();
List <WebElement> checkBox = driver.findElements(By.xpath("//input[@type='checkbox']")); 
 	 	 int checkedCount = 0;
      int uncheckedCount = 0; 
	 	 	 for (int i=0;i<checkBox.size();i++) 
	 	 	 { 
	 	 	  if ( checkBox.get(i).isSelected() == true) 
 	 	         checkedCount++;  	 	        else 
	 	 	         uncheckedCount++; 
	 	 	        } 
	 	 	 System.out.println("Number of checked checkboxes are " +checkedCount); 
 	 	 System.out.println("Number of unchecked checkboxes are " + uncheckedCount); 
 
 
	 	driver.close(); 
	 	} 
 	 } 
```

# 13. Write and test a program to update 10 student records into table into Excel file  
```
import java.io.FileInputStream; 
 
import java.io.FileOutputStream;
import jxl.Sheet;
import jxl.Workbook;
import jxl.write.Label;
import jxl.write.WritableSheet;
import jxl.write.WritableWorkbook; 
import org.testng.annotations.*; 
 
public class excel { 
 
    @BeforeClass // @BeforeClass runs once before the entire test
public void setUp() throws Exception { 
        // Initialization before tests, if needed 
    } 
 
    @Test 
    public void testImportExport1() throws Exception { 
        // Specify input and output file paths 
        String inputFile = "F:\\Software Engineering and Testing \\Students.xls";
 String outputFile = "F\\Software Engineering and Testing\\ Result.xls"; 
 
        // Read the Excel file 
        FileInputStream fi = new FileInputStream(inputFile); 
        Workbook w = Workbook.getWorkbook(fi); 
        Sheet s = w.getSheet(0); 
 
        // Initialize 2D array to store data from the sheet 
        String[][] a = new String[s.getRows()][s.getColumns()]; 
 
        // Create the output Excel file and writable sheet 
        FileOutputStream fo = new FileOutputStream(outputFile); 
        WritableWorkbook wwb = Workbook.createWorkbook(fo); 
        WritableSheet ws = wwb.createSheet("result1", 0); 
 
        // Write headers to the result sheet
for (int i = 0; i < s.getRows(); i++) {
for (int j = 0; j < s.getColumns(); j++) {
 a[i][j] = s.getCell(j, i).getContents();
// Read contents
 Label l2 = new Label(j, i, a[i][j]); // Write the data
 ws.addCell(l2); 
            } 
        } 
        // Add the "Result" label to the first row (header row) 
        Label resultLabel = new Label(s.getColumns(), 0, "Result");
ws.addCell(resultLabel); 
 
        // Process the data and calculate the result for each student
for (int i = 1; i < s.getRows(); i++) {
 for (int j = 2; j < s.getColumns(); j++) {
 a[i][j] = s.getCell(j, i).getContents();
int score = Integer.parseInt(a[i][j]);
 String result = (score > 35) ? "pass" : "fail"; 
 
                // Write the result to the "Result"
  Label resultCell = new Label(s.getColumns(), i, result);
   ws.addCell(resultCell); 
            } 
        } 
 
    wwb.write();
 wwb.close(); 
 
        System.out.println("Records successfully updated and saved to Result.xls"); 
    } 
} 
```

# 14. Write a program in java to test do…while construct using TestNG 
# sumOfNumbers.java 
```
package sumOfNumbers; 
 
public class sum { 
	 	public static void main(String[] args) { 
	 	int i = 1, sum = 0;do 
	 	{ 
 	 	sum += i; // sum=sum+i;  	 	i++; 
	 	} 
	 	while(i<=10); 
	 	 	System.out.println("The sum of numbers from 1 to 10 is: "+sum); 
	 	} 
	 	public static int calculateSum(int start, int end) { 
 	int i = start, sum = 0;  	do { 	 
 	sum += i;  	i++; 
	 	} while (i <= end); 
	 	 	 	return sum; 
	 	} 
} 
 ```
# sumOfNumbersTest.java 
```package dowhile.DoWhile; import org.testng.Assert; import org.testng.annotations.Test; import dowhile.SumOfNumbers; public class sumOfNumbersTest {   
	 	@Test 
 	public void testPositiveValuesInRange() {  	int expectedSum = 55; 
	 	int actualSum=sumOfNumbers.calculateSum(1,10); 
	 	Assert.assertEquals(actualSum,expectedSum); 
	 	} 
	 	@Test 
 	public void testNegativeValuesInRange() {  	int expectedSum =0; 
	 	int actualSum=sumOfNumbers.calculateSum(-10,10); 
	 	Assert.assertEquals(actualSum,expectedSum); 
	 	} 
	 	@Test 
	 	public void testOutOfRange() { 
 	 	//int expectedSum=155  	int expectedSum = 0; 
	 	int actualSum =sumOfNumbers.calculateSum(11,20); 
	 	Assert.assertEquals(actualSum,expectedSum); 
	 	} 
	} 	 
```

