# Power-Shell-command-to-block-software-to-access-Internet-using-folder-
in windows 11  a Power shell command  to auto bock the access of internet  

1) open Poweshell as admanster
2) copy and make changes to the  $folderPath using notepade 
3) copy the folder daractory and past in  " "
4) it will automatically scan and islote ever software which access internet using windows defender firewall with Advance Security
5) you can see the creat in the outbound rules 


The command to be copied → ▼

$folderPath = "C:\Path\To\Your\Folder"
$executables = Get-ChildItem -Path $folderPath -Recurse -Filter "*.exe"

foreach ($exe in $executables) {
    $ruleName = "Block_" + $exe.Name
    New-NetFirewallRule -DisplayName $ruleName -Direction Outbound -Program $exe.FullName -Action Block
    Write-Host "Blocked: $($exe.FullName)"
}
