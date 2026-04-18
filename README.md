# Near-Chat-regression
Near chat regression testing
package nearChat;

import java.awt.AWTException;
import java.awt.Robot;
import java.awt.Toolkit;
import java.awt.datatransfer.StringSelection;
import java.awt.event.KeyEvent;
import java.time.Duration;

import org.openqa.selenium.By;
import org.openqa.selenium.JavascriptExecutor;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.chrome.ChromeOptions;
import org.openqa.selenium.support.ui.Select;
import io.github.bonigarcia.wdm.WebDriverManager;

public class LoginClass 
{

	public static void main(String[] args) throws InterruptedException, AWTException 
	{
		
		
		
		WebDriverManager.chromedriver().setup();
		//ChromeDriver driver = new ChromeDriver();
	    ChromeOptions options = new ChromeOptions();
	    options.addArguments("use-fake-media-for-media-stream");
		options.addArguments("use-fake-ui-for-media-stream"); 
	
		ChromeDriver driver = new ChromeDriver(options);


		driver.get("https://nearchat.nearconferences.com/");
		driver.manage().window().maximize();
		driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(30));
		Thread.sleep(100);
		
//		System.setProperty("webdriver.edge.driver", "msedgedriver.exe");
//
//		WebDriver driver = new EdgeDriver(options);
//		driver.get("https://your_URL_here");
//		
		
		
		
		
		
		// Login
		driver.findElement(By.id("formBasicEmail")).sendKeys("sonit@xgensys.biz");
		driver.findElement(By.id("formBasicPassword")).sendKeys("Xgen@123");
		Thread.sleep(500);
		driver.findElement(By.xpath("//button[@type='submit']")).click();
		Thread.sleep(500);
		// Search user
		WebElement search = driver.findElement(By.name("searchUser"));
		search.sendKeys("fathima");

		// Click on username
		driver.findElement(By.xpath("//div[@class='flex-grow-1 ms-3 f-15 rtl-chat-name']")).click();
		Thread.sleep(500);

		// find input filed& type text
		WebElement inputField = driver.findElement(By.xpath("//input [@name='message']"));
		String textOne = "Sony";
		inputField.sendKeys(textOne);

		// find send btn
		WebElement sendButton = driver.findElement(By.xpath("//div[@class = 'footer-action text-action']"));

		sendButton.click();

		for (int i = 0; i < 2; i++)
		{
			inputField.sendKeys(textOne);
			sendButton.click();

			try 
			{
				Thread.sleep(110); // Add a delay to avoid overloading the server
			} 
			catch (InterruptedException e)
			{
				e.printStackTrace();
			}
		}

		// to group text message
		//WebElement searchgroup =
		
		Thread.sleep(5000);
				driver.findElement(By.xpath("//input[@name= 'searchUser']")).clear();
	
		
	
	
		WebElement searchgroup =	driver.findElement(By.xpath("//input[@name= 'searchUser']"));
		searchgroup.sendKeys("GroupOne");
		

		driver.findElement(By.xpath("//div[@class='flex-grow-1 ms-3 f-15 rtl-chat-name']")).click();
		Thread.sleep(500);

		//text in group
		WebElement inputFieldo = driver.findElement(By.xpath("//input [@name='message']"));
		String texttwo = "text send to group one";
		inputFieldo.sendKeys(texttwo);

		sendButton.click();

		// voice in group
		WebElement voice = driver.findElement(By.xpath("//div[@class='footer-action voice-action']"));
		voice.click();
		Thread.sleep(5000);
		voice.click();
		sendButton.click();

		Thread.sleep(500);

		//image in group
		WebElement image = driver.findElement(By.xpath("//div[@class='footer-action file-action']"));
		image.click(); 
		
		WebElement photos = driver.findElement(By.xpath("//button[@class='dropdown-item'][3]"));
		photos.click();
		String path = "file:C:\\Users\\user\\Desktop\\fgt.jpg"; //path of the file
		Robot r = new Robot();
		StringSelection s = new StringSelection(path); //store the path to string s 
		Toolkit.getDefaultToolkit().getSystemClipboard().setContents(s, null);  //set the content
		
