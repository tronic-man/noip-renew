

# Automatically confirm noip.com free hosts

[noip.com](https://www.noip.com/) free hosts expire every month.
This script uses [Selenium](https://www.selenium.dev/) and [GAS](https://script.google.com/home) to automatically renew hosts

 - [Selenium](https://www.selenium.dev/) is used to automatically navigate No-IP.com to renew the hosts.
 - [GAS](https://script.google.com/home) is used to grab the OPTs from your gmail inbox. 
.



Please Note
-
- This Script has not yet been thoroughly tested.
- This Script only works with Only Gmail Users



Part 1 - Google Apps Script:
-
 - Create a New [Google Apps Script](https://script.new)
 - Paste the following code in the editor 
>function doGet(e) {
>    var threads = GmailApp.getInboxThreads();
>    for (x = 0; x < threads.length; x++) {
>        if (threads[x].getFirstMessageSubject().includes('No-IP Verification Code:')) {
>            var code = threads[x].getFirstMessageSubject().split(': ')[1];
>            break
>        }
>    }
>    return HtmlService.createHtmlOutput('&' + code + '&')
>}
 - Publish as a web app
	 - Click 'Deploy' in the top right
	 - Click 'New Deployment'
	 - Click on the gear icon next to 'Select Type'
	 - Check 'Web App'
	 - Set 'Execute as' to 'Me (Your email)'
	 - Set 'Who has access to 'Anyone'
	 - Click 'Deploy'
	 - Save the Web App URL
	  
Part 2 - Configuring Logins.txt
-
 - On line 1 of 'Logins.txt', paste the Web App URL
 - On line 2 of 'Logins.txt', type the email for your No-IP Account
 - On line 3 of 'Logins.txt', type the password for your No-IP Account

Part 3 - Installing Repositories
-
- Install the following repositories
	- `pip install selenium`
	- `pip install requests`

Part 4 - Running the Script
-
- To run the script, just simply `cd` into the directory with the script files and run  `python run.py`

