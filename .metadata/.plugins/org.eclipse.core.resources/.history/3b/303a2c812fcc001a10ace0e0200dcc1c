package com.Muntasirlab.demoProject;

import org.testng.ITestResult;
import org.testng.annotations.AfterMethod;
import org.testng.annotations.BeforeMethod;
import org.testng.annotations.Test;

import junit.framework.Assert;
import net.rcarz.jiraclient.BasicCredentials;
import net.rcarz.jiraclient.Field;
import net.rcarz.jiraclient.Issue;
import net.rcarz.jiraclient.JiraClient;
import net.rcarz.jiraclient.JiraException;

import org.openqa.selenium.chrome.ChromeDriver;
import java.util.concurrent.TimeUnit;
import org.openqa.selenium.WebDriver;

public class TestClass {

	public static WebDriver driver;
	
	@BeforeMethod
	public void launchDriver() {
		System.setProperty("webdriver.chrome.driver", "C:\\PayPal backup\\mavendemo\\mavendemo\\chromedriver.exe");
		driver = new ChromeDriver();
		driver.manage().timeouts().implicitlyWait(10, TimeUnit.SECONDS);
		driver.manage().window().fullscreen();
		
	}
	
	@Test
	public void Test1() {
		driver.navigate().to("https://google.com");
		System.out.println("Test 1 title is"+driver.getTitle());
	}
	@Test
	public void Test2() {
		
		driver.navigate().to("https://google.com");
		System.out.println("Test 2 title is"+driver.getTitle());
	}
	@Test
	public void Test3() {
		driver.navigate().to("https://google.com");
		System.out.println("Test 3 title is"+driver.getTitle());
	    Assert.assertEquals("Expected Title", driver.getTitle());
	
    }
	
	@AfterMethod
	public void quit(ITestResult result) throws JiraException {
		driver.quit();
		if(result.getStatus() == ITestResult.FAILURE) {
			BasicCredentials creds = new BasicCredentials("muntasirg","Vfr$5tgb");
			JiraClient jira = new JiraClient("http://localhost:8090", creds);
			Issue issueName = jira.createIssue("DEMO", "Bug").field(Field.SUMMARY, result.getMethod().getMethodName() + "is failed"+ result.getThrowable().toString()).field(Field.DESCRIPTION, "get the description").execute();
		    System.out.println("Issue is created in JIRA with issue key: "+issueName.getKey());
		}
	}
}