		Thread.sleep(2000);
		 r.keyPress(KeyEvent.VK_CONTROL);
		    r.keyPress(KeyEvent.VK_V);
		    r.keyRelease(KeyEvent.VK_V);
		    r.keyRelease(KeyEvent.VK_CONTROL);
		    
		   
		  
		    r.keyPress(KeyEvent.VK_ENTER);
		    Thread.sleep(2000);
		    r.keyRelease(KeyEvent.VK_ENTER);
		 
		    Thread.sleep(2000);
		    WebElement photoSendIcon =    driver.findElement(By.xpath("//div[@class='sendAction']"));
		    photoSendIcon.click();
		    
		    
		    
		    
		    Thread.sleep(2000);
		  //document in group   
		    
		    WebElement imageDoc = driver.findElement(By.xpath("//div[@class='footer-action file-action']"));
		    imageDoc.click();
		    WebElement doc = driver.findElement(By.xpath("//button[@class='dropdown-item'][1]"));
		    doc.click();
		    
			
			
	    StringSelection ss = new StringSelection("C:\\Users\\user\\Desktop\\Jasheer.pdf");
	     Toolkit.getDefaultToolkit().getSystemClipboard().setContents(ss, null);
	     
	     Thread.sleep(2000);
	    
	     Robot ro = new Robot();
		 ro.keyPress(KeyEvent.VK_CONTROL);
	 	 ro.keyPress(KeyEvent.VK_V);
	 	 ro.delay(250);
 	     ro.keyRelease(KeyEvent.VK_CONTROL);
		 ro.keyRelease(KeyEvent.VK_V);
		 ro.delay(250);
		 ro.keyPress(KeyEvent.VK_ENTER);
		 ro.delay(250);
		 ro.keyRelease(KeyEvent.VK_ENTER);
		WebElement sendicon = driver.findElement(By.xpath("//div[@class='sendAction']"));
		sendicon.click();
		 Thread.sleep(2000);
		 
		// Camera in group
		 WebElement camerattachment = driver.findElement(By.xpath("//div[@class='footer-action file-action']"));
		 camerattachment.click();
		 
		 
		 WebElement camera = driver.findElement(By.xpath("//button[@class='dropdown-item'][2]"));
		 camera.click();
		
		 Thread.sleep(5000);
		 WebElement addMore = driver.findElement(By.xpath("/html/body/div/main/section/div/div/div/div/div[2]/div[1]/div/div[3]/div/div[3]"));
		
		 addMore.click();
		 
		 driver.findElement(By.xpath("//div[@class='sendAction']")).click();
		 
		 //Polling/html/body/div/main/section/div/div/div/div/div[2]/div[10]/div[4]/div/div[1]/div/div/button[1]
		 //Poling
		 driver.findElement(By.xpath("//div[@for='buttonAppsOptions']")).click();
		 driver.findElement(By.xpath("//button[contains(text(),'Polling')]")).click();
		
		 Thread.sleep(2000);
		 
		 //enter question
		 WebElement questionField = driver.findElement(By.xpath("//textarea[@rows='2']"));
		 questionField.sendKeys("here is the polling question here is the polling question");
		 
		 //tick check box anonymousPolling
		 
		 WebElement	Checkbox= driver.findElement(By.xpath("//input[@name='anonymousPolling']"));
		 Checkbox.click();
		 
		 //Click on add item
		 
		 WebElement	addItem = driver.findElement(By.xpath("//div[@class='add-item']"));
		 addItem.click();
		 
		 //Enter textin new option field
		 
		 WebElement	newOp = driver.findElement(By.xpath("/html/body/div/main/section/div/div/div/div/div[2]/div[6]/div/div[2]/div/div/div/form/div[3]/div[3]/div/div/input\r\n"));
		 String optext ="option c";
		 newOp.sendKeys(optext);
	 
	 for (int i = 0; i < 5; i++) 
	 {
		 
		 addItem.click(); 
//		 newOp.sendKeys(optext);
//		 sendButton.click();
		 
	
		

		try 
     	{
			Thread.sleep(110); // Add a delay to avoid overloading the server
		} 
		catch (InterruptedException e)
		{
			e.printStackTrace();
			
	
	}
	 }
	 
	 
	 WebElement	optFour = driver.findElement(By.xpath("/html/body/div/main/section/div/div/div/div/div[2]/div[6]/div/div[2]/div/div/div/form/div[3]/div[4]/div/div/input"));
	 optFour.sendKeys("option D");
	 
