## Commands/Steps Log

# Open Windows Firewall GUI
1. Press Win+R → `wf.msc` → Enter

# Add block rule for port 23
2. Inbound Rules → New Rule → Port → TCP 23 → Block → Apply all profiles → Name

# Test with PowerShell
3. Test-NetConnection -ComputerName localhost -Port 23

# (Optional) Remove rule after testing
4. Inbound Rules → Locate rule → Delete
