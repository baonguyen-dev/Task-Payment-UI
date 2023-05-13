# 1. Project structure
	![[Screenshot 2023-05-13 at 10.48.55.png]]
	- When *resource error* occur when build application: try to clean -> build (option show in VS) these project in order BaseControl -> TaskCommonUI -> CommonUI -> TaskDroidUI -> DroidUI -> TaskShellUI -> ShellUI -> DroidApp (sometime you need to remove bin and obj folder when clean not work)
	- CloudBanking.BaseControl: this is where you put all custom control (included layout file, code behind, dimen, color) for reuse able entire project
	- ClouBanking.CommonUI: this is where you put all common dialog, activity for reuse able purpose (**Note**: this is just contain code behind)
	- CloudBanking.TaskCommonUI: this is where you put layout file for CommonUI project meaning that this project don't have any code behind in it, only xml file put in resource folder
	- DroidUI, TaskDroidUI, ShellUI, TaskShellUI are having the same structure
	- DroidApp: is the application project that you need to select when want to run app
	
	**NOTE: Applying this structure for reusable purpose, each company will have different UI folder, currently having StandardUI and TaskUI and will have more in the future**
	
# 2. Convert from Figma px to dp or sp: 
	ex: selected dpi is 320 and px want to convert is 40
	px = dp * (dpi/160)
	dp = px / (dpi / 160) = 40 / (320/160) = 20
	
	ex: If you want to set px 40 you need to define 20dp margin in code if your device setup is 320dpi
	![[Screenshot 2023-05-13 at 10.41.53.png]]
	*Note* 
	Current application using scaleable dp lib for define dimen so when you want to create 20dp instead of:
	`<dimen name="base_screen_padding">20dp</dimen>`
	use 
	`<dimen name="base_screen_padding">@dimen/_20sdp</dimen>`
	
	s is stand for scalable
# 3. 