	 WebElement	optFive = driver.findElement(By.xpath("/html/body/div/main/section/div/div/div/div/div[2]/div[6]/div/div[2]/div/div/div/form/div[3]/div[5]/div/div/input"));
	 optFive.sendKeys("option e");
	 
	 WebElement	optSix = driver.findElement(By.xpath("/html/body/div/main/section/div/div/div/div/div[2]/div[6]/div/div[2]/div/div/div/form/div[3]/div[6]/div/div/input"));
	 optSix.sendKeys("option f");
	 
	 
	 WebElement	optSeven = driver.findElement(By.xpath("/html/body/div/main/section/div/div/div/div/div[2]/div[6]/div/div[2]/div/div/div/form/div[3]/div[7]/div/div/input"));
	 optSeven.sendKeys("option g");
	 
	 WebElement	optEight = driver.findElement(By.xpath("/html/body/div/main/section/div/div/div/div/div[2]/div[6]/div/div[2]/div/div/div/form/div[3]/div[8]/div/div/input"));
	 optEight.sendKeys("option h"); 
	 
	 
	 WebElement startPollBtn =driver.findElement(By.xpath("//button[contains(text(),'Start Poll')]"));
	 startPollBtn.click();
	 
	 //WebDriver driver = new ChromeDriver();
	 JavascriptExecutor js = (JavascriptExecutor) driver;
	 js.executeScript("window.scrollBy(0, 5000);");
	 
//	 Thread.sleep(2000);
//	 WebElement eblPolOption =driver.findElement(By.xpath("/html/body/div/main/section/div/div/div/div/div[2]/div[10]/div[2]/div/div[321]/div/div[2]/div[10]/div/input"));
//	 eblPolOption.click();
	
	 
	 //tasks
	 
	 driver.findElement(By.xpath("//div[@for='buttonAppsOptions']")).click();
	 driver.findElement(By.xpath("//button[contains(text(),'Tasks')]")).click();
	 WebElement addTask =driver.findElement(By.xpath("//button[contains(text(),'Add Task')]"));
		Thread.sleep(500);

	 
	 addTask.click();
	 
	 // Task name 
	 WebElement taskname =driver.findElement(By.xpath("//input[@name='taskName']"));
	 taskname.sendKeys("Todo task to sony");
		Thread.sleep(500);

	 
	 //Click on Save
	 
	 
	 
	 WebElement save =driver.findElement(By.xpath("//button[contains(text(),'Save')]"));
	 save.click();
	
	 Thread.sleep(4000);
	 //Ongoing
		
	 driver.findElement(By.xpath("//button[contains(text(),'Add Task')]")).click();
	 driver.findElement(By.xpath("//input[@name='taskName']")).sendKeys("ongoing task to fathima");
	
	 WebElement statusDropdown = driver.findElement(By.xpath("//select[@name='status']"));
	 Select s1 = new Select(statusDropdown);
	 s1.selectByVisibleText("Ongoing");
	 
	 Thread.sleep(2000);
	 //Select assign to
	 WebElement assigntoDropdown = driver.findElement(By.xpath("//select[@name='assignTo']"));
	 Select s2 = new Select(assigntoDropdown);
	 s2.selectByVisibleText("Fathima Thasni");
	 driver.findElement(By.xpath("//button[contains(text(),'Save')]")).click();
	 
	 Thread.sleep(4000);
	 
	 //pending
	 
	 driver.findElement(By.xpath("//button[contains(text(),'Add Task')]")).click();
	 driver.findElement(By.xpath("//input[@name='taskName']")).sendKeys("pendong task to sony");
	
	 WebElement statusDropdownt = driver.findElement(By.xpath("//select[@name='status']"));
	 Select s5 = new Select(statusDropdownt);
	 s5.selectByValue("Pending");
	 
