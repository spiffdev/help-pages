---
title: 'Print Server'
---

# Installing The Spiff Print Server 

## Prerequisites
Windows 10 however earlier versions should also work.
8GB Ram. 4GB might be passable.
10-20 GB Approx Free Hard Drive Space allowing for PDF downlaods.
Optional: A printer that is installed with a working print driver.

## Steps To Install Ghost Script. 

Note ghost script is only required if prints need to be sent direclty to a printer. If there is some other software device that handles printing from a hot folder these steps can be skipped.

1. Download 9.23 of Ghostscript from https://github.com/ArtifexSoftware/ghostpdl-downloads/releases/download/gs923/gs923w64.exe for the 64 bit version. You should not ever install the 32 bit version.
2. Double click the installer 
3. Hit the next button until the installer is done. There should be no reason to change any default settings.

## Steps To Install Print Server

1. Download the print server from https://s3-ap-southeast-2.amazonaws.com/local.code.spiff.com.au/spiff-print-server-releases/spiff-print-server-2.0.34.zip
2. Unzip to `c:\Program Files\spiff-print-server`
3. In the install folder edit the file called App.config. Make sure to set the correct locationId according to the location details of your partner. This can be discovered by logging in to the spiff hub.
4. Next install the print server as a windows service. Open a command prompt in administrator mode
5. Change the directly to the install location of the print server. In this case execute the command `cd c:\Program Files\spiff-print-server`
6. To install the service run the executable `.\spiff-print-server.exe install`. Note this step may say "complete" even if the service is not installed.
7. Verify the install. Open windows services. Start -> Administration Tools -> Services
8. Find the service "Spiff Printer Agent" in the service list and start it. Note if the service does not appear this is most likely due to an issue with step 6. Repeat step 6 and ensure that the command prompt is running in administraotr mode.
9. Verify everything works by sending a test print. Allow up to 30 seconds for the PDF file to land on your machine.
10. Verify the PDF is as expected.

## Configruation Settings
|name|value|notes|
|----|----|----|
|location|string|The id of the spiff location. This should be set from within the hub|
|doPrinting|boolean|True if the PDF needs to be sent to the preconfigured print device. You will need to make sure the printer name has been set correctly|
|productionDownloadFolder${id}|string|The path to the folder of the product that has the ID within the tag. Note this will be moved to an attribute in the future|
|printerCount|number|The number of attached printers to the current print server. These will be printed to using a round robin stragity to increase thoughput. Make sure each printier in the cluster is named ${printerName}\_1, ${printName}\_2 etc etc|
