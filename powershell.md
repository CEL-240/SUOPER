function q1($var2, $var3, $var4, $var5) {
    <#
    The parameters listed are the values of all angles in a polygon except one.
    Find and return the value of the remaining angle. If an impossible angle
    is found, return -1. The formula to find the sum of all angles of a polygon
    is `(n-2) * 180`, where `n` is the total number of angles.
    An impossible angle is one that is zero degrees (or less) or 360 degrees (or more).
    #>

  
    $totalSum = $var2 + $var3 + $var4 + $var5

 
    $totalPolygonSum = 540

    
    $missingAngle = $totalPolygonSum - $totalSum

    if ($missingAngle -le 0 -or $missingAngle -ge 360) {
        return -1
    } else {
        return $missingAngle
    }
}











function q2($arr,$key) {
    <# Search the 2 dimensional array for the first occurance 
      of key at column index 0 and return the value at column
      index 2 of the same row. Return -1 if the key is not found.
    #>

 foreach ($row in $arr) {
        if ($row[0] -eq $key) {
            return $row[2]
        }
    }
    return -1
}




function q3 {
    <# In a loop, prompt the user to enter a string until
       the user enters an empty string (length of 0) to 
       stop. Return the string with the maximum 
       length that the user entered."
	#>

 $maxString = ""

    while ($true) {
        $inputString = Read-Host "Enter a string (press Enter to stop):"
        if ([string]::IsNullOrEmpty($inputString)) {
            break
        }

        if ($inputString.Length -gt $maxString.Length) {
            $maxString = $inputString
        }
    }

    return $maxString
}
function q4($filename,$start) {
    <# Return the line of text from the file given by the `$filename
	   argument that begins with the text specified by `$start.
	   If no line in the file begins with the `$start text, return 
	   $null."
	#>

    $line = Get-Content $filename | Where-Object { $_.StartsWith($start) }

    if ($line) {
        return $line
    } else {
        return $null
    }
}




function q5($path) {
    <# Return the services in Stopped status sorted
       descending by their Name
	#>


    Get-Service | Where-Object { $_.Status -eq 'Stopped' } | Sort-Object -Property Name -Descending











}
function q6($filename) {
    <#
    Write each of the elements provided on the pipeline to the
    file specified by the $filename argument on separate lines
    #>

    process {
        # Write each pipeline element to the file
        $_ | Out-File -FilePath $filename -Append
    }
}

function q7 {
    <#
    Return the list of all startup apps that have an 
    AppId 'not ending in }'.
    #>


  Get-StartApps | Where-Object {$_.AppID -notmatch '}$'}
  
    


}















function q8($arr) {
    <# Combine the provided `$arr argument into a string separated 
       by a '-' between each element and return 
       this string #>

    $combinedString = $arr -join '-'
    return $combinedString




}
function q9($addr) {
	<# Return `$true when the given argument is an IPv4 address
	   within the class 'E' otherwise return `$false. 
       For an IPv4 address to be within class 'E', it
       must fall within the range '240.0.0.0' to
       '254.255.255.255'. 
	#>

  



    $ip = [System.Net.IPAddress]::Parse($addr)
    

    $ipBytes = $ip.GetAddressBytes()
    $startIp = [System.Net.IPAddress]::Parse("240.0.0.0").GetAddressBytes()
    $endIp = [System.Net.IPAddress]::Parse("254.255.255.255").GetAddressBytes()
    
    $inRange = $true
    for ($i = 0; $i -lt $ipBytes.Length; $i++) {
        if ($ipBytes[$i] -lt $startIp[$i] -or $ipBytes[$i] -gt $endIp[$i]) {
            $inRange = $false
            break
        }
    }
    
    return $inRange
}









function q10 () {
    <# Return the current date/time as a string formatted in 
       the following way:
       YearMonthDay@Hour:Minute:Second
       For example, If the current date/time is 5 minutes and 
       2 seconds after 3 PM on February 8th, 2018, the return 
       value should be:  20180208@15:05:02
    #>


    $currentDateTime = Get-Date -Format "yyyyMMdd@HH:mm:ss"
    return $currentDateTime