	 //Select assign to
	 WebElement assigntoDropdownt = driver.findElement(By.xpath("//select[@name='assignTo']"));
	 Select s6 = new Select(assigntoDropdownt);
	 s6.selectByVisibleText("Soni Thankachan");
	 driver.findElement(By.xpath("//button[contains(text(),'Save')]")).click();
	 
	 
	 //completed
	 
	 driver.findElement(By.xpath("//button[contains(text(),'Add Task')]")).click();
	 driver.findElement(By.xpath("//input[@name='taskName']")).sendKeys("Completed task to fathima");
	
	 WebElement statusDropdownta = driver.findElement(By.xpath("//select[@name='status']"));
	 Select s8 = new Select(statusDropdownta);
	 s8.selectByValue("Completed");
	 
	 //Select assign to
	 WebElement assigntoDropdownta = driver.findElement(By.xpath("//select[@name='assignTo']"));
	 Select s9 = new Select(assigntoDropdownta);
	 s9.selectByVisibleText("Fathima Thasni");
	 driver.findElement(By.xpath("//button[contains(text(),'Save')]")).click();
	 
	 //click on ongoing menu
	 
	 driver.findElement(By.xpath("//a[@id='left-tabs-example-tab-Ongoing']")).click();
	 Thread.sleep(2000);
	 
	 //click on pending menu
	 driver.findElement(By.xpath("//a[@id='left-tabs-example-tab-Pending']")).click();
	 Thread.sleep(2000);
	 
	 
	 //click on completed menu
	 driver.findElement(By.xpath("//a[@id='left-tabs-example-tab-Completed']")).click();
	 Thread.sleep(2000);
	 
// click on close button
 driver.findElement(By.xpath("/html/body/div/main/section/div/div/div/div/div[2]/div[3]/div/div[1]/div/div/div[2]")).click();
	
	 
	 //Click on Imoji
	 
	 driver.findElement(By.xpath("//div[@class='footer-action emoji-action']")).click();
	 
	 driver.findElement(By.xpath("//button[@data-full-name='smiley,smiling face with open mouth']")).click();
	 
	 
	 driver.findElement(By.xpath("//div[@class='footer-action text-action']")).click();
	
	 
	 //3 menu 
    WebElement menu= driver.findElement(By.xpath("/html/body/div/main/section/div/div/div/div/div[2]/div[10]/div[1]/div/div/div/div[5]/span/div/button"));
    menu.click();
    
    
   	//Group info
    
    WebElement groupInfo= driver.findElement(By.xpath("//button[contains(text(),'Group info')]"));
    groupInfo.click();
	Thread.sleep(500);

    
	// addevents
    WebElement addEvents= driver.findElement(By.xpath("//button[contains(text(),'Add events')]"));
    addEvents.click();
	Thread.sleep(500);

    // enter text in the Details
    
    WebElement addDetails = driver.findElement(By.xpath("//textarea[@name='selectedEventDetails']"));
    addDetails.sendKeys("entering the first event");
	Thread.sleep(500);

    
    //click on date field
    
    WebElement dateField = driver.findElement(By.xpath("//div[@class='react-datepicker__input-container']"));
    dateField.click();
	Thread.sleep(500);

  
    //date
    
    WebElement date = driver.findElement(By.xpath("//div[contains(text(),'5')]"));
    date.click();
    
    //duration
    WebElement duration = driver.findElement(By.xpath("//select[@name='selectedEventDuration']"));
    duration.click();
    Select sa = new Select(duration);
    sa.selectByVisibleText("Full Day");
    
    //click on save btn
    
    WebElement savebtn = driver.findElement(By.xpath("//button[contains(text(),'Save')]"));
    savebtn.click();
  
    //clicks on add paicipant 
    
    WebElement addPaticipant = driver.findElement(By.xpath(" //button[contains(text(),'Add participant')]"));
    addPaticipant.click();
    
  //  search field
  WebElement usersearchField = driver.findElement(By.xpath("//input[@id='searchUser']"));
  usersearchField.sendKeys("akhila");
  
