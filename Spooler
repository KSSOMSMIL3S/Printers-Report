#this is written in PowerShell format
#using this to run or restart my printer spooler service
#file path for document report, can be wherever your print server is located
#you can use the FQDN or IP address I'm just using a fake sample so replace the path with your file location
$file= '\\9.9.9.9\drivers\print report\printer report.txt'
#get the printer status, the printer name, and the computer name
Get-Printer -ComputerName 9.9.9.9 | select printerstatus, name, computername | foreach {
  if ($_.PrinterStatus -ne 'normal')
    {if (Test-Connection -ComputerName $_.ComputerName -Quiet)
      {Invoke-Command -ComputerName $_.ComputerName -ScriptBlock {Restart-Service -Name Spooler} }}} | Out-File -LiteralPath -$file -Append
