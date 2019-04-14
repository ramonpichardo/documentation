* Set the following global environment value to update the command prompt  
`setx PROMPT [%USERNAME%@%COMPUTERNAME%$S$D$S$T$H$H$H]$_$M$_$P$G$S /M`  
* Set the following global environment value to update the PATH for Cygwin  
`setx PATH "%PATH%;C:\cygwin64\bin" /M`  
* Set the following global environment value to update the PATH for PSTools (32-bit)  
`setx PATH "%PATH%;C:\Program Files (x86)\PSTools\" /M`  
* Set the following global environment value to update the PATH for PSTools (64-bit)  
`setx PATH "%PATH%;C:\Program Files\PSTools64\" /M`  
* Call a command prompt from either `cmd.exe` or "`Command Prompt`" in Start window.  
* Set the following properties in each instance:  
  * Tabs  
    * Edit Options  
      * Check to enable both "QuickEdit Mode" and " Insert Mode"  
    * Font  
      * Size: 14  
      * Font: Lucida Console  
    * Layout  
      * Screen Buffer Size  
        * Width: 110  
        * Height: 9999  
      * Windows Size  
        * Width: 110  
        * Height: 55  
      * Windows Position  
        * Let system position window  
    * Colors  
      * Screen Text: R=0, G=255, B=255  
      * Screen Background: R=0, G=0, B=0  
      * Popup Text: R=128, G=0, B=128  
      * Popup Background: R=255, G=255, B=255  

Reference: http://www.hanselman.com/blog/ABetterPROMPTForCMDEXEOrCoolPromptEnvironmentVariablesAndANiceTransparentMultiprompt.aspx 