  // Robot ro = new Robot();
     ro.keyPress(KeyEvent.VK_ENTER);
	 ro.delay(250);
	 ro.keyRelease(KeyEvent.VK_ENTER);
  
  
 //select ahkila warrior from the search list 
  WebElement usrsearchList = driver.findElement(By.xpath("//div[contains(text(),'Akhila OUtlook CV')]"));
  usrsearchList.click();
  
  
  //Click on add participant btn
  
//  WebElement addParticipant = driver.findElement(By.xpath("/html/body/div/main/section/div/div/div/div/div[2]/div[4]/div[2]/div/div/div[2]/div/div[2]/div[2]/form/div[4]/button')]"));
//  addParticipant.click();
  
  //close the events page
  
  WebElement closebtnEventPage = driver.findElement(By.xpath("/html/body/div/main/section/div/div/div/div/div[2]/div[4]/div[1]/div/div/div[2]"));
  closebtnEventPage.click();
  
  //Click on 3 dots
  menu.click();
  
  //close chat 
  WebElement closeChat = driver.findElement(By.xpath("//button[contains(text(),'Close chat')]"));
  closeChat.click();
  
  
 //Click on menu to create group
  
  WebElement menuButon = driver.findElement(By.xpath("//div[@title='Menu']"));
  menuButon.click();
  
  //Click on Create group
  
  WebElement createGroup  = driver.findElement(By.xpath("//button[contains(text(),'New Group')]"));
  createGroup.click();
  
  //Group name field
  
  WebElement groupName  = driver.findElement(By.xpath("//input[@id='groupName']"));
  groupName.sendKeys("NEW GROUP ");
  Thread.sleep(1000);
  
  //Add data in 'About' field
  
  WebElement aboutField  = driver.findElement(By.xpath("//textarea[@name='groupBio']"));
  aboutField.sendKeys("NEW GROUP ONE ABOUT FIELD");
  Thread.sleep(1000);
  
  //Clik onnext button
  
  WebElement nextButton  = driver.findElement(By.xpath("//button[@class='btn btn-primary rotate-180 btn btn-primary']"));
  nextButton.click();
  
  
  
  
//add user
  
  WebElement addUserField  = driver.findElement(By.xpath("//input[@id='searchUser']"));
  addUserField.sendKeys("vishak");
  
     ro.keyPress(KeyEvent.VK_ENTER);
	 ro.delay(250);
	 ro.keyRelease(KeyEvent.VK_ENTER);


	 
	  WebElement addUser = driver.findElement(By.xpath("//div[contains(text(),'vishakrn@xgensys.biz')]"));
      addUser.click();
	  
      WebElement createButton = driver.findElement(By.xpath("//button[contains(text(), 'Create')]"));
      createButton.click();
      
 
  
// Search field clear
      
      driver.findElement(By.xpath("//input[@name= 'searchUser']")).clear();
  	
//Click on menu
      menuButon.click();
      
//Click on create channel
      
      WebElement createChannel  = driver.findElement(By.xpath("//button[contains(text(),'Create Channel')]"));
      createChannel.click();
      
      
 //Enter Channel Name
      WebElement channelNameField  = driver.findElement(By.xpath("//input[@name='channelName']"));
      channelNameField.sendKeys("Public channel four");
      
      
//     Enter Description Name
      WebElement descriptionField  = driver.findElement(By.xpath("//textarea[@name='channelDesc']"));
      descriptionField.sendKeys("Entering descripion");
      
 // Click on create
      
      WebElement createBtnChannel  = driver.findElement(By.xpath("//button[contains(text(),'Create')]"));
      createBtnChannel.click();
      
// click on created channel name from the list
      
      WebElement channelname  = driver.findElement(By.xpath("//div[contains(text(),'Public channel four')]"));
      channelname.click();
      
 //     Click on 3 dot
      
      WebElement dropwntwo  = driver.findElement(By.xpath("//div[@class='actions-btn-no-hover']"));
      dropwntwo.click(); 
      
 //clicks on channel info
     
