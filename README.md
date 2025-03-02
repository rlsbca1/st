# 4
```

public class program1 {

	public static void main(String[] args) throws InterruptedException {
		// TODO Auto-generated method stub
		WebDriver driver=new ChromeDriver();
		driver.get("https://www.google.com/");
		driver.manage().window().maximize();
		String title =driver.getTitle();
		System.out.println(title);
		Thread.sleep(1000);
		WebElement t=driver.findElement(By.tagName("textarea"));
		t.sendKeys("youtube");
		t.submit();
		driver.findElement(By.xpath("//a[@href='https://www.youtube.com/']")).click();
		driver.navigate().refresh();
		String url=driver.getCurrentUrl();
		System.out.println(url);
		driver.manage().window().fullscreen();
		driver.navigate().back();
		Thread.sleep(2000);
		driver.close();
	}	
		
	
}
```
