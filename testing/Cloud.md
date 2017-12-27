### Liquid Manual Testing -- X86 cloud VM

1. download and follow https://github.com/liquidinvestigations/web-ui-deployment-scripts
2. boot the image with ./launch_liquid.sh and wait for it to boot
3. visit liquid.example.org

### Welcome Form

4. fill out form with:

    - domain name: test-liquid.org
    - username: administrator
    - password: parola123
    - hotspot ssid: test-liquid
    - password: parola123

    ENTER

5. welcome screen: wait a minute and refresh until it works -- TODO develop feature to fix this
6. you will be redirected to the login form

### Login Form

7. Login with:

    - username: administrator
    - password: parola123

### ADMIN PANEL

8. Click on "admin" in the pill on the top right
    - See General Status: No information
    - In the future there will be some information -- TODO develop feature

9. Click on Network on the left hand menu
    - First tab: status
    - See Domain: as above
    - See Lan configuration > SSID & password: as above
    - See Wan configuration > SSID & password: empty

10. Click on the "lan" tab
    - See SSID: as above
    - See Password: as above
    - IP fields -- no testing for now, -- TODO develop feature

11. Change password: asdqwer, hit ENTER
    - See: progress bar that says "reconfiguring"
    - See: it dissapears

12. Click "wan" 
    - See ssid and password empty
    - See dhcp toggle on

13. Change "wan" settings
    - Set SSID: hotel-network
    - Set Password: hotel123
    - Click DHCP
    - Click Update 
    
14. Click "SSH"
    - See that there is no key
    - See that ssh is enabled
    
15. Configure "SSH"
    - Click add and add your key, click Update
    - Test ssh connection:
        - run ./ssh.sh 
        - check that it doesn't require a password

16. Click "VPN" tab
    - On Status tab
    - See that server and client state is Disabled.
    - See Enabled & Running is 'no'.
    - See Connection count and Registered keys are '0'.

17. Configure "VPN" Server
    - Click on VPN Server
    - Click generate new key
    - Add 'test1' label and click continue (~1m)
    - Click Download on generated key and save on desktop (overwrite if it exists)
    - Enable vpn server (~1m25s)
        - If the VPN Server is enabled before the key generation, client doesn't connect

18. Setup local Ovpn client
    - Open your openvpn client
    - Import connection with downloaded .ovpn file
    - Connect

19. Test VPN Server
    - Create new key
    - Revoke old key
    - Try to connect with old key (shouldn't work)
    - (set up and) Connect with the new key

20. Test "Services"
    - Open hoover.liquid.example.org in a new tab
    - Disable hoover in Services tab
    - Refresh hoover tab
    - Rnable hoover service
    - Refresh hoover tab (test login and hoover-admin)
    - Repeat with the rest of apps

21. Create simple "User"
    - Click 'Add user' (user1 / user1pass)
    - Leave Admin toggle off, fill names and click Add

22. Create admin "User"
    - Click 'Add user' (admin2 / admin2pass)
    - Click Admin toggle on, fill names and click Add

23. Edit first administrator account
    - Click Edit
    - Add first and last names
    - Click Update

24. Test second administrator account
    - Logout with top-right exit button
    - Login with admin2 / admin2pass
    - Go to users, edit first admin, remove admin privileges

25. Test first administrator account privileges
    - Logout from admin2
    - Login from administrator
    - Test rights by:
    - Admin top right button should be missing
    - Visit http://liquid.example.org/admin-ui/users
    - Should get redirected to login screen

