1. Project structure
	
	![](_attachments/Screenshot%202.png)
	- When *resource error* occur when build application: try to clean -> build (option show in VS) these project in order BaseControl -> TaskCommonUI -> CommonUI -> TaskDroidUI -> DroidUI -> TaskShellUI -> ShellUI -> DroidApp (sometime you need to remove bin and obj folder when clean not work)
	- CloudBanking.BaseControl: this is where you put all custom control (included layout file, code behind, dimen, color) for reuse able entire project, 
	- ClouBanking.CommonUI: this is where you put all common dialog, activity for reuse able purpose (**Note**: this is just contain code behind)
	- CloudBanking.TaskCommonUI, TaskDroidUI, TaskShellUI: this is where you put layout file for CommonUI project meaning that this project don't have any code behind in it, only xml file put in resource folder. **NOTE: these project will also use when need to change UI of default control**
	- DroidUI, ShellUI contain UI that will show to the user, it will use control from TaskDroidUI, TaskShellUI or BaseControl to make layout file
	- DroidApp: is the application project that you need to select when want to run app
	**NOTE: Applying this structure for reusable purpose, each company will have different UI folder, currently having StandardUI and TaskUI and will have more in the future**
2. Convert from Figma px to dp or sp: 
	ex: selected dpi is 320 and px want to convert is 40
	px = dp * (dpi/160)
	dp = px / (dpi / 160) = 40 / (320/160) = 20
	ex: If you want to set px 40 you need to define 20dp margin in code if your device setup is 320dpi
	![](_attachments/Screenshot%201.png)
	
	*Note* 
	Current application using scaleable dp lib for define dimen so when you want to create 20dp instead of:
	`<dimen name="base_screen_padding">20dp</dimen>`
	use 
	`<dimen name="base_screen_padding">@dimen/_20sdp</dimen>`
	s is stand for scalable
3. **All reusable dimen, color, drawable, etc. must put in BaseControl project**
	
	Adding layout start with TaskUI, starting to put base dimen in base_dimen.xml file
	
	![](_attachments/Screenshot%202023-05-13%20at%2011.29.57.png)
4. Specific dimen for TaskUI (not use for all app) must define in TaskDroidUI resources folder
	
	![](_attachments/Screenshot%202023-05-13%20at%2011.32.44.png)
5. How to custom a base control to correct with design of each company (eg: Task)
		Checkout for ButtonWithVectorIcon to know how to create new custon control to adapt with new design