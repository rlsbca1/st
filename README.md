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
// Store window id
ArrayList<String> wid = new 
ArrayList<String>(driver.getWindowHandles());
// Switch the tab to latest tab
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
// Get count of CheckBoxes present
List<WebElement> checkboxes = 
driver.findElements(By.xpath("//input[@type='checkbox']"));
System.out.println(checkboxes.size() + " Number of CheckBoxes");
// Get count of Dropdown menus
List<WebElement> dropdown = driver.findElements(By.tagName("select"));
System.out.println(dropdown.size() + " Number of DropDown Menus");
// Get count no’ of radio buttons
List<WebElement>radioBtns = 
driver.findElements(By.xpath("//input[@type='radio']"));
System.out.println(radioBtns.size() + " Number of Radio Buttons");
driver.close();
}
}
```

