Create User
```
$secpass = Read-Host "Password" -AsSecureString
New-ADUser -Name "BLACK Joe" -SamAccountName "jblack" -UserPrincipalName "jblack@acme.com" -AccountPassword $secpass -Path "OU=IT,OU=Employees,OU=Montreal,DC=acme,DC=com" -Enabled $true
```

Create User by Copying Account
```
$secpass = Read-Host "Password" -AsSecureString
$user = Get-ADUser -Identity jblack -Properties memberof, office
New-ADUser -Name "BEAN Francis" -SamAccountName fbean -UserPrincipalName "fbean@acme.com" -AccountPassword $secpass -Path "cn=Users,dc=acme,dc=com" -Enabled:$true -Instance $user
```

Bulk AD user account creation
```
$secpass = Read-Host "Password" -AsSecureString
Import-Csv names.csv | foreach {$name = "$($_.LastName) $($_.FirstName)"
 New-ADUser -GivenName $($_.FirstName) -Surname $($_.LastName) 
 -Name $name -SamAccountName $($_.SamAccountName) 
 -UserPrincipalName "$($_.SamAccountName)@acme.com" 
 -AccountPassword $secpass -Path "cn=Users,dc=acme,dc=com" 
 -Enabled:$true
}
```

Modify User Attribute
```
Set-ADUser -Identity "CN=BLACK Joe,OU=IT,OU=Employees,OU=Montreal,DC=Acme,DC=com" -OfficePhone "987-6541"
```

