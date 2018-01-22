### Liquid Manual Testing -- ARM64: Odroid C2 / Rock64

1. Download the latest [OdroidC2 Liquid image](https://jenkins.liquiddemo.org/job/setup-arm64/job/master/lastSuccessfulBuild/artifact/liquid-odroid_c2-arm64-raw.img.gz) or [Rock64 Liquid image](https://jenkins.liquiddemo.org/job/setup-rock64/job/master/lastStableBuild/artifact/liquid-rock64.img.gz) and write it to the MicroSD card with [Etcher](https://etcher.io/)
2. Insert the card (and one or two wifi dongles for hotspot and connecting to a router)
3. Turn the board on, connect to it with a lan cable and wait 2~4 min (network icon will say connected).

### Welcome Form

4. Go to liquid.example.org and fill out the welcome form with:

    - domain name: test-liquid.org
    - username: administrator
    - password: parola123

    ENTER

5. Post welcome screen: wait ~5+ mins and refresh until it works (you may get a 502 error, keep waiting) -- TODO develop feature to fix this
6. You will be redirected to the login form

### Login Form

7. Login with:

    - username: administrator
    - password: parola123

### ADMIN PANEL

8. Click on "Admin panel" in the pill on the top right
    - See General Status: No information
    - In the future there will be some information -- TODO develop feature

9. Click on Network on the left hand menu
    - First tab: status
    - See Domain: as above
    - See Lan configuration > default for now
    - See Wan configuration > SSID & password: empty

10. Click on the "lan" tab
    - SSID and Password: creates hotspot -- TODO develop feature 
    - IP fields -- no testing for now, -- TODO develop feature

11. Click "wan" 
    - See ssid and password empty
    - See dhcp toggle on

13. Change "wan" settings
    - Set wifi name and password to connect to wireless network
    - Click Update (wait, refresh manually after 2 min)
    - You will also get internet via cable now
    
14. Click "SSH"
    - See that there is no key
    - See that ssh is enabled
    
15. (optional) Configure "SSH"
    - Click add and add your key, click Update
    - Test ssh connection (make sure that it doesn't require a password)

16. Skip VPN for now 

17. Test "Services" login.
    - Click "Apps panel" from top right to swap from "Admin panel".
    - Open each service in a new tab
    - Login with the credentials you added on the welcome screen

18. Test "Services" toggle
    - Click "Admin panel" from top right to swap back.
    - Open hoover.liquid.example.org in a new tab
    - Disable hoover in Services tab
    - Refresh hoover tab
    - Renable hoover service
    - Refresh hoover tab (test login and hoover-admin)
    - Repeat with the rest of apps

19. Create simple "User"
    - Click 'Add user' (user1 / user1pass)
    - Leave Admin toggle off, fill names and click Add

20. Create admin "User"
    - Click 'Add user' (admin2 / admin2pass)
    - Click Admin toggle on, fill names and click Add

21. Edit first administrator account
    - Click Edit
    - Add first and last names
    - Click Update

22. Test second administrator account
    - Logout with top-right exit button
    - Login with admin2 / admin2pass
    - Go to users, edit first admin, remove admin privileges

23. Test first administrator account privileges
    - Logout from admin2
    - Login from administrator
    - Test rights by:
    - Admin top right button should be missing
    - Visit http://liquid.example.org/admin-ui/users
    - Should get redirected to login screen

### Test functionality

24. Test 
