#donuts

1.  A vendor is trying to connect to a server we publicly expose (assume we are not using VPN). When asked for his public IP from which he will be connecting, the vendor provides us with the following IP `192.168.0.100`, what should be our next steps?

    1.  Include questions we may need to ask to get additional information to ensure this vendor will be able to connect over the public internet to our server. __Note that this vendor is not in our LAN, nor on a VPN with us__.

        > Add follow up Questions here as a bulleted list and add an explanation why you ask each question (what do you expect to receive back)

        1.  What method will you be using to connect to our server? RDP, SSH, TelNet, FTP, etc.
            This will help in determining what rule will be set in the firewall for the vendor's access

        1.  Which directory, folder, files will the access be needed?
            A separate account is needed in order to make sure that no confidential data will be leaked or will accidentally be accessed by the vendor unless it is needed for the project that they are doing


    1.  Write a PowerShell command (assume Windows 2012 R2) to add a new firewall rule on a single server, allowing incoming connections on port `3389` for `TCP` protocol __limited to the public IP of the vendor only__ (assuming we have the public IP of the vendor)

    ```powershell
    # netsh advfirewall firewall add rule name="Open Port 3389" dir=in action=allow protocol=TCP localport=3389

    ```

1.  How do you list all Computers in an Active Directory Domain using Powershell (output DNSHostname in a table format, no need for `filters` or `SearchBase`)

    ```powershell
    # get-adcomputer -filter * | format-table DNSHostname

    ```

1.  What could possible troubleshoot tests be for the following output on a macOS machine.

    For each step, mention what would be your next step

    ```bash
    $ ping microsoft.com
    PING microsoft.com (23.100.122.175): 56 data bytes
    Request timeout for icmp_seq 0
    Request timeout for icmp_seq 1
    ...
    ```

    Notes:

    -   Local machines in the same network can still be pinged by IP

    # Check DNS under Settings > Network and select which type of connection is used > Advanced > DNS
    # Check that microsoft.com is not in the Host file
    # Run a traceroute to check where the connection stops on a macOS machine
    # Clear the DNS cache
    # Another possible reason is if macbook has a software firewall/antivirus installed and configuration may have been set to not allow acces to microsoft.com or any website.
    # Possible virus might have infected the machine thus preventing access