   WebElement channelInfo  = driver.findElement(By.xpath(" //button[contains(text(),'Channel info')]"));
    channelInfo.click();
    
//      // edit channel info click -unable to lacate  
//      
//      WebElement editChannelInfoIcon  = driver.findElement(By.xpath("/html/body/div/main/section/div/div/div/div/div[2]/div[4]/div[2]/div/div/div[1]/div/div/div/div[2]/p[1]"));
//      editChannelInfoIcon.click();
//      
//      
//      //edit chanel info textarea  click
//      Thread.sleep(1000);
//      
//      WebElement editInfofield  = driver.findElement(By.xpath("//textarea[@id='groupDesc']"));
//      editInfofield.sendKeys("updated");
//      
//      WebElement saveClick  = driver.findElement(By.xpath("//div[@title='Save']"));
//      saveClick.click();
//      
      //click on publi channel
      
      WebElement publicChannelO = driver.findElement(By.xpath("//select[@name='channelType']"));
      publicChannelO.click();
      Thread.sleep(1000);
      Select sy = new Select(publicChannelO);
      sy.selectByValue("Private");
      Thread.sleep(1000);
      
      //Click on copy link
     
      WebElement copyLink = driver.findElement(By.xpath("//button[contains(text(),'Copy link')][1]"));
      copyLink.click();
      Thread.sleep(2000);
      
      //Click on close button
//      WebElement closeBtnTwo = driver.findElement(By.xpath("/html/body/div/main/section/div/div/div/div/div[2]/div[4]/div[1]/div/div/div[2]"));
//      closeBtnTwo.click();
//     
//      Thread.sleep(1000);
      
      //click on chat menu
      
      driver.findElement(By.xpath("//span[@title='Chat']")).click();
      
      //Search username in chat
      WebElement searchOne = driver.findElement(By.name("searchUser"));
      searchOne.sendKeys("fathima");
      //selevt user
      driver.findElement(By.xpath("//div[@class='flex-grow-1 ms-3 f-15 rtl-chat-name']")).click();
	 Thread.sleep(100);
	 
	 // click on iput fiels
	 
	   driver.findElement(By.xpath("//input[@name='message']")).click();
		Thread.sleep(100);
	 
	 //[paste the link & enter
	 
	 ro.keyPress(KeyEvent.VK_CONTROL);
 	 ro.keyPress(KeyEvent.VK_V);
 	 ro.delay(250);
	     ro.keyRelease(KeyEvent.VK_CONTROL);
	 ro.keyRelease(KeyEvent.VK_V);
	 ro.delay(250);
	 ro.keyPress(KeyEvent.VK_ENTER);
	 ro.delay(250);
	 ro.keyRelease(KeyEvent.VK_ENTER);
     
     
	 
	//click on profile
	 WebElement profilePic= driver.findElement(By.xpath("//div[@class='position-relative profile-section']"));
	 profilePic.click();
	 Thread.sleep(500);
	 
	 //Click on profile pic
	 
	 WebElement changeProfilePic= driver.findElement(By.xpath("/html/body/div/main/section/div/div/div/div/div[1]/div[1]/div[4]/div/div[2]/div/div/div[1]/div[1]/div/img"));
	 Thread.sleep(1000);
	 changeProfilePic.click();
	 Thread.sleep(100);
	 
	 String patha = "file:C:\\Users\\user\\Desktop\\onam.jpg"; //path of the file
		Robot rp = new Robot();
		StringSelection sb = new StringSelection(patha); //store the path to string s 
		Toolkit.getDefaultToolkit().getSystemClipboard().setContents(sb, null);  //set the content
		
		Thread.sleep(2000);
		 rp.keyPress(KeyEvent.VK_CONTROL);
		    rp.keyPress(KeyEvent.VK_V);
		    rp.keyRelease(KeyEvent.VK_V);
		    rp.keyRelease(KeyEvent.VK_CONTROL);
		    
		   
		  
		    rp.keyPress(KeyEvent.VK_ENTER);
		    Thread.sleep(2000);
		    rp.keyRelease(KeyEvent.VK_ENTER);
      
		    
		    //Edit profile fields
			 WebElement profieSave= driver.findElement(By.xpath("//button[@class='nj-btn-primary btn btn-primary']"));
			 profieSave.click();
			 Thread.sleep(6000);
		    
			 WebElement firstNamef = driver.findElement(By.xpath("//input[@id='firstName']"));
			 firstNamef.clear();
			 Thread.sleep(1000);
			 firstNamef.sendKeys("Soni");
			 
