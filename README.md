while ($true) {
    $adapter = Get-NetAdapter -Name "*AX201*" | 
        Select-Object ReceiveLinkSpeed, TransmitLinkSpeed
    $signal = (netsh wlan show interfaces | Select-String "Signal").ToString().Trim()
    Write-Host "$(Get-Date -Format 'HH:mm:ss') | RX: $($adapter.ReceiveLinkSpeed/1000000)Mbps | TX: $($adapter.TransmitLinkSpeed/1000000)Mbps | $signal"
    Start-Sleep -Seconds 2
}
