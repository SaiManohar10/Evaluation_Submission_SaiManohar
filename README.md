# Evaluation_Submission_SaiManohar
Mobile App Testing


Project title : F-DROID
By : Sai Manohar
Description of the project : Validate the App using appium and Spring Tool Suite.
Instructions : The objective is to perform mobile app testing and to understand and implement
automated testing for mobile applications using Java and Appium.

1 .Download the file
2. paste inside SDK i.e, C:\Users\saima\AppData\Local\Android\Sdk\platform-tools
3. Open command prompt from this path 
4. Open emulator, to check whether device is attached give command : abd.exe devices
5. To install App in emulator give cmd : adb install "F-Droid.apk" 
6. App is Downloaded in the Emulator and is ready to Test.
7.Open STS Create a Maven Project add dependencies ,Add  Capability class in src/main/java & Test class in src/test/java
8.Start Appium 
9.Add esired capabilities to appium inspector and start session
10.Find locators
11.Add dependencies and host port details in src/main/java
12.Add locators and the actions to perform in src/test/java

* dependencies and host port details in src/main/java :

package capabilities;

import java.net.MalformedURLException;
import java.net.URL;

import org.openqa.selenium.remote.DesiredCapabilities;

import io.appium.java_client.android.AndroidDriver;
import io.appium.java_client.android.AndroidElement;
import io.appium.java_client.remote.AndroidMobileCapabilityType;
import io.appium.java_client.remote.AutomationName;
import io.appium.java_client.remote.MobileCapabilityType;

public class F_DROID_Capabilities {
	public static AndroidDriver<AndroidElement> capabilities1() throws MalformedURLException {
		DesiredCapabilities dc = new DesiredCapabilities();
		dc.setCapability(MobileCapabilityType.DEVICE_NAME, "OnePlus");
		dc.setCapability(MobileCapabilityType.PLATFORM_NAME, "Android");
		dc.setCapability(AndroidMobileCapabilityType.APP_PACKAGE,"org.fdroid.fdroid");
		dc.setCapability(AndroidMobileCapabilityType.APP_ACTIVITY,"org.fdroid.fdroid.nearby.SwapWorkflowActivity");
		dc.setCapability(MobileCapabilityType.NO_RESET, true);
		dc.setCapability(MobileCapabilityType.AUTOMATION_NAME, AutomationName.ANDROID_UIAUTOMATOR2);
		//server 0.0.0.0:4723 
		// 0.0.0.0 localHost/wd/hub 
		//in place webelement w e use androiddriver 
		
		//Automation Name for android is ANDROID_UIAUTOMATOR2
		AndroidDriver<AndroidElement> driver = new AndroidDriver<AndroidElement>(new URL("http://0.0.0.0:4723/wd/hub"), dc);
		//AndroidDriver<AndroidElement> driver = new AndroidDriver<AndroidElement>(new URL(htpps://0.0.0.0:4723/wd/hub),dc);
		return driver ;	
	}

}

* locators and the actions to perform in src/test/java
  public class F_DROID_appTest extends F_DROID_Capabilities {
	AndroidDriver<AndroidElement> driver;
	@BeforeTest
	public void bt() throws MalformedURLException, InterruptedException {
		  driver = capabilities1();
		  driver.manage().timeouts().implicitlyWait(10, TimeUnit.SECONDS);
		  	
	}
	
	@Test(enabled = true)
	public void test1() throws InterruptedException {
		System.out.println("F-Droid Opened");
		
	}





