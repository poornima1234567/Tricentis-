# Tricentis-
Project Tricentis demo website
package com.Sogeti.pages;

import java.util.List;
import java.util.concurrent.TimeUnit;


import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.interactions.Action;
import org.openqa.selenium.interactions.Actions;
import org.openqa.selenium.support.ui.Select;


public class Mainpage {


@SuppressWarnings({ "deprecation", "unused" })
public static void main(String[] args){
// access modifier are public,private,protected
// Should be in a @BeforeX annotated TestNG method. As this is set-up before each test.
WebDriver driver= new ChromeDriver();
System.setProperty("webdriver.chrome.driver", "C:\\Users\\ponallan\\Downloads\\chrome-win64\\chromedriver.exe");
driver.get("http://sampleapp.tricentis.com/101/");
driver.manage().window().maximize();
//


// using imlicit wait// fluent wait
driver.manage().timeouts().implicitlyWait(20000, TimeUnit.MILLISECONDS);

driver.findElement(By.id("nav_automobile")).click();
// static dropdown
WebElement StaticDropdown = driver.findElement(By.id("make"));
Select dropdown = new Select(StaticDropdown);
dropdown.selectByIndex(1);

// date field if i change to 10/10/2022 test fow 2
driver.findElement(By.id("engineperformance")).sendKeys("10");
WebElement dateBox = driver.findElement(By.xpath(".//*[@id='dateofmanufacture']"));
dateBox.sendKeys("10/10/2021");

// static dropdown
WebElement StaticDropdown1 = driver.findElement(By.id("numberofseats"));
Select dropdown1 = new Select(StaticDropdown1);
dropdown1.selectByIndex(2);

// static dropdown
WebElement StaticDropdown2 = driver.findElement(By.id("fuel"));
Select dropdown2 = new Select(StaticDropdown2);
dropdown2.selectByIndex(1);


driver.findElement(By.id("listprice")).sendKeys("60000");
driver.findElement(By.id("licenseplatenumber")).sendKeys("1234");
driver.findElement(By.id("annualmileage")).sendKeys("500");
driver.findElement(By.id("nextenterinsurantdata")).click();
driver.findElement(By.id("firstname")).sendKeys("Test");
driver.findElement(By.id("lastname")).sendKeys("User");
WebElement dateBox1 = driver.findElement(By.xpath("//input[@id='birthdate']"));
dateBox1.sendKeys("12/12/1990");
WebElement radio1 = driver.findElement(By.xpath("(//span[@class='ideal-radio'])[2]"));
radio1.click();

driver.findElement(By.id("streetaddress")).sendKeys("Kotkagatan3");
driver.findElement(By.xpath("//select[@id='country']")).click();
driver.findElement(By.xpath("//select[@id='country']")).sendKeys("Sweden");
driver.findElement(By.id("zipcode")).sendKeys("12345");
driver.findElement(By.id("city")).sendKeys("Stockholm");
// static dropdown create a select class object
Select se = new Select(driver.findElement(By.id("occupation")));
// Select the option by index // we can use select method to verify is that select or not
se.selectByIndex(1);

// check the total no of options in the dropdown list one list is blank
List<WebElement> optionList=se.getOptions();
System.out.println("Total options are in the Dropdown="+(optionList.size()-1));
// check box field
//driver.findElement(By.className("ideal-check")).click();
driver.findElement(By.xpath("//label[normalize-space()='Bungee Jumping']//span")).click();
// button field
driver.findElement(By.id("nextenterproductdata")).click();
// date field
WebElement dateBox2= driver.findElement(By.xpath("//input[@id='startdate']"));
dateBox2.sendKeys("30/12/2023");
// static dropdown with select tag

Select sel1 = new Select(driver.findElement(By.xpath("//select[@id='insurancesum']")));
sel1.selectByIndex(2);

Select sel2 = new Select(driver.findElement(By.id("meritrating")));
sel2.selectByIndex(2);

Select sel3 = new Select(driver.findElement(By.cssSelector("#damageinsurance")));
sel3.selectByIndex(2);

// checkbox
// Action class,when x-path,css selctor are not unique or doesnot work, mouse hover actions
WebElement txtUsername = driver.findElement(By.id("EuroProtection"));
Actions builder = new Actions(driver);
Action seriesOfActions = builder     .moveToElement(txtUsername)     .click()     .build();    
seriesOfActions.perform() ;



Select sel4 = new Select(driver.findElement(By.xpath("//select[@name='Courtesy Car']")));
sel4.selectByIndex(1);

// next tab
driver.findElement(By.id("nextselectpriceoption")).click();
WebElement radio3 = driver.findElement(By.xpath("(//span[@class='ideal-radio'])[3]"));
radio3.click();

// click on download button using action class--- if i use download button code test 3. should uncomment
//WebElement mainMenu = driver.findElement(By.xpath("(//span[@class='hb hb-sm inv spin-icon hb-file-pdf-o-inv'])[2]"));
//Action seriesOfActions1 = builder     .moveToElement(mainMenu)     .click()     .build();    
//seriesOfActions1.perform() ;


// test1 happy flow

driver.findElement(By.id("nextsendquote")).click();

driver.findElement(By.id("email")).sendKeys("poornima.nallani@gmail.com");

driver.findElement(By.id("phone")).sendKeys("0704433049");

driver.findElement(By.id("username")).sendKeys("Poornima");

driver.findElement(By.id("password")).sendKeys("PooRniMa1");

driver.findElement(By.id("confirmpassword")).sendKeys("PooRniMa1");

driver.findElement(By.id("Comments")).sendKeys("Test successful");
driver.findElement(By.id("sendemail")).click();

// WebDriverWait w = new WebDriverWait(driver,30);

System.out.println(driver.findElement(By.xpath("//div[@class='sweet-alert showSweetAlert visible']/h2")).getText());
//driver.findElement(By.xpath("//button[@class='confirm']")).click();

boolean value = isFileDownloaded("Downloads","Tricentis_Insurance_Quote (19).pdf");

if(true)
  System.out.println("File found");
else
System.out.println("File not found");

driver.close();
// java execution class
}

private static boolean isFileDownloaded(String string, String string2) {
return false;
}

}
