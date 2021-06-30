---
title: 'Print Server'
media_order: 'Screen Shot 2021-02-10 at 11.54.27 am.png'
---

# Installing The Spiff Print Server 

## Prerequisites
Windows 10 however earlier versions should also work.
8GB Ram. 4GB might be passable.
10-20 GB Approx Free Hard Drive Space allowing for PDF downlaods.
Optional: A printer that is installed with a working print driver.

## Steps To Install Print Server

1. Download the [print server 2.0.36](https://s3-ap-southeast-2.amazonaws.com/local.code.spiff.com.au/spiff-print-server-releases/spiff-print-server-2.0.36.zip)
2. Unzip to `c:\Program Files\spiff-print-server`
3. In the install folder edit the file called App.config. Make sure to set the correct locationId according to the location details of your partner. This can be discovered by logging in to the spiff hub by going to the Nav Bar and clicking on Partner => My Account and then scrolling down to the locations Card near the bottom. 

![](https://help.spiff.com.au/user/pages/12.developer/04.print-server/Screen%20Shot%202021-02-10%20at%2011.54.27%20am.png)


4. Next install the print server as a windows service. Open a command prompt in administrator mode
5. Change the directory to the install location of the print server. In this case execute the command `cd c:\Program Files\spiff-print-server`
6. To install the service run the executable `print-server.exe install`. Note this step may say "complete" even if the service is not installed.
7. Verify the install. Open windows services. Start -> Administration Tools -> Services
8. Find the service "Spiff Printer Agent" in the service list and start it. Note if the service does not appear this is most likely due to an issue with step 6. Repeat step 6 and ensure that the command prompt is running in administrator mode. 
9. Double Click on the Spiff Print Server service and open the User TAB and enter the user credentials in the log in and password fields.
10. Verify everything works by sending a test print. Allow up to 30 seconds for the PDF file to land on your machine.
11. Verify the PDF is as expected.

> Note: When the machine is attached to a domain, ensure that both Ghostscript and the Spiff Print Server are installed on the same domain account.

## Steps To Create Individual Folders by Product

Step 1 - Open the App.Config File for the print Server 
Step 2 - add the following line `<productionDownloadFolder123-123-123-123>e:\some\location</productionDownloadFolder123-123-123-123>` where 123-123-123-123 = product Id from spiff and `e:\some\location` is the location of the folder on the hard drive of the computer  
Step 3 - Repeat this process for each product   
Step 4 - Save the File  
Step 5 - Restart the Service  


## Configruation Settings
The print server is configured with XML and is found in the App.config file. The following is an incomplete list of the configuration items that are avaiable.

|name|value|notes|
|----|----|----|
|location|string|The id of the spiff location. This should be set from within the hub|
|doPrinting|boolean|True if the PDF needs to be sent to the preconfigured print device. You will need to make sure the printer name has been set correctly|
|productionDownloadFolder${id}|string|The path to the folder of the product that has the ID within the tag. Note this will be moved to an attribute in the future|
|printerCount|number|The number of attached printers to the current print server. These will be printed to using a round robin stragity to increase thoughput. Make sure each printier in the cluster is named ${printerName}\_1, ${printName}\_2 etc etc|

## Uninstalling The Print Server

Step 1 - Open the Command Prompt in Administrator mode  
Step 2 - Change Directory to the Current Spiff Print Server cd `c:\ProgramFiles\Spiff-Print-Server-xx`
Step 3 - type in `print-server.exe uninstall`  
Step 4 - Ensure Spiff Print Server Agrent does not appear in the Services Window anymore.  
Step 5 - Delete the Folder in program Files  

```
<?xml version="1.0" encoding="utf-8"?>

<configuration>
    <commandLineArgs>-sDEVICE=mswinpr2 -dORIENT1=false -dNOPROMPT -dPrinted -dBATCH -dNOPAUSE -dNOSAFER -q </commandLineArgs>
    <configUrl>https://services.spiff.com.au/agents/credentials</configUrl>
    <defaultPaperHeight>0.0</defaultPaperHeight>
    <defaultPaperWidth>0.0</defaultPaperWidth>
    <defaultPrinterName>Brother DCP-1510 series</defaultPrinterName>
    <deleteFileAfterPrinting>false</deleteFileAfterPrinting>
    <doPrinting>false</doPrinting>
    <downloadFolder>E:\KOKO Common\RICOH PRINTER\WORKFLOWS\Fiery JobFlow\JobFlow_KOKOVM001\Gift Cards</downloadFolder>
    <gsPrintExecutable>C:\Program Files\gs\gs9.23\bin\gswin64c.exe</gsPrintExecutable>
    <location>3f39351474974d9590c78203e9c0841d</location>
    <logFilePath>C:/spiff-print/print-server.log</logFilePath>
    <logLevel>Error</logLevel>
 <!--Main products-->
    <productDownloadFoldercbf29963-3eb6-444a-8f09-d6fb191c18f4>E:\Koko Common\RICOH PRINTER\WORKFLOWS\Fiery JobFlow\JobFlow_KOKOVM001\9 Praline Sleeve - ONLINE</productDownloadFoldercbf29963-3eb6-444a-8f09-d6fb191c18f4>
    <productDownloadFolderebde6100-2a99-44b8-ae6f-86c513a5ab23>E:\Koko Common\RICOH PRINTER\WORKFLOWS\Fiery JobFlow\JobFlow_KOKOVM001\16 Praline Sleeve - ONLINE</productDownloadFolderebde6100-2a99-44b8-ae6f-86c513a5ab23>
    <productDownloadFolder06b350b8-3082-403c-ba65-e3d82c620ad7>E:\Koko Common\RICOH PRINTER\WORKFLOWS\Fiery JobFlow\JobFlow_KOKOVM001\25 Praline Sleeve - ONLINE</productDownloadFolder06b350b8-3082-403c-ba65-e3d82c620ad7>
    <productDownloadFoldera548aa85-9ff4-4081-bbaf-23379ba17e05>E:\Koko Common\RICOH PRINTER\WORKFLOWS\Fiery JobFlow\JobFlow_KOKOVM001\Sleeve for  Allround GIFT CUBE - ONLINE</productDownloadFoldera548aa85-9ff4-4081-bbaf-23379ba17e05>
    <productDownloadFolder0b588238-826b-4309-b950-5f6791834d2b>E:\Koko Common\RICOH PRINTER\WORKFLOWS\Fiery JobFlow\JobFlow_KOKOVM001\49 SLEEVE - ONLINE</productDownloadFolder0b588238-826b-4309-b950-5f6791834d2b>   
    <productDownloadFolder7f9827a8-c84d-404e-b93f-4e789b8c9c45>E:\Koko Common\RICOH PRINTER\WORKFLOWS\Fiery JobFlow\JobFlow_KOKOVM001\36 SLEEVE - ONLINE</productDownloadFolder7f9827a8-c84d-404e-b93f-4e789b8c9c45> 
    <productDownloadFolder59b6951e-ba95-4588-b5c9-a3694497fe64>E:\Koko Common\RICOH PRINTER\WORKFLOWS\Fiery JobFlow\JobFlow_KOKOVM001\Gift Cards</productDownloadFolder59b6951e-ba95-4588-b5c9-a3694497fe64>
    <productDownloadFoldera13f5c0b-34a9-42f5-b86e-b89b86ee45be>E:\Koko Common\RICOH PRINTER\WORKFLOWS\Fiery JobFlow\JobFlow_KOKOVM001\Gift Cards</productDownloadFoldera13f5c0b-34a9-42f5-b86e-b89b86ee45be>
    <productDownloadFolder89b6298f-3c17-466b-9e69-29fe20175a22>E:\Koko Common\RICOH PRINTER\WORKFLOWS\Fiery JobFlow\JobFlow_KOKOVM001\Gift Cards</productDownloadFolder89b6298f-3c17-466b-9e69-29fe20175a22>
    <productDownloadFolder4d2ee17e-e3ff-401b-a03a-c249141e2724>E:\Koko Common\RICOH PRINTER\WORKFLOWS\Fiery JobFlow\JobFlow_KOKOVM001\Gift Cards</productDownloadFolder4d2ee17e-e3ff-401b-a03a-c249141e2724>
   <!--Teachers Poem Products-->
    <productDownloadFolder0ed022dc-5dcd-4b65-8c25-f5bbc9bf0f98>E:\Koko Common\RICOH PRINTER\WORKFLOWS\Fiery JobFlow\JobFlow_KOKOVM001\16 Praline Sleeve - ONLINE</productDownloadFolder0ed022dc-5dcd-4b65-8c25-f5bbc9bf0f98>
    <productDownloadFolder40e3c9b7-398e-4da1-b3e4-611906301d05>E:\Koko Common\RICOH PRINTER\WORKFLOWS\Fiery JobFlow\JobFlow_KOKOVM001\25 Praline Sleeve - ONLINE</productDownloadFolder40e3c9b7-398e-4da1-b3e4-611906301d05>
     <!--Christmas Poem Products-->
    <productDownloadFoldera359863e-72e4-41d1-9210-cb0378ebae44>E:\Koko Common\RICOH PRINTER\WORKFLOWS\Fiery JobFlow\JobFlow_KOKOVM001\16 Praline Sleeve - ONLINE</productDownloadFoldera359863e-72e4-41d1-9210-cb0378ebae44>
    <productDownloadFolder73295adb-0c08-4065-99e5-0e1e3be85512>E:\Koko Common\RICOH PRINTER\WORKFLOWS\Fiery JobFlow\JobFlow_KOKOVM001\25 Praline Sleeve - ONLINE</productDownloadFolder73295adb-0c08-4065-99e5-0e1e3be85512>
    <!--Internal Products-->
    <productDownloadFolder7538c0ed-eb7f-694f-e03f-e7356bfc0a66>E:\Koko Common\RICOH PRINTER\WORKFLOWS\Fiery JobFlow\JobFlow_KOKOVM001\9 Praline Sleeve - ONLINE</productDownloadFolder7538c0ed-eb7f-694f-e03f-e7356bfc0a66>
    <productDownloadFolder841d3b9b-5d81-fd5d-e86f-809e7b813468>E:\Koko Common\RICOH PRINTER\WORKFLOWS\Fiery JobFlow\JobFlow_KOKOVM001\16 Praline Sleeve - ONLINE</productDownloadFolder841d3b9b-5d81-fd5d-e86f-809e7b813468>
    <productDownloadFolder51abfe1c-7cdb-f49c-bb5e-3676bcfaca7d>E:\Koko Common\RICOH PRINTER\WORKFLOWS\Fiery JobFlow\JobFlow_KOKOVM001\25 Praline Sleeve - ONLINE</productDownloadFolder51abfe1c-7cdb-f49c-bb5e-3676bcfaca7d>
    <productDownloadFoldera24adc2a-6a04-2c17-af2d-c1639b20ec89>E:\Koko Common\RICOH PRINTER\WORKFLOWS\Fiery JobFlow\JobFlow_KOKOVM001\Sleeve for  Allround GIFT CUBE - ONLINE</productDownloadFoldera24adc2a-6a04-2c17-af2d-c1639b20ec89>
    <productDownloadFolder7449fe85-9b61-e217-2b5e-fc5e79b96a05>E:\Koko Common\RICOH PRINTER\WORKFLOWS\Fiery JobFlow\JobFlow_KOKOVM001\49 SLEEVE - ONLINE</productDownloadFolder7449fe85-9b61-e217-2b5e-fc5e79b96a05>   
    <productDownloadFolder7f9827a8-c84d-404e-b93f-4e789b8c9c45>E:\Koko Common\RICOH PRINTER\WORKFLOWS\Fiery JobFlow\JobFlow_KOKOVM001\36 SLEEVE - ONLINE</productDownloadFolder3a8d35a5-b14a-7b01-08fb-3ddb49d72557> 
    <!--Gift Cards Internal-->
    <productDownloadFolderd073c56a-aa65-a266-f0f7-0707aa750339>E:\Koko Common\RICOH PRINTER\WORKFLOWS\Fiery JobFlow\JobFlow_KOKOVM001\Gift Cards</productDownloadFolderd073c56a-aa65-a266-f0f7-0707aa750339>
    <productDownloadFolderbb07d81a-2f7b-f171-223e-9d5357b8aa3a>E:\Koko Common\RICOH PRINTER\WORKFLOWS\Fiery JobFlow\JobFlow_KOKOVM001\Gift Cards</productDownloadFolderbb07d81a-2f7b-f171-223e-9d5357b8aa3a>
    <productDownloadFolder73f54a2b-e9e5-ef71-9902-eca145c51548>E:\Koko Common\RICOH PRINTER\WORKFLOWS\Fiery JobFlow\JobFlow_KOKOVM001\Gift Cards</productDownloadFolder73f54a2b-e9e5-ef71-9902-eca145c51548>
    <!--Easter Bunny Range-->
    <productDownloadFolder5857ca2e-cd40-4568-ab8b-5889cdf79238>E:\Koko Common\RICOH PRINTER\WORKFLOWS\Fiery JobFlow\JobFlow_KOKOVM001\Easter - Sleeve - Littlest Bunny</productDownloadFolder5857ca2e-cd40-4568-ab8b-5889cdf79238>
    <productDownloadFolder43e3c645-0aed-4319-ba05-ce1692e428aa>E:\Koko Common\RICOH PRINTER\WORKFLOWS\Fiery JobFlow\JobFlow_KOKOVM001\Easter - Sleeve - Double Trouble</productDownloadFolder43e3c645-0aed-4319-ba05-ce1692e428aa>
    <productDownloadFolder1ccb6e3e-9e18-456e-ab19-4206d2bbb909>E:\Koko Common\RICOH PRINTER\WORKFLOWS\Fiery JobFlow\JobFlow_KOKOVM001\Easter - Sleeve - Three of a kind</productDownloadFolder1ccb6e3e-9e18-456e-ab19-4206d2bbb909>
    <productDownloadFolder0b5503e4-23b2-4c5f-a80e-9e4b8259b0b1>E:\Koko Common\RICOH PRINTER\WORKFLOWS\Fiery JobFlow\JobFlow_KOKOVM001\Easter - Sleeve - Mightiest Bunny</productDownloadFolder0b5503e4-23b2-4c5f-a80e-9e4b8259b0b1>
    <productDownloadFolder55de74b6-60c2-4546-993c-2fd539c46400>E:\Koko Common\RICOH PRINTER\WORKFLOWS\Fiery JobFlow\JobFlow_KOKOVM001\Easter - Sleeve - Dozen Praline Eggs</productDownloadFolder55de74b6-60c2-4546-993c-2fd539c46400>

     <writeCopies>true</writeCopies>
    <printerCount>1</printerCount>
</configuration>
```

## Steps To Install Ghost Script. 

Note: Ghost script is only required if prints need to be sent direclty to a printer. If there is some other software device that handles printing from a hot folder these steps can be skipped.

1. Click the link to Download [Ghostscript 9.23](https://github.com/ArtifexSoftware/ghostpdl-downloads/releases/download/gs923/gs923w64.exe) for the 64 bit version. You should not ever install the 32 bit version.
2. Double click the installer 
3. Hit the next button until the installer is done. Default settings are fine and nothing more needs to be done in GhostScript. 