			 Thread.sleep(1000);

			 WebElement lastNamef = driver.findElement(By.xpath("//input[@id='lastName']"));
			 lastNamef.clear();
			 Thread.sleep(1000);
			 lastNamef.sendKeys("Thankachan");
			 Thread.sleep(1000);
			 
			 WebElement poneNum = driver.findElement(By.xpath("//input[@type='tel']"));
			 poneNum.clear();
			 Thread.sleep(1000);
			 poneNum.sendKeys("3434354435");
			 Thread.sleep(1000);
			 
			 WebElement about = driver.findElement(By.xpath("//textarea[@name='about']"));
			 about.clear();
			 Thread.sleep(1000);
			 about.sendKeys(" about edited");
			 Thread.sleep(1000);
			 
			 Thread.sleep(1000);
			 WebElement sendIcono = driver.findElement(By.xpath("//button[contains(text(),'Save')]"));
			 sendIcono.click();
			 
			 Thread.sleep(10000);
			 driver.findElement(By.cssSelector("div.py-4.px-4.d-lg-block > div.d-flex.align-items-center > div.flex-grow-1.pl-3.text-white > svg.pro-back-icon")).click();
			
			 
			 Thread.sleep(1000);
			 driver.findElement(By.xpath("//input[@name='searchUser']")).clear();
//			 Thread.sleep(300);
//			 WebElement lastNamef = driver.findElement(By.xpath("//input[@id='lastName']"));
//			 lastNamef.sendKeys("LN");
//			 
//			 Thread.sleep(300);//input[@name='searchUser']
//			 WebElement poneNum = driver.findElement(By.xpath("//input[@value='+966']"));
//			 poneNum.sendKeys("343435443543");
//			 
//			 Thread.sleep(300);
//			 
//			 WebElement about = driver.findElement(By.xpath("//textarea[@name='about']"));
//			 about.sendKeys(" about edited");
//			 
//			 WebElement sendIcon = driver.findElement(By.xpath("//button[@type='submit']"));
//			 sendIcon.click();
//			 
			 
			 
		 
    //div[@title='Save']
      
    //div[@class= 'dropstart']
      
   
    //div[contains(text(),'Public channel one')]  
      
      //input[@name = 'channelName']
      
//button[contains(text(),'Close chat')]//
  
  
  

	 
	 
    
     
  //button[contains(text(),'Save')]
	
		// driver.findElement(By.xpath("button[@class='dropdown-item'][1]")).click();
		 
		//button[@class='dropdown-item'][1]
		 
		 
		// /html/body/div/main/section/div/div/div/div/div[2]/div[1]/div/div[3]/div/div[3
		 // Polling
		// WebElement camerattachment = driver.findElement(By.xpath("/html/body/div/main/section/div/div/div/div/div[2]/div[1]/div/div[3]/div/div[3]']"));
		//div[@class='dropdown']
		 
		 
		
//		 
//		 
//		 WebDriverWait wait = new WebDriverWait (driver, Duration.ofSeconds(500));
//		 wait.until(ExpectedConditions.visibilityOfElementLocated(By.xpath("//div[@title='Retake'")));
//		 
//		 driver.findElement(By.xpath("//div[@title='Retake'")).click();
		 
		
	// New group
		 
		 
		 
		 
		/*footer-action file-action
		 * // //// EdgeOptions options = new EdgeOptions(); //
		 * options.setCapability("permissions.default.microphone", 1); //// ////
		 * WebDriverWait wait= new WebDriverWait (driver, Duration.ofSeconds(500)); ////
		 * Alert alert = wait.until(ExpectedConditions.alertIsPresent()); ////
		 * alert.accept(); //// //// Thread.sleep(2000); //// sendButton.click(); ////
		 * 
		 * //WebElement file=
		 * driver.findElement(By.xpath("//svg[@stroke='currentColor']"));
		 * //file.click();
		 * 
		 * // Robot r = new Robot(); // r.keyPress(KeyEvent.VK_ENTER); //
		 * r.keyRelease(KeyEvent.VK_ENTER); //
		 */

		// driver.findElement(By.xpath("//submit[text()='Login']")).click();

	}

}
