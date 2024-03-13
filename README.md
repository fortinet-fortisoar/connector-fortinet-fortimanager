<h2>About the connector</h2>

<p>Fortinet FortiManager provides easy centralized configuration, policy-based provisioning, update management, and end-to-end network monitoring for your Fortinet-installed environment.</p>

<p>This document provides information about the Fortinet FortiManager Connector, which facilitates automated interactions with your Fortinet FortiManager server using FortiSOAR&trade; playbooks. Add the Fortinet FortiManager connector, as a step in FortiSOAR&trade; playbooks and perform automated operations such as retrieving a list of all devices configured on the Fortinet FortiManager server, creating and updating incidents on the Fortinet FortiManager server, and retrieving a list of all incidents from the Fortinet FortiManager server.</p>

<p>You can use FortiSOAR&trade;'s Data Ingestion Wizard to easily ingest data into FortiSOAR&trade; by pulling incidents from Fortinet FortiManager. For more information, see the <a href="#dataIngestion">Data Ingestion Support</a> topic.</p>

<h3>Version information</h3>

<p>Connector Version: 4.0.0</p>

<p>FortiSOAR&trade; Version Tested on: 7.4.3-3294</p>

<p>Fortinet FortiManager Version Tested on: FortiManager VM64-KVM-V7.2.2 build6198</p>

<p>Authored By: Fortinet</p>

<p>Certified: Yes</p>

<h3>Release Notes for version 4.0.0</h3>

<p>The following changes have been made to the Fortinet FortiManager Connector in version 4.0.0:</p>

<ul>
    <li>Added a new config parameter named <strong>Workspace Mode Enabled</strong> to identify whether the workspace mode is enabled or disabled on FortiManager.</li>
    <li>Added a new parameter named <strong><em>NGFW Mode</em></strong> in the following actions:
        <ul>
            <li>List ADOM Firewall Policies</li>
            <li>Create Firewall Policy</li>
            <li>Update Firewall policy</li>
            <li>Delete Firewall policy</li>
            <li>Move Firewall Policy</li>
            <li>ADOM Level Block IP Address</li>
            <li>ADOM Level Unblock IP Address</li>
        </ul>
    <li>Made the parameter <em>NGFW Mode</em> input mandatory in the <strong>Update Policy Package</strong> action.</li>
    <li>Updated the output schema of the following actions:
        <ul>
            <li>Get Installation Policy Package Status</li>
            <li>Get User Groups List</li>
        </ul>
    </li>
    <ul>
        <li>Renamed the parameter <em><code>Firewall Policy Name</code></em> to <strong><code>Firewall/Security Policy Name</code></strong> in the action <strong><em>List ADOM Firewall Policies</em></strong>.</li>
    </ul>
    <li>Moved the parameters <strong><code>Inspection Mode</code></strong> and <strong><code>Schedule Timeout</code></strong> under <em><code>NGFW Mode</code></em> for following actions:
        <ul>
            <li>Create Firewall Policy</li>
            <li>Update Firewall Policy</li>
        </ul>
    </li>
</ul>

<h2>Installing the connector</h2>

<p>Use the <strong>Connector Store</strong> to install the connector. For the detailed procedure to install a connector, click <a href="https://docs.fortinet.com/document/fortisoar/0.0.0/installing-a-connector/1/installing-a-connector" target="_blank">here</a>.</p>

<p>You can also use the following yum command as a <code>root</code> user to install connectors from an SSH session:</p>

<pre>yum install cyops-connector-fortinet-fortimanager</pre>

<h2>Prerequisites to configuring the connector</h2>

<ul>
    <li>You must have the IP address or hostname of the Fortinet FortiManager server to which you will connect and perform automated operations and credentials (username-password pair) to access that server.</li>
    <li>You must enable <em>FortiAnalyzer Features</em> in FortiManager to perform the following operations:
        <ul>
            <li>Create Incident</li>
            <li>List Incident</li>
            <li>Get Events Related to Incident</li>
            <li>Get Events</li>
            <li>Get Events Details</li>
            <li>Update Incident</li>
        </ul>
    </li>
    <li>You must enable the <em>Administrative Domain</em> features in FortiManager.</li>
    <li>The FortiSOAR&trade; server should have outbound connectivity to port 443 on the Fortinet FortiManager server.</li>
    <li>You must add the configurations required to block or unblock IP addresses, URLs, or applications in Fortinet FortiManager. For more information, see the <a href="#blockUnblockIPAdd">Blocking or Unblocking IP addresses, URLs, or applications in Fortinet FortiManager</a> section.</li>









</ul>

<h2>Minimum Permissions Required</h2>

<p>The minimum privileges that require to be assigned to users who are going to use this connector and run actions on Fortinet FortiManager are:</p>

<ul>
    <li>Admin Profile - Super User</li>
    <li>JSON API Access - Read & Write</li>
</ul>

<h2>Configuring the connector</h2>

<p>For the procedure to configure a connector, click <a href="https://docs.fortinet.com/document/fortisoar/0.0.0/configuring-a-connector/1/configuring-a-connector" rel="noreferrer noopener" target="_blank">here</a>.</p>

<h3>Configuration parameters</h3>

<p>In FortiSOAR&trade;, on the Connectors page, click the <strong>Fortinet FortiManager</strong> connector row (if you are in the <strong>Grid</strong> view on the Connectors page), and in the <strong>Configurations</strong> tab enter the required configuration details.</p>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Hostname</td>
            <td>IP address or Hostname of the Fortinet FortiManager endpoint server to which you will connect and perform the automated operations.</td>
        </tr>
        <tr>
            <td>Username</td>
            <td>Username to access the Fortinet FortiManager server to which you will connect and perform the automated operations.</td>
        </tr>
        <tr>
            <td>Password</td>
            <td>Password to access the Fortinet FortiManager server to which you will connect and perform the automated operations.</td>
        </tr>
        <tr>
            <td>ADOM</td>
            <td>Administrative domain names (ADOMs) of the Fortinet FortiManager server to which you will connect and perform the automated operations. Enter the ADOMs in the CSV or List format.</td>
        </tr>
        <tr>
            <td>Port</td>
            <td>Port number used to access the Fortinet FortiManager server to which you will connect and perform the automated operations. By default, this is set to 443.</td>
        </tr>
        <tr>
            <td>Workspace Mode Enabled</td>
            <td>Specifies whether the Workspace(ALL ADOMs) mode is enabled. By default, this option is set to <code>False</code>.</td>
        </tr>
        <tr>
            <td>Verify SSL</td>
            <td>Specifies whether the SSL certificate for the server is to be verified.<br />
                By default, this option is set to <code>True</code>.</td>
        </tr>
    </tbody>
</table>

<h2>Actions supported by the connector</h2>

<p>The following automated operations can be included in playbooks and you can also use the annotations to access operations:</p>

<table border="1">
    <thead>
        <tr>
            <th>Function</th>
            <th>Description</th>
            <th>Annotation and Category</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Create Incident</td>
            <td>Creates an incident in Fortinet FortiManager based on the reporter name, endpoint name, and other input parameters you have specified.</td>
            <td>create_incident<br />
                Investigation</td>
        </tr>
        <tr>
            <td>List Incident</td>
            <td>Retrieves a list of all incidents or a specific incident from Fortinet FortiManager based on the search parameters you have specified.</td>
            <td>get_incidents<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Get Events Related to Incident</td>
            <td>Retrieves details of events associated with a Fortinet FortiManager incident, based on the incident ID and other input parameters you have specified.</td>
            <td>get_incident_events<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Get Device List</td>
            <td>Retrieves a list of devices from Fortinet FortiManager based on the search parameters you have specified.
                <p><strong>NOTE</strong>: If a parameter is left blank or null, then this operation will return devices matching all values.</p>
            </td>
            <td>get_devices<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Get Events</td>
            <td>Retrieves a list of events from Fortinet FortiManager based on the search parameters you have specified.
                <p><strong>Note</strong>: If a parameter is left blank or null, then this operation will return events matching all values.</p>
            </td>
            <td>get_alert_event<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Get Event Details</td>
            <td>Retrieves a list of event details (logs) from Fortinet FortiManager based on the alert IDs and other search parameters you have specified.</td>
            <td>get_alert_logs<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Update Incident</td>
            <td>Update an incident in Fortinet FortiManager based on the incident ID and other input parameters you have specified.</td>
            <td>update_incident<br />
                Investigation</td>
        </tr>
        <tr>
            <td>List ADOM Policy Package</td>
            <td>Retrieves a list of all ADOM policy packages or a specific ADOM policy package from Fortinet FortiManager based on the search parameters you have specified.</td>
            <td>get_adom_policy_package<br />
                Investigation</td>
        </tr>
        <tr>
            <td>List ADOM Firewall Policies</td>
            <td>Retrieves a list of all ADOM firewall policies or a specific ADOM firewall policy from Fortinet FortiManager based on the search parameters you have specified.</td>
            <td>get_adom_policy<br />
                Investigation</td>
        </tr>
        <tr>
            <td>ADOM Level Get Blocked IP Addresses</td>
            <td>Retrieves a list of ADOM-level IP Addresses that are blocked on Fortinet FortiGate through Fortinet FortiManager based on the firewall policy, address group name, and other input parameters you have specified.</td>
            <td>get_blocked_ip<br />
                Investigation</td>
        </tr>
        <tr>
            <td>ADOM Level Block IP Address</td>
            <td>Blocks IP addresses at the ADOM level on Fortinet FortiGate based on the Firewall policy, address group name, and other input parameters you have specified.</td>
            <td>block_ip<br />
                Containment</td>
        </tr>
        <tr>
            <td>ADOM Level Unblock IP Address</td>
            <td>Unlocks IP addresses at the ADOM level on Fortinet FortiGate based on the Firewall policy, address group name, and other input parameters you have specified.</td>
            <td>unblock_ip<br />
                Remediation</td>
        </tr>
        <tr>
            <td>Re-install Policy</td>
            <td>Reinstalls a Firewall Policy in Fortinet FortiManager based on the ADOM Name and policy package name you have specified.</td>
            <td>reinstall_policy<br />
                Investigation</td>
        </tr>
        <tr>
            <td>List Global Policy Package</td>
            <td>Retrieves a list of all policy packages or a specific policy package from Fortinet FortiManager based on the search parameters you have specified.</td>
            <td>get_global_policy_package<br />
                Investigation</td>
        </tr>
        <tr>
            <td>List Global Firewall Policies</td>
            <td>Retrieves a list of all global firewall policies or a specific firewall policy from Fortinet FortiManager based on the search parameters you have specified.</td>
            <td>get_global_policy<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Global Level Get Blocked IP Addresses</td>
            <td>Retrieves a list of Global (header/footer policy) level IP Addresses that are blocked on Fortinet FortiGate through Fortinet FortiManager based on the firewall policy, address group name, and other input parameters you have specified.</td>
            <td>get_blocked_ip<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Global Level Block IP Address</td>
            <td>Blocks IP addresses at the global level on Fortinet FortiGate based on the firewall header/footer policy, address group name, and other input parameters you have specified.</td>
            <td>block_ip<br />
                Containment</td>
        </tr>
        <tr>
            <td>Global Level Unblock IP Address</td>
            <td>Unblocks IP addresses at the global level on Fortinet FortiGate based on the firewall header/footer policy, address group name, and other input parameters you have specified.</td>
            <td>unblock_ip<br />
                Remediation</td>
        </tr>
        <tr>
            <td>Assign Global Policy Package</td>
            <td>Assigns a global policy package to ADOM packages in Fortinet FortiManager based on the policy package name, ADOM devices, and other input parameters you have specified.</td>
            <td>global_assign_policy<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Get Device Groups List</td>
            <td>Retrieves a list of all device groups or a specific device group from Fortinet FortiManager based on the level type and other search parameters you have specified.</td>
            <td>get_device_groups<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Create Address</td>
            <td>Creates an address in Fortinet FortiManager based on the address name, level type, and other input parameters you have specified.</td>
            <td>create_address<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Get Addresses List</td>
            <td>Retrieves a list of addresses or a specific address from Fortinet FortiManager based on the level type and other search parameters you have specified.</td>
            <td>get_addresses<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Update Address</td>
            <td>Updates an address in Fortinet FortiManager based on the address name, level type, and other input parameters you have specified.</td>
            <td>update_address<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Delete Address</td>
            <td>Deletes an address from Fortinet FortiManager based on the level type you have specified.</td>
            <td>delete_address<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Create Address Group</td>
            <td>Creates an address group in Fortinet FortiManager based on the address name, level type, and other input parameters you have specified.</td>
            <td>create_address_group<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Get Address Groups List</td>
            <td>Retrieves a list of address groups or a specific address group from Fortinet FortiManager based on the level type and other search parameters you have specified.</td>
            <td>get_address_groups<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Update Address Group</td>
            <td>Updates an existing address group in Fortinet FortiManager based on the level type, method, and other input parameters you have specified.</td>
            <td>update_address_group<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Delete Address Group</td>
            <td>Deletes an address group from Fortinet FortiManager based on the level type you have specified.</td>
            <td>delete_address_group<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Get Service Categories List</td>
            <td>Retrieves a list of service categories or a specific service category from Fortinet FortiManager based on the level type and other search parameters you have specified.</td>
            <td>get_service_categories<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Create Service Group</td>
            <td>Creates a service group in Fortinet FortiManager based on the level type, members, and other input parameters you have specified.</td>
            <td>create_service_group<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Get Service Groups List</td>
            <td>Retrieves a list of service groups or a specific service group from Fortinet FortiManager based on the level type and other search parameters you have specified.</td>
            <td>get_service_group<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Update Service Group</td>
            <td>Updates an existing service group in Fortinet FortiManager based on the level type, method, and other input parameters you have specified.</td>
            <td>update_service_group<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Delete Service Group</td>
            <td>Deletes a service group from Fortinet FortiManager based on the level type you have specified.</td>
            <td>delete_service_group<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Create Custom Service</td>
            <td>Creates a custom service in Fortinet FortiManager based on the level type and other input parameters you have specified.</td>
            <td>create_custom_service<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Get Custom Services List</td>
            <td>Retrieves a list of custom services or a specific custom service from Fortinet FortiManager based on the level type and other search parameters you have specified.</td>
            <td>get_custom_service<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Update Custom Service</td>
            <td>Updates an existing custom service in Fortinet FortiManager based on the level type and other input parameters you have specified.</td>
            <td>update_custom_service<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Delete Custom Service</td>
            <td>Deletes a custom service from Fortinet FortiManager based on the level type you have specified.</td>
            <td>delete_custom_service<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Create Policy Package</td>
            <td>Creates a policy package in Fortinet FortiManager based on the level type, package type, and other input parameters you have specified.</td>
            <td>create_policy_package<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Update Policy Package</td>
            <td>Updates a policy package in Fortinet FortiManager based on the level type and other input parameters you have specified.</td>
            <td>update_policy_package<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Delete Policy Package</td>
            <td>Deletes a policy package from Fortinet FortiManager based on the level type and other input parameters you have specified.</td>
            <td>delete_policy_package<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Create Firewall Policy</td>
            <td>Creates a firewall policy in Fortinet FortiManager based on the level type, package type, policy package name, and other input parameters you have specified.</td>
            <td>create_policy<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Update Firewall Policy</td>
            <td>Updates a firewall policy in Fortinet FortiManager based on the level type, package type, policy package name, and other input parameters you have specified.</td>
            <td>update_policy<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Delete Firewall Policy</td>
            <td>Deletes a firewall policy in Fortinet FortiManager based on the level type, policy ID, policy package name, and other input parameters you have specified.</td>
            <td>delete_policy<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Move Firewall Policy</td>
            <td>Moves a firewall policy in Fortinet FortiManager based on the level type, policy ID, policy package name, target, and other input parameters you have specified.</td>
            <td>move_policy<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Get Dynamic Interface List</td>
            <td>Retrieves a list of all dynamic interfaces or a specific dynamic interface from Fortinet FortiManager based on the level type and other search parameters you have specified.</td>
            <td>get_dynamic_interface<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Install Policy</td>
            <td>Installs a policy package on Fortinet FortiManager based on the ADOM, policy package name, and other input parameters you have specified.</td>
            <td>install_policy<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Get Installation Policy Package Status</td>
            <td>Retrieves the status of installation for a specific policy package from Fortinet FortiManager based on the task ID you have specified.</td>
            <td>install_policy_status<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Create LDAP Server</td>
            <td>Creates an LDAP server in Fortinet FortiManager based on the level type, LDAP server name, username, password, and other input parameters you have specified.</td>
            <td>create_ldap_server<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Get LDAP Server List</td>
            <td>Retrieves a list of LDAP servers or a specific LDAP server from Fortinet FortiManager based on the level type and other search parameters you have specified.</td>
            <td>get_ldap_server<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Update LDAP Server</td>
            <td>Updates an LDAP server in Fortinet FortiManager based on the level type, LDAP server name, and other input parameters you have specified.</td>
            <td>update_ldap_server<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Delete LDAP Server</td>
            <td>Deletes an LDAP server from Fortinet FortiManager based on the level type, LDAP server name, and other input parameters you have specified.</td>
            <td>delete_ldap_server<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Create User Group</td>
            <td>Creates a user group in Fortinet FortiManager based on the level type, group name, members list, and other input parameters you have specified.</td>
            <td>create_user_group<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Get User Groups List</td>
            <td>Retrieves a list of all user groups or a specific user group from Fortinet FortiManager based on the level type and other search parameters you have specified.</td>
            <td>get_user_group<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Update User Group</td>
            <td>Updates a user group in Fortinet FortiManager based on the level type, group name, change in the members' list, and other input parameters you have specified.</td>
            <td>update_user_group<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Delete User Group</td>
            <td>Deletes a user group from Fortinet FortiManager based on the level type, group name, and other input parameters you have specified.</td>
            <td>delete_user_group<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Get SSL VPN Settings</td>
            <td>Retrieves SSL VPN settings from Fortinet FortiManager based on the device name, VDOM, and other search parameters you have specified.</td>
            <td>get_ssl_vpn<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Update SSL VPN Settings</td>
            <td>Updates an SSL VPN settings in Fortinet FortiManager based on the device name, VDOM, and input search parameters you have specified.</td>
            <td>update_ssl_vpn<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Get Web Filter List</td>
            <td>Retrieves a list of web filters from Fortinet FortiManager based on the level type and other search parameters you have specified.</td>
            <td>get_web_filter<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Get Blocked URLs</td>
            <td>Retrieves a list of URLs that are blocked on Fortinet FortiManager based on the specified web filter profile name, level type, and other search parameters you have specified.</td>
            <td>get_blocked_urls<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Block URL</td>
            <td>Blocks URLs on Fortinet FortiManager using the Web Filter Profile Name you have specified.</td>
            <td>block_url<br />
                Containment</td>
        </tr>
        <tr>
            <td>Unblock URL</td>
            <td>Unblocks URLs on Fortinet FortiManager using the Web Filter Profile Name you have specified.</td>
            <td>unblock_url<br />
                Remediation</td>
        </tr>
        <tr>
            <td>Get Applications Detail</td>
            <td>Retrieves a list of all application names and associated details from the Fortinet FortiManager server.</td>
            <td>get_app_details<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Get Applications Control List</td>
            <td>Retrieves a list of control profiles from Fortinet FortiManager based on the level type and other search parameters you have specified.</td>
            <td>get_application_control_list<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Get Blocked Applications</td>
            <td>Retrieves a list of application names that are blocked on Fortinet FortiManager based on the specified application control name, level type, and other search parameters you have specified.</td>
            <td>get_blocked_app<br />
                Investigation</td>
        </tr>
        <tr>
            <td>Block Application</td>
            <td>Blocks applications on Fortinet FortiManager using the Application Control Profile Name you have specified.</td>
            <td>block_application<br />
                Containment</td>
        </tr>
        <tr>
            <td>Unblock Application</td>
            <td>Unblocks applications on Fortinet FortiManager using the Application Control Profile Name you have specified.</td>
            <td>unblock_applications<br />
                Remediation</td>
        </tr>
    </tbody>
</table>

<h3>operation: Create Incident</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>ADOM</td>
            <td>(Optional) Specify the administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified in the <strong>Connector Configuration</strong> as a configuration parameter.</td>
        </tr>
        <tr>
            <td>Reporter</td>
            <td>Specify the name of the reporter of the incident that you want to create in Fortinet FortiManager. For example, admin.</td>
        </tr>
        <tr>
            <td>Endpoint Name</td>
            <td>Specify the details of the endpoint affected by the incident that you want to create in Fortinet FortiManager. For example, <code>11.XXX.YY.Z/32 (11.XXX.YY.Z) or 11.XXX.YY.Z/32 (Emp1 Laptop).</code></td>
        </tr>
        <tr>
            <td>Endpoint ID</td>
            <td>(Optional) Specify the endpoint ID that you want to assign to the incident you want to create in Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>End User ID</td>
            <td>(Optional) Specify the end-user ID that you want to assign to the incident you want to create in Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Category</td>
            <td>(Optional) Select the category you want to assign to the incident you want to create in Fortinet FortiManager. You can select from the following options:
                <ul>
                    <li>Unauthorized access</li>
                    <li>Denial of Service</li>
                    <li>Malicious Code</li>
                    <li>Improper Usage</li>
                    <li>Scans/Probes/Attempted Access</li>
                    <li>Uncategorized</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Severity</td>
            <td>(Optional) Select the severity level you want to assign to the incident you want to create in Fortinet FortiManager. You can select from the following options:
                <ul>
                    <li>High</li>
                    <li>Medium</li>
                    <li>Low</li>
                </ul>
                </td>
        </tr>
        <tr>
            <td>Status</td>
            <td>(Optional) Select the status you want to assign to the incident you want to create in Fortinet FortiManager. You can select from the following options:
                <ul>
                    <li>New</li>
                    <li>Analysis</li>
                    <li>Response</li>
                    <li>Closed: Remediated</li>
                    <li>Closed: False Positive</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Description</td>
            <td>(Optional) Specify the description of the new incident that you want to create in Fortinet FortiManager.</td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "jsonrpc": "",
    "id": "",
    "result": {
        "incid": ""
    }
}</pre>

<h3>operation: List Incident</h3>

<h4>Input parameters</h4>

<p><strong>NOTE</strong>: All the input parameters are optional. However, if you do not specify any parameter, then no filter criterion is applied, and an unfiltered list is returned.</p>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>ADOM</td>
            <td>Specify the administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified in the <strong>Connector Configuration</strong> as a configuration parameter.</td>
        </tr>
        <tr>
            <td>Incident ID</td>
            <td>Specify the ID of incidents in CSV or list format to retrieve from Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Detail Level</td>
            <td>Select the level of detail of the incidents to retrieve from Fortinet FortiManager. You can select from following options:
                <ul>
                    <li>Basic</li>
                    <li>Standard</li>
                    <li>Extended</li>
                </ul>
                By default, this is set to <strong>Standard</strong>.
            </td>
        </tr>
        <tr>
            <td>Filter</td>
            <td>Specify the query using which to filter incidents being retrieved from Fortinet FortiManager. The query is in the format:
                <pre>field_name=&quot;field_value&quot;</pre>
                For example:
                <pre>category=&quot;CAT2&quot; and severity=&quot;medium&quot;</pre>
            </td>
        </tr>
        <tr>
            <td>Sort By</td>
            <td>Select <em>Field</em> as the sorting criteria to order the results and specify values in the following fields:
                <ul>
                    <li><strong>Field</strong>: Specify the name of the field on which to sort the results. For example: severity or category.</li>
                    <li><strong>Order</strong>: Select the order in which to sort the results. You can select from following options:
                        <ul>
                            <li>Ascending (default)</li>
                            <li>Descending</li>
                        </ul>
                    </li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Limit</td>
            <td>Specify the maximum number of records that this operation should return. Values supported are:
            <ul>
                <li><strong>Default:<code>&quot;50&quot;</code></strong></li>
                <li><strong>Minimum:<code>&quot;1&quot;</code></strong></li>
                <li><strong>Maximum:<code>&quot;2000&quot;</code></strong></li>
            </ul>
        </td>
        </tr>
        <tr>
            <td>Offset</td>
            <td>(Optional) Specify the offset value to retrieve a subset of records that starts from the offset value. The offset works with the <em>Limit</em> parameter, which determines how many records to retrieve starting from the offset. Values supported are:
                <ul>
                    <li><strong>Default:<code>&quot;0&quot;</code></strong></li>
                    <li><strong>Minimum:<code>&quot;0&quot;</code></strong></li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<p>Output schema when you select <em>Detail Level</em> as <em><strong>Basic</strong></em>:</p>

<pre>{ 
    "jsonrpc": "", 
    "id": "", 
    "result": { 
        "status": { 
            "code": "", 
            "message": "" 
        }, 
        "detail-level": "", 
        "data": [ 
            { 
                "attach_revision": "", 
                "attach_lastupdate": "", 
                "lastupdate": "", 
                "revision": "", 
                "incid": "" 
            } 
        ] 
    } 
}</pre>

<p>Output schema when you select <em>Detail Level</em> as <em><strong>Extended</strong></em>:</p>

<pre>{
    "result": {
        "data": [
            {
                "endpoint": "",
                "euname": "",
                "epip": "",
                "status": "",
                "incid": "",
                "attachments": [
                    {
                        "lastupdate": "",
                        "attachid": "",
                        "revision": ""
                    }
                ],
                "lastupdate": "",
                "osversion": "",
                "attach_lastupdate": "",
                "euid": "",
                "category": "",
                "epid": "",
                "epname": "",
                "revision": "",
                "reporter": "",
                "createtime": "",
                "description": "",
                "osname": "",
                "mac": "",
                "lastuser": "",
                "severity": "",
                "attach_revision": "",
                "refinfo": ""
            }
        ],
        "detail-level": "",
        "status": {
            "message": "",
            "code": ""
        }
    },
    "id": "",
    "jsonrpc": ""
}</pre>

<p>This is the default output schema:</p>

<pre>{
    "result": {
        "data": [
            {
                "endpoint": "",
                "reporter": "",
                "createtime": "",
                "description": "",
                "status": "",
                "incid": "",
                "severity": "",
                "lastuser": "",
                "attach_lastupdate": "",
                "lastupdate": "",
                "euid": "",
                "attach_revision": "",
                "category": "",
                "refinfo": "",
                "epid": "",
                "revision": ""
            }
        ],
        "detail-level": "",
        "status": {
            "message": "",
            "code": ""
        }
    },
    "id": "",
    "jsonrpc": ""
}</pre>

<h3>operation: Get Events Related to Incident</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>ADOM</td>
            <td>(Optional) Specify the administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified in the <strong>Connector Configuration</strong> as a configuration parameter.</td>
        </tr>
        <tr>
            <td>Incident ID</td>
            <td>Specify the ID of the incident whose associated events you want to retrieve from Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Attachment Type</td>
            <td>Specify the attachment types that you want to search for in Fortinet FortiManager. Valid types include:
                <ul>
                    <li>Alert Event</li>
                    <li>Log</li>
                    <li>Comment</li>
                    <li>Log Search Filter</li>
                    <li>Upload File</li>
                    <li>Report</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Limit</td>
            <td>Specify the maximum number of records that this operation should return. Values supported are:
                <ul>
                    <li><strong>Default:<code>&quot;50&quot;</code></strong></li>
                    <li><strong>Minimum:<code>&quot;1&quot;</code></strong></li>
                    <li><strong>Maximum:<code>&quot;2000&quot;</code></strong></li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Offset</td>
            <td>(Optional) Specify the offset value to retrieve a subset of records that starts from the offset value. The offset works with the <em>Limit</em> parameter, which determines how many records to retrieve starting from the offset. Values supported are:
                <ul>
                    <li><strong>Default:<code>&quot;0&quot;</code></strong></li>
                    <li><strong>Minimum:<code>&quot;0&quot;</code></strong></li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "result": {
        "data": [
            {
                "attachtype": "",
                "lastupdate": "",
                "incid": "",
                "attachid": "",
                "createtime": "",
                "data": "",
                "lastuser": "",
                "revision": ""
            }
        ],
        "status": {
            "message": "",
            "code": ""
        }
    },
    "id": "",
    "jsonrpc": ""
}</pre>

<h3>operation: Get Device List</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>ADOM</td>
            <td>(Optional) Specify the administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified in the <strong>Connector Configuration</strong> as a configuration parameter.</td>
        </tr>
        <tr>
            <td>Device Name</td>
            <td>Specify the valid device name based on which you want to retrieve details of devices from Fortinet FortiManager.<br />
                <strong>NOTE</strong>: If a parameter is left blank or <code>null</code>, this operation returns devices matching all values.
            </td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "url": "",
            "status": {
                "code": "",
                "message": ""
            },
            "data": [
                {
                    "os_ver": "",
                    "build": "",
                    "ips_ext": "",
                    "foslic_inst_time": "",
                    "mgmt.__data[5]": "",
                    "lic_region": "",
                    "latitude": "",
                    "foslic_ram": "",
                    "faz.perm": "",
                    "branch_pt": "",
                    "ips_ver": "",
                    "foslic_utm": "",
                    "source": "",
                    "foslic_cpu": "",
                    "mgmt.__data[3]": "",
                    "mgmt.__data[2]": "",
                    "ha_mode": "",
                    "opts": "",
                    "last_resync": "",
                    "foslic_last_sync": "",
                    "conn_status": "",
                    "mgmt.__data[7]": "",
                    "patch": "",
                    "hw_rev_minor": "",
                    "mgmt.__data[1]": "",
                    "psk": "",
                    "checksum": "",
                    "faz.quota": "",
                    "ha_group_id": "",
                    "adm_usr": "",
                    "ha_group_name": "",
                    "faz.used": "",
                    "tunnel_cookie": "",
                    "conf_status": "",
                    "mgmt.__data[6]": "",
                    "last_checked": "",
                    "version": "",
                    "mgmt.__data[0]": "",
                    "ha_slave": "",
                    "name": "",
                    "longitude": "",
                    "platform_str": "",
                    "foslic_dr_site": "",
                    "tunnel_ip": "",
                    "oid": "",
                    "foslic_type": "",
                    "prefer_img_ver": "",
                    "location_from": "",
                    "vm_cpu_limit": "",
                    "mgmt_if": "",
                    "faz.full_act": "",
                    "av_ver": "",
                    "fex_cnt": "",
                    "fsw_cnt": "",
                    "mgmt.__data[4]": "",
                    "vm_mem": "",
                    "sn": "",
                    "logdisk_size": "",
                    "lic_flags": "",
                    "hostname": "",
                    "vm_mem_limit": "",
                    "vdom": [
                        {
                            "tab_status": "",
                            "opmode": "",
                            "name": "",
                            "devid": "",
                            "rtm_prof_id": "",
                            "status": "",
                            "comments": "",
                            "oid": "",
                            "ext_flags": "",
                            "node_flags": "",
                            "vpn_id": "",
                            "flags": ""
                        }
                    ],
                    "tab_status": "",
                    "adm_pass": [],
                    "mgmt_id": "",
                    "beta": "",
                    "dev_status": "",
                    "os_type": "",
                    "vm_lic_expire": "",
                    "mgmt_mode": "",
                    "hdisk_size": "",
                    "ip": "",
                    "vm_status": "",
                    "db_status": "",
                    "mr": "",
                    "module_sn": "",
                    "hw_rev_major": "",
                    "flags": "",
                    "desc": "",
                    "app_ver": "",
                    "maxvdom": "",
                    "vm_cpu": "",
                    "conn_mode": "",
                    "node_flags": "",
                    "fap_cnt": "",
                    "mgt_vdom": ""
                }
            ]
        }
    ]
}</pre>

<h3>operation: Get Events</h3>

<h4>Input parameters</h4>

<p><strong>Note</strong>: All the input parameters are optional. However, if you do not specify any parameter, then no filter criterion is applied, and an unfiltered list is returned.</p>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>ADOM</td>
            <td>Specify the administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified in the <strong>Connector Configuration</strong> as a configuration parameter.</td>
        </tr>
        <tr>
            <td>Filter</td>
            <td>Specify the filter expression using which you want to retrieve events from Fortinet FortiManager.
                <p><code>'event_value', 'severity', 'triggername', 'count', 'comment' and 'flags'</code> are supported.</p>
                <p>For example, <code>triggername='Local Device Event' and severity&gt;=3 or subject='desc:User login from SSH failed'</code></p>
            </td>
        </tr>
        <tr>
            <td>Time Range</td>
            <td>Select to specify the time range for which you want to retrieve events from Fortinet FortiManager.
                <ul>
                    <li><strong>Start Time</strong>: Specify the start date and time from when you want to retrieve events from Fortinet FortiManager.<br />
                        Consider the timezone as Fortinet FortiAnalyzer's timezone, if the timezone info is not specified.<br />
                        Format: 'yyyy-MM-dd'T'HH:mm:ssZ' (RFC 3339) e.g. '2016-10-17T20:45:37-07:00 or 'yyyy-MM-dd HH:mm:ss' e.g. '2016-10-17 20:45:37'</li>
                    <li><strong>End Time</strong>: Ending DateTime till when you want to retrieve events from Fortinet FortiManager.<br />
                        Consider the timezone as Fortinet FortiAnalyzer's timezone, if the timezone info is not specified.<br />
                        Format: 'yyyy-MM-dd'T'HH:mm:ssZ' (RFC 3339) e.g. '2016-10-17T20:45:37-07:00 or 'yyyy-MM-dd HH:mm:ss' e.g. '2016-10-17 20:45:37'</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Limit</td>
            <td>Specify the maximum number of records that this operation should return. Values supported are:
                <ul>
                    <li><strong>Default:<code>&quot;50&quot;</code></strong></li>
                    <li><strong>Minimum:<code>&quot;1&quot;</code></strong></li>
                    <li><strong>Maximum:<code>&quot;2000&quot;</code></strong></li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Offset</td>
            <td>(Optional) Specify the offset value to retrieve a subset of records that starts from the offset value. The offset works with the <em>Limit</em> parameter, which determines how many records to retrieve starting from the offset. Values supported are:
                <ul>
                    <li><strong>Default:<code>&quot;0&quot;</code></strong></li>
                    <li><strong>Minimum:<code>&quot;0&quot;</code></strong></li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "jsonrpc": "",
    "result": {
        "data": [
            {
                "alerttime": "",
                "triggername": "",
                "devname": "",
                "vdom": "",
                "filterid": "",
                "filterkey": "",
                "devtype": "",
                "eventtype": "",
                "groupby1": "",
                "euid": "",
                "subject": "",
                "devid": "",
                "alertid": "",
                "extrainfo": "",
                "euname": "",
                "epname": "",
                "ackflag": "",
                "logcount": "",
                "filtercksum": "",
                "tag": "",
                "updatetime": "",
                "epid": "1",
                "severity": "",
                "readflag": "",
                "lastlogtime": "",
                "firstlogtime": ""
            }
        ]
    },
    "id": ""
}</pre>

<h3>operation: Get Event Details</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>ADOM</td>
            <td>(Optional) Specify the administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified in the <strong>Connector Configuration</strong> as a configuration parameter.</td>
        </tr>
        <tr>
            <td>Alert ID</td>
            <td>Specify the ID of alerts in CSV or list format whose event details (logs) you want to retrieve from Fortinet FortiManager.<br />
                <strong>Note</strong>: You can find the &quot;Alert IDs&quot; using the &quot;Get Events&quot; action.
            </td>
        </tr>
        <tr>
            <td>Time Order</td>
            <td>Select the order in which you want to sort the result. You can select between <strong>Ascending</strong> or <strong>Descending</strong>. By default, this is set to <strong>Descending</strong>.</td>
        </tr>
        <tr>
            <td>Limit</td>
            <td>Specify the maximum number of records that this operation should return. Values supported are:
                <ul>
                    <li><strong>Default:<code>&quot;50&quot;</code></strong></li>
                    <li><strong>Minimum:<code>&quot;1&quot;</code></strong></li>
                    <li><strong>Maximum:<code>&quot;2000&quot;</code></strong></li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Offset</td>
            <td>(Optional) Specify the offset value to retrieve a subset of records that starts from the offset value. The offset works with the <em>Limit</em> parameter, which determines how many records to retrieve starting from the offset. Values supported are:
                <ul>
                    <li><strong>Default:<code>&quot;0&quot;</code></strong></li>
                    <li><strong>Minimum:<code>&quot;0&quot;</code></strong></li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": {
        "data": [
            {
                "log_id": "",
                "devname": "",
                "userfrom": "",
                "time": "",
                "dstepid": "",
                "desc": "",
                "user": "",
                "dtime": "",
                "msg": "",
                "type": "",
                "devid": "",
                "dsteuid": "",
                "euid": "",
                "date": "",
                "idseq": "",
                "itime_t": "",
                "epid": "",
                "subtype": "",
                "level": "",
                "itime": ""
            }
        ]
    },
    "jsonrpc": ""
}</pre>

<h3>operation: Update Incident</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>ADOM</td>
            <td>(Optional) Specify the administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified in the <strong>Connector Configuration</strong> as a configuration parameter.</td>
        </tr>
        <tr>
            <td>Incident ID</td>
            <td>Specify the ID of the incident that you want to update in FortiManager.</td>
        </tr>
        <tr>
            <td>Endpoint Name</td>
            <td>Specify the details of the endpoint affected by the incident that you want to update in Fortinet FortiManager. For example, <code>11.XXX.YY.Z/32 (11.XXX.YY.Z) or 11.XXX.YY.Z/32 (Emp1 Laptop).</code></td>
        </tr>
        <tr>
            <td>Endpoint ID</td>
            <td>(Optional) Specify the endpoint ID that you want to assign to the incident you want to update in Fortinet FortiManager.</p>
            </td>
        </tr>
        <tr>
            <td>End User ID</td>
            <td>(Optional) Specify the end-user ID that you want to assign to the incident you want to update in Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Category</td>
            <td>(Optional) Select the category you want to assign to the incident you want to update in Fortinet FortiManager. You can select from the following options:
                <ul>
                    <li>Unauthorized access</li>
                    <li>Denial of Service</li>
                    <li>Malicious Code</li>
                    <li>Improper Usage</li>
                    <li>Scans/Probes/Attempted Access</li>
                    <li>Uncategorized</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Severity</td>
            <td>(Optional) Select the severity level you want to assign to the incident you want to update in Fortinet FortiManager. You can select from the following options:
                <ul>
                    <li>High</li>
                    <li>Medium</li>
                    <li>Low</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Status</td>
            <td>(Optional) Select the status you want to assign to the incident you want to update in Fortinet FortiManager. You can select from the following options:
                <ul>
                    <li>New</li>
                    <li>Analysis</li>
                    <li>Response</li>
                    <li>Closed: Remediated</li>
                    <li>Closed: False Positive</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Description</td>
            <td>(Optional) Specify the description of the incident that you want to update in Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Last Revision</td>
            <td>(Optional) Specify the last version of the incident that you want to update in Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Last User</td>
            <td>(Optional) Specify the last user of the incident that you want to update in Fortinet FortiManager.</td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "jsonrpc": "",
    "id": "",
    "result": {
        "status": {
            "code": "",
            "message": ""
        }
    }
}</pre>

<h3>operation: List ADOM Policy Package</h3>

<h4>Input parameters</h4>

<p><strong>Note</strong>: All the input parameters are optional. However, if you do not specify any parameter, then no filter criterion is applied, and an unfiltered list is returned.</p>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>ADOM Name</td>
            <td>Specify the ADOM name whose policy package you want to retrieve from Fortinet FortiManager. The ADOM that you specify here overwrites the ADOM that you have specified in the <strong>Connector Configuration</strong> as a configuration parameter.</td>
        </tr>
        <tr>
            <td>Policy Package Name</td>
            <td>Select the policy package name whose details you want to retrieve from Fortinet FortiManager. This parameter makes an API call named <code>list_adom_policy_package</code> to dynamically populate its dropdown selection.</td>
        </tr>
        <tr>
            <td>Policy Package/Folder Path</td>
            <td>Specify the policy package or folder path of the ADOM policy package whose details you want to retrieve from Fortinet FortiManager.</td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<p>Output schema when the <strong>Policy Package Name</strong> is not specified:</p>

<pre>{
    "result": [
        {
            "data": [
                {
                    "type": "",
                    "package settings": {
                        "consolidated-firewall-mode": "",
                        "fwpolicy6-implicit-log": "",
                        "fwpolicy-implicit-log": "",
                        "ngfw-mode": "",
                        "central-nat": ""
                    },
                    "oid": "",
                    "name": "",
                    "scope member": [
                        {
                            "vdom": "",
                            "name": ""
                        }
                    ],
                    "obj ver": ""
                }
            ],
            "url": "",
            "status": {
                "code": "",
                "message": ""
            }
        }
    ],
    "id": ""
}</pre>

<p>This is the default output schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "status": {
                "code": "",
                "message": ""
            },
            "data": {
                "obj ver": "",
                "name": "",
                "type": "",
                "scope member": [
                    {
                        "name": "",
                        "vdom": ""
                    }
                ],
                "oid": "",
                "package settings": {
                    "ngfw-mode": "",
                    "consolidated-firewall-mode": "",
                    "fwpolicy6-implicit-log": "",
                    "fwpolicy-implicit-log": "",
                    "central-nat": ""
                }
            },
            "url": ""
        }
    ]
}</pre>

<h3>operation: List ADOM Firewall Policies</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>ADOM Name</td>
            <td>(Optional) Specify the ADOM name whose ADOM firewall policy you want to retrieve from Fortinet FortiManager. The ADOM that you specify here overwrites the ADOM that you have specified in the <strong>Connector Configuration</strong> as a configuration parameter.</td>
        </tr>
        <tr>
            <td>Policy Package Name</td>
            <td>Select the policy package name whose firewall policy details you want to retrieve from Fortinet FortiManager. This parameter makes an API call named <code>list_adom_policy_package</code> to dynamically populate its dropdown selection.</td>
        </tr>
        <tr>
            <td>Policy Package/Folder Path</td>
            <td>(Optional) Specify the policy package or folder path of the ADOM firewall policy whose details you want to retrieve from Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>NGFW Mode</td>
            <td>Select the NGFW mode of the policy package. You can select from following options:
                <ul>
                    <li>Profile Based</li>
                    <li>Policy Based</li>
                </ul>
                By default, it is <em>Profile Based</em>.
            </td>
        </tr>
        <tr>
            <td>Firewall/Security Policy Name</td>
            <td>(Optional) Specify the firewall policy name whose details you want to retrieve from Fortinet FortiManager.</td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "data": [
                {
                    "_last_hit": "",
                    "_byte": "",
                    "custom-log-fields": [],
                    "_pkts": "",
                    "anti-replay": "",
                    "_first_hit": "",
                    "webproxy-profile": [],
                    "delay-tcp-npu-session": "",
                    "dstaddr-negate": "",
                    "tcp-mss-receiver": "",
                    "internet-service": "",
                    "srcaddr": [],
                    "traffic-shaper": [],
                    "vpn_dst_node": "",
                    "match-vip-only": "",
                    "_hitcount": "",
                    "schedule": [],
                    "fsso-agent-for-ntlm": [],
                    "permit-any-host": "",
                    "schedule-timeout": "",
                    "radius-mac-auth-bypass": "",
                    "email-collect": "",
                    "name": "",
                    "ssl-mirror-intf": [],
                    "status": "",
                    "policyid": "",
                    "vlan-cos-fwd": "",
                    "vpn_src_node": "",
                    "nat": "",
                    "block-notification": "",
                    "logtraffic-start": "",
                    "per-ip-shaper": [],
                    "tos-negate": "",
                    "traffic-shaper-reverse": [],
                    "logtraffic": "",
                    "np-acceleration": "",
                    "session-ttl": "",
                    "uuid": "",
                    "service-negate": "",
                    "srcaddr-negate": "",
                    "wccp": "",
                    "_policy_block": "",
                    "action": "",
                    "groups": [],
                    "fsso": "",
                    "tos": "",
                    "internet-service-src": "",
                    "utm-status": "",
                    "natip": [],
                    "capture-packet": "",
                    "dstaddr": [],
                    "tcp-mss-sender": "",
                    "_first_session": "",
                    "_sesscount": "",
                    "_global-vpn-tgt": "",
                    "srcintf": [],
                    "tcp-session-without-syn": "",
                    "timeout-send-rst": "",
                    "ssl-ssh-profile": [],
                    "fsso-groups": [],
                    "service": [],
                    "vlan-cos-rev": "",
                    "captive-portal-exempt": "",
                    "users": [],
                    "app-group": [],
                    "webcache-https": "",
                    "geoip-anycast": "",
                    "diffserv-forward": "",
                    "profile-type": "",
                    "rtp-nat": "",
                    "reputation-direction": "",
                    "disclaimer": "",
                    "webproxy-forward-server": [],
                    "inspection-mode": "",
                    "obj seq": "",
                    "auto-asic-offload": "",
                    "_global-vpn": [],
                    "ssl-mirror": "",
                    "dstintf": [],
                    "_last_session": "",
                    "match-vip": "",
                    "diffserv-reverse": "",
                    "dsri": "",
                    "tos-mask": "",
                    "reputation-minimum": "",
                    "profile-protocol-options": [],
                    "replacemsg-override-group": []
                }
            ],
            "status": {
                "message": "",
                "code": ""
            },
            "url": ""
        }
    ]
}</pre>

<h3>operation: ADOM Level Get Blocked IP Addresses</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>ADOM</td>
            <td>(Optional) Specify the ADOM name whose associated list of blocked IP addresses you want to retrieve from Fortinet FortiManager. The ADOM that you specify here overwrites the ADOM that you have specified in the <strong>Connector Configuration</strong> as a configuration parameter.</td>
        </tr>
        <tr>
            <td>Policy Package Name</td>
            <td>Select the policy package name whose associated blocked IP addresses you want to retrieve from Fortinet FortiManager. This parameter makes an API call named <code>list_adom_policy_package</code> to dynamically populate its dropdown selection.</td>
        </tr>
        <tr>
            <td>Policy Package/Folder Path</td>
            <td>(Optional) Specify the policy package or folder path of the ADOM Firewall policy whose associated blocked IP addresses you want to retrieve from Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Firewall Policy Name</td>
            <td>Specify the Firewall policy name associated with the blocked IP addresses you want to retrieve from Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Address Group Name</td>
            <td>Specify the name of the IP address group, in the CSV or list format, that you have specified in Fortinet FortiManager for blocking or unblocking IP addresses. For more information, see the <a href="#blockUnblockIPAdd">Blocking or Unblocking IP addresses, URLs, or applications in Fortinet FortiManager</a> section.</td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "policy_name": "",
    "dstaddr": [],
    "srcaddr": [],
    "addrgrp": [
        {
            "name": "",
            "member": []
        }
    ],
    "addrgrp_not_exist": []
}</pre>

<h3>operation: ADOM Level Block IP Address</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>ADOM Name</td>
            <td>(Optional) Specify the ADOM name whose associated IP addresses you want to block in the firewall policy of Fortinet FortiManager. The ADOM that you specify here overwrites the ADOM that you have specified in the <strong>Connector Configuration</strong> as a configuration parameter.</td>
        </tr>
        <tr>
            <td>NGFW Mode</td>
            <td>Select the NGFW mode of the policy package. You can select from following options:
                <ul>
                    <li>Profile Based</li>
                    <li>Policy Based</li>
                </ul>
                By default, it is <em>Profile Based</em>.
            </td>
        </tr>
        <tr>
            <td>Policy Package Name</td>
            <td>Select the policy package name whose associated IP addresses you want to block in the firewall policy of Fortinet FortiManager. This parameter makes an API call named <code>list_adom_policy_package</code> to dynamically populate its dropdown selection.</td>
        </tr>
        <tr>
            <td>Policy Package/Folder Path</td>
            <td>(Optional) Specify the policy package or folder path of the ADOM firewall policy whose associated IP addresses you want to block in Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Firewall Policy Name</td>
            <td>Specify the name of the firewall policy that you have specified in Fortinet FortiManager for blocking or unblocking IP addresses.</td>
        </tr>
        <tr>
            <td>Address Group Name</td>
            <td>Specify the name of the IP address group that you have specified in Fortinet FortiManager for blocking or unblocking IP addresses. For more information, see the <a href="#blockUnblockIPAdd">Blocking or Unblocking IP addresses, URLs, or applications in Fortinet FortiManager</a> section.</td>
        </tr>
        <tr>
            <td>IP Address</td>
            <td>Specify the IP addresses that you want to block using Fortinet FortiManager in the CSV or list format. For example, <code>[&quot;1.1.1.1&quot;, &quot;2.2.2.2&quot;] or &quot;1.1.1.1&quot;, &quot;2.2.2.2&quot;</code>.</td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "already_blocked": [],
    "newly_blocked": [],
    "error_with_block": []
}</pre>

<h3>operation: ADOM Level Unblock IP Address</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>ADOM Name</td>
            <td>(Optional) Specify the ADOM name whose associated IP addresses you want to unblock in the firewall policy of Fortinet FortiManager. The ADOM that you specify here overwrite the ADOM that you have specified in the <strong>Connector Configuration</strong> as a configuration parameter.</td>
        </tr>
        <tr>
            <td>NGFW Mode</td>
            <td>Select the NGFW mode of the policy package. You can select from following options:
                <ul>
                    <li>Profile Based</li>
                    <li>Policy Based</li>
                </ul>
                By default, it is <em>Profile Based</em>.
            </td>
        </tr>
        <tr>
            <td>Policy Package Name</td>
            <td>Select the policy package name whose associated IP addresses you want to unblock in the firewall policy of Fortinet FortiManager. This parameter makes an API call named <code>list_adom_policy_package</code> to dynamically populate its dropdown selection.</td>
        </tr>
        <tr>
            <td>Policy Package/Folder Path</td>
            <td>(Optional) Specify the policy package or folder path of the ADOM firewall policy whose associated IP addresses you want to unblock in Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Firewall Policy Name</td>
            <td>Specify the name of the firewall Policy that you have specified in Fortinet FortiManager for blocking or unblocking IP addresses.</td>
        </tr>
        <tr>
            <td>Address Group Name</td>
            <td>Specify the name of the IP address group, that you have specified in Fortinet FortiManager for blocking or unblocking IP addresses. For more information, see the <a href="#blockUnblockIPAdd">Blocking or Unblocking IP addresses, URLs, or applications in Fortinet FortiManager</a> section.</td>
        </tr>
        <tr>
            <td>Address name/IP</td>
            <td>Specify the IP addresses that you want to unblock using Fortinet FortiManager in the CSV or list format. For example, <code>[&quot;1.1.1.1&quot;, &quot;2.2.2.2&quot;] or &quot;1.1.1.1&quot;, &quot;2.2.2.2&quot;</code>.</td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "not_exist": [],
    "newly_unblocked": [],
    "error_with_unblock": []
}</pre>

<h3>operation: Re-install Policy</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>ADOM Name</td>
            <td>(Optional) Specify the ADOM name to which you want to apply the firewall policy in Fortinet FortiManager. The ADOM that you specify here overwrites the ADOM that you have specified in the <strong>Connector Configuration</strong> as a configuration parameter.</td>
        </tr>
        <tr>
            <td>Policy Package Name</td>
            <td>Select the policy package name to which you want to apply the firewall policy in Fortinet FortiManager. This parameter makes an API call named <code>list_adom_policy_package</code> to dynamically populate its dropdown selection.</td>
        </tr>
        <tr>
            <td>Policy Package/Folder Path</td>
            <td>(Optional) Specify the policy package or folder path to apply the firewall policy in Fortinet FortiManager.</td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "data": {
                "task": ""
            },
            "status": {
                "message": "",
                "code": ""
            },
            "url": ""
        }
    ]
}</pre>

<h3>operation: List Global Policy Package</h3>

<h4>Input parameters</h4>

<p><strong>Note</strong>: All the input parameters are optional. However, if you do not specify any parameter, then no filter criterion is applied, and an unfiltered list is returned.</p>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Package Name</td>
            <td>Specify the name of the global policy package from which you want to retrieve package details.</td>
        </tr>
        <tr>
            <td>Policy Package/Folder Path</td>
            <td>Specify the policy package or folder path from which you want to retrieve package details.</td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<p>Output schema when the "Package Name" is not specified:</p>

<pre>{
    "result": [
        {
            "url": "",
            "data": [
                {
                    "type": "",
                    "package settings": {
                        "ngfw-mode": "",
                        "central-nat": "",
                        "consolidated-firewall-mode": "",
                        "fwpolicy-implicit-log": "",
                        "fwpolicy6-implicit-log": ""
                    },
                    "scope member": [
                        {
                            "name": ""
                        }
                    ],
                    "obj ver": "",
                    "name": "",
                    "oid": ""
                }
            ],
            "status": {
                "message": "",
                "code": ""
            }
        }
    ],
    "id": ""
}</pre>

<p>This is the default output schema:</p>

<pre>{
    "result": [
        {
            "url": "",
            "data": {
                "type": "",
                "package settings": {
                    "ngfw-mode": "",
                    "central-nat": "",
                    "consolidated-firewall-mode": "",
                    "fwpolicy-implicit-log": "",
                    "fwpolicy6-implicit-log": ""
                },
                "scope member": [
                    {
                        "name": ""
                    }
                ],
                "obj ver": "",
                "name": "",
                "oid": ""
            },
            "status": {
                "message": "",
                "code": ""
            }
        }
    ],
    "id": ""
}</pre>

<h3>operation: List Global Firewall Policies</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Policy Package Name</td>
            <td>Specify the name of the global firewall policy package from which you want to retrieve package details. This parameter makes an API call named <code>list_global_policy_pck</code> to dynamically populate its dropdown selections.</td>
        </tr>
        <tr>
            <td>Policy Package/Folder Path</td>
            <td>(Optional) Specify the policy package or folder path from which you want to retrieve package details.</td>
        </tr>
        <tr>
            <td>Policy Type</td>
            <td>Select the policy type from which you want to retrieve firewall policy details.</td>
        </tr>
        <tr>
            <td>Policy Name</td>
            <td>(Optional) Specify the name of the global firewall policy whose details you want to retrieve from Fortinet FortiManager.</td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "result": [
        {
            "url": "",
            "data": [
                {
                    "ssl-ssh-profile": [],
                    "_pkts": "",
                    "disclaimer": "",
                    "diffserv-reverse": "",
                    "replacemsg-override-group": [],
                    "dstaddr": [],
                    "per-ip-shaper": [],
                    "vlan-cos-rev": "",
                    "schedule": [],
                    "wccp": "",
                    "_byte": "",
                    "status": "",
                    "groups": [],
                    "block-notification": "",
                    "_global-vpn": [],
                    "webcache-https": "",
                    "obj seq": "",
                    "utm-status": "",
                    "webproxy-profile": [],
                    "tcp-mss-receiver": "",
                    "tos-negate": "",
                    "profile-type": "",
                    "reputation-minimum": "",
                    "timeout-send-rst": "",
                    "policyid": "",
                    "dstaddr-negate": "",
                    "traffic-shaper": [],
                    "profile-protocol-options": [],
                    "internet-service": "",
                    "reputation-direction": "",
                    "natip": [],
                    "session-ttl": "",
                    "vlan-cos-fwd": "",
                    "delay-tcp-npu-session": "",
                    "webproxy-forward-server": [],
                    "email-collect": "",
                    "np-acceleration": "",
                    "fsso-agent-for-ntlm": [],
                    "identity-based-policy": "",
                    "name": "",
                    "tos": "",
                    "_first_session": "",
                    "uuid": "",
                    "_sesscount": "",
                    "match-vip": "",
                    "logtraffic": "",
                    "schedule-timeout": "",
                    "traffic-shaper-reverse": [],
                    "tos-mask": "",
                    "permit-any-host": "",
                    "anti-replay": "",
                    "capture-packet": "",
                    "ssl-mirror-intf": [],
                    "srcaddr": [],
                    "service": [],
                    "internet-service-src": "",
                    "dstintf": [],
                    "_last_hit": "",
                    "_hitcount": "",
                    "_first_hit": "",
                    "gtp-profile": [],
                    "radius-mac-auth-bypass": "",
                    "diffserv-forward": "",
                    "geoip-anycast": "",
                    "tcp-mss-sender": "",
                    "app-group": [],
                    "rtp-nat": "",
                    "inspection-mode": "",
                    "tcp-session-without-syn": "",
                    "logtraffic-start": "",
                    "auto-asic-offload": "",
                    "action": "",
                    "fsso-groups": [],
                    "fsso": "",
                    "_global-vpn-tgt": "",
                    "captive-portal-exempt": "",
                    "users": [],
                    "custom-log-fields": [],
                    "dsri": "",
                    "srcintf": [],
                    "nat": "",
                    "service-negate": "",
                    "match-vip-only": "",
                    "ssl-mirror": "",
                    "_last_session": "",
                    "srcaddr-negate": ""
                }
            ],
            "status": {
                "message": "",
                "code": ""
            }
        }
    ],
    "id": ""
}</pre>

<h3>operation: Global Level Get Blocked IP Addresses</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Policy Package Name</td>
            <td>Specify the name of the global firewall policy whose associated blocked IP addresses you want to retrieve from Fortinet FortiManager. This parameter makes an API call named <code>list_global_policy_pck</code> to dynamically populate its dropdown selections.</td>
        </tr>
        <tr>
            <td>Policy Package/Folder Path</td>
            <td>(Optional) Specify the policy package or folder path of the global firewall policy whose associated blocked IP addresses you want to retrieve from Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Policy Type</td>
            <td>Select the policy type based on which you want to retrieve blocked IP addresses from Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Firewall Policy Name</td>
            <td>Specify the firewall policy name associated with the blocked IP addresses you want to retrieve from Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Address Group Name</td>
            <td>Specify the name of the IP address group, in the CSV or list format, that you have specified in Fortinet FortiManager for blocking or unblocking IP addresses. For more information, see the <a href="#blockUnblockIPAdd">Blocking or Unblocking IP addresses, URLs, or applications in Fortinet FortiManager</a> section.</td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "policy_name": "",
    "dstaddr": [],
    "srcaddr": [],
    "addrgrp": [
        {
            "name": "",
            "member": []
        }
    ],
    "addrgrp_not_exist": []
}</pre>

<h3>operation: Global Level Block IP Address</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Policy Package Name</td>
            <td>Select the policy package whose associated IP addresses you want to block in the global firewall policy of Fortinet FortiManager. This parameter makes an API call named <code>list_global_policy_pck</code> to dynamically populate its dropdown selections.</td>
        </tr>
        <tr>
            <td>Policy Package/Folder Path</td>
            <td>(Optional) Specify the policy package or folder path of the global firewall policy whose associated IP addresses you want to block in Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Policy Type</td>
            <td>Select the policy type whose IP addresses you want to block in Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Firewall Policy Name</td>
            <td>Specify the name of the firewall Policy that you have specified in Fortinet FortiManager for blocking or unblocking IP addresses.</td>
        </tr>
        <tr>
            <td>Address Group Name</td>
            <td>Specify the name of the IP address group, that you have specified in Fortinet FortiManager for blocking or unblocking IP addresses. For more information, see the <a href="#blockUnblockIPAdd">Blocking or Unblocking IP addresses, URLs or applications in Fortinet FortiManager</a> section.</td>
        </tr>
        <tr>
            <td>IP Address</td>
            <td>Specify the IP addresses that you want to block using Fortinet FortiManager in the CSV or list format.For example, <code>[&quot;1.1.1.1&quot;, &quot;2.2.2.2&quot;] or &quot;1.1.1.1&quot;, &quot;2.2.2.2&quot;</code>.</td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "already_blocked": [],
    "newly_blocked": [],
    "error_with_block": []
}</pre>

<h3>operation: Global Level Unblock IP Address</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Policy Package Name</td>
            <td>Select the policy package whose associated IP addresses you want to unblock in the global firewall policy of Fortinet FortiManager. This parameter makes an API call named <code>list_global_policy_pck</code> to dynamically populate its dropdown selections.</td>
        </tr>
        <tr>
            <td>Policy Package/Folder Path</td>
            <td>(Optional) Specify the policy package or folder path of the global firewall policy whose associated IP addresses you want to unblock in Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Policy Type</td>
            <td>Select the policy type whose IP addresses you want to unblock in Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Firewall Policy Name</td>
            <td>Specify the name of the firewall Policy that you have specified in Fortinet FortiManager for blocking or unblocking IP addresses.</td>
        </tr>
        <tr>
            <td>Address Group Name</td>
            <td>Specify the name of the IP address group, that you have specified in Fortinet FortiManager for blocking or unblocking IP addresses. For more information, see the <a href="#blockUnblockIPAdd">Blocking or Unblocking IP addresses, URLs, or applications in Fortinet FortiManager</a> section.</td>
        </tr>
        <tr>
            <td>Address name/IP</td>
            <td>Specify the IP addresses that you want to unblock using Fortinet FortiManager in the CSV or list format.For example, <code>[&quot;1.1.1.1&quot;, &quot;2.2.2.2&quot;] or &quot;1.1.1.1&quot;, &quot;2.2.2.2&quot;</code>.</td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "not_exist": [],
    "newly_unblocked": [],
    "error_with_unblock": []
}</pre>

<h3>operation: Assign Global Policy Package</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Policy Package Name</td>
            <td>Select the policy package that you want to assign to ADOM devices in the global firewall policy of Fortinet FortiManager. This parameter makes an API call named <code>list_global_policy_pck</code> to dynamically populate its dropdown selections.</td>
        </tr>
        <tr>
            <td>Policy Package/Folder Path</td>
            <td>Specify the policy package or folder path of the global policy package that you want to assign to ADOM devices in Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>ADOM Devices</td>
            <td>Specify one or more destination ADOMs to which you want to assign the selected global policy package. This parameter makes an API call named <code>list_global_adom</code> to dynamically populate its dropdown selections.</td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "data": {
                "task": ""
            },
            "status": {
                "message": "",
                "code": ""
            },
            "url": ""
        }
    ]
}</pre>

<h3>operation: Get Device Groups List</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Level Type</td>
            <td>Select the level type from which to retrieve the device group details. You can select from following options:
                <ul>
                    <li><strong>ADOM</strong>: Specify the following parameters:
                        <ul>
                            <li><strong>ADOM</strong>: Administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified as a configuration parameter.</li>
                            <li><strong>Device Group</strong>: Valid device group name based on which you want to retrieve details of the device group from Fortinet FortiManager.
                                <p><strong>NOTE</strong>: If this parameter is left blank or <code>null</code>, this operation returns devices matching all values.</p>
                            </li>
                        </ul>
                    </li>
                    <li><strong>Global</strong>: Specify values in the following fields:
                        <ul>
                            <li><strong>Device Group</strong>: Valid device group name based on which you want to retrieve details of the device group from Fortinet FortiManager.
                                <p><strong>NOTE</strong>: If this parameter is left blank or <code>null</code>, this operation returns devices matching all values.</p>
                            </li>
                        </ul>
                    </li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Attributes in Result</td>
            <td>(Optional) Specify a string array to limit the output by returning only the specified attributes. For example, <code>[ &quot;desc&quot;, &quot;name&quot;, &quot;os_type&quot;, &quot;type&quot;]</code>. If attributes are not specified, then all attributes are returned.</td>
        </tr>
        <tr>
            <td>Filter By</td>
            <td>(Optional) Specify attributes to filter the results according to a set criteria. Attributes are <code>desc</code>, <code>name</code>, <code>os_type</code>, and <code>type</code>. For example, <code>[[&quot;name&quot;, &quot;==&quot;, &quot;All_FortiADC&quot;],[ &quot;os_type&quot;, &quot;==&quot;, 9]]</code>.</td>
        </tr>
        <tr>
            <td>Limit</td>
            <td>(Optional) Specify the maximum number of results that this operation should return.</td>
        </tr>
        <tr>
            <td>Offset</td>
            <td>(Optional) Specify the offset value to retrieve a subset of records that starts from the offset value. The offset works with the <em>Limit</em> parameter, which determines how many records to retrieve starting from the offset. Values supported are:
                <ul>
                    <li><strong>Default:<code>&quot;0&quot;</code></strong></li>
                    <li><strong>Minimum:<code>&quot;0&quot;</code></strong></li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Sort By</td>
            <td>Select <em>Field</em> as the sorting criteria to order the results. Once selected, specify values in the following fields:
                <ul>
                    <li><strong>Field</strong>: Specify the name of the field on which to sort the results. For example, severity, or category.</li>
                    <li><strong>Order</strong>: Select the order in which to sort the results. You can select from following options:
                        <ul>
                            <li>Ascending (default)</li>
                            <li>Descending</li>
                        </ul>
                    </li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "url": "",
            "data": {
                "oid": "",
                "desc": "",
                "name": "",
                "type": "",
                "os_type": ""
            },
            "status": {
                "code": "",
                "message": ""
            }
        }
    ]
}</pre>

<h3>operation: Create Address</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Level Type</td>
            <td>Select the level type on which to create the address. You can select from following options:
                <ul>
                    <li><strong>ADOM</strong>: Specify the following parameters:
                        <ul>
                            <li><strong>ADOM</strong>: Administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified as a configuration parameter.</li>
                            <li><strong>Address Name</strong>: Valid address name to create in Fortinet FortiManager.</li>
                        </ul>
                    </li>
                    <li><strong>Global</strong>: Specify values in the following fields:
                        <ul>
                            <li><strong>Address Name</strong>: Valid address name to create in Fortinet FortiManager.</li>
                        </ul>
                    </li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Address Type</td>
            <td>Select the type of address to create in Fortinet FortiManager. You can select from following options:
                <ul>
                    <li><strong>Subnet</strong>: Specify values in the following fields:
                        <ul>
                            <li><strong>Subnet</strong>: Specify the IP address and subnet mask of the address that you want to create.</li>
                            <li><strong>Subnet Name</strong>: Specify the Subnet name of the address that you want to create.</li>
                        </ul>
                    </li>
                    <li><strong>IP Range</strong>: Specify values in the following fields:
                        <ul>
                            <li><strong>Start IP</strong>: Specify the starting (First) IP address (inclusive) in the IP address range to be assigned to the address you want to create.</li>
                            <li><strong>End IP</strong>: Specify the ending (Final) IP address (inclusive) in the IP address range to be assigned to the address you want to create.</li>
                        </ul>
                    </li>
                    <li><strong>FQDN</strong>: Specify the Fully Qualified Domain Name (FQDN) of the address to create, in the <strong>FQDN</strong> field.</li>
                    <li><strong>Wildcard</strong>: Specify the IP address and wildcard netmask of the address to create, in the <strong>Wildcard</strong> field.</li>
                    <li><strong>Geography</strong>: Specify the country whose IP addresses you want to associate with the address being created, in the <strong>Country</strong> field.</li>
                    <li><strong>MAC Address</strong>: Specify values in the following fields:
                        <ul>
                            <li><strong>MAC Address Scope</strong>: Select the MAC address scope to be associated with the address being created. You can select from following options:
                                <ul>
                                    <li><strong>Single Address</strong>: Specify the single MAC address to be added to the address being created, in the <strong>MAC Address</strong> field. For example, <code>00:15:00:e8:27:25</code>.</li>
                                    <li><strong>Range</strong>: Specify values in the following fields:
                                        <ul>
                                            <li><strong>MAC Address Start</strong>: Specify the starting (First) MAC address of the address range to create. For example, <code>00:15:00:e8:27:25</code></li>
                                            <li><strong>MAC Address End</strong>: : Specify the ending (Final) MAC address of the address range to create. For example, <code>00:15:00:e8:27:27</code></li>
                                        </ul>
                                    </li>
                                    <li><strong>MAC List</strong>: Specify a CSV or a list of MAC addresses being created, in the <strong>MAC Address</strong> field. For example:
                                        <pre>[&quot;00:15:00:e8:27:25&quot;,&quot;00:15:00:e8:27:26&quot;,]</pre>
                                    </li>
                                </ul>
                            </li>
                        </ul>
                    </li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Policy Group Name</td>
            <td>(Optional) Specify the name of the policy group to be added to the address that you want to create.</td>
        </tr>
        <tr>
            <td>Comment</td>
            <td>(Optional) Comment to be added to the address that you want to create.</td>
        </tr>
        <tr>
            <td>Additional Address Arguments</td>
            <td>(Optional) Specify additional arguments, in JSON format, to be added during the creation of the address. You can enter the arguments in the following format: <code>{&quot;field1&quot;:value1, &quot;field2&quot;:value2}</code></td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "url": "",
            "data": {
                "name": ""
            },
            "status": {
                "code": "",
                "message": ""
            }
        }
    ]
}</pre>

<h3>operation: Get Addresses List</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Level Type</td>
            <td>Select the level type from which to retrieve the address details. You can select from following options:
                <ul>
                    <li><strong>ADOM</strong>: Specify the following parameters:
                        <ul>
                            <li><strong>ADOM</strong>: Administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified as a configuration parameter.</li>
                            <li><strong>Address Name</strong>: Valid address name to retrieve its details from Fortinet FortiManager.
                                <p><strong>NOTE</strong>: If this parameter is left blank or <code>null</code>, this operation returns addresses matching all values.</p>
                            </li>
                        </ul>
                    </li>
                    <li><strong>Global</strong>: Specify values in the following fields:
                        <ul>
                            <li><strong>Address Name</strong>: Valid address name to retrieve its details from Fortinet FortiManager.
                                <p><strong>NOTE</strong>: If this parameter is left blank or <code>null</code>, this operation returns addresses matching all values.</p>
                            </li>
                        </ul>
                    </li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Attributes in Result</td>
            <td>(Optional) Specify a string array to limit the output by returning only the specified attributes. For example,<code>&nbsp;[ &quot;_image-base64&quot;, &quot;allow-routing&quot;, &quot;associated-interface&quot;, &quot;cache-ttl&quot;, &quot;clearpass-spt&quot;, &quot;color&quot;, &quot;comment&quot;, &quot;country&quot;, &quot;end-ip&quot;, &quot;epg-name&quot;, &quot;fabric-object&quot;, &quot;filter&quot;, &quot;fqdn&quot;, &quot;fsso-group&quot;, &quot;interface&quot;, &quot;macaddr&quot;, &quot;name&quot;, &quot;node-ip-only&quot;, &quot;obj-id&quot;, &quot;obj-tag&quot;, &quot;obj-type&quot;, &quot;organization&quot;, &quot;policy-group&quot;, &quot;sdn&quot;, &quot;sdn-addr-type&quot;, &quot;sdn-tag&quot;, &quot;start-ip&quot;, &quot;sub-type&quot;, &quot;subnet&quot;, &quot;subnet-name&quot;, &quot;tenant&quot;, &quot;type&quot;, &quot;uuid&quot;, &quot;wildcard&quot;, &quot;wildcard-fqdn&quot;]&nbsp;</code>
                <p><strong>Note</strong>: If attributes are not specified, then all attributes will be returned.</p>
            </td>
        </tr>
        <tr>
            <td>Filter By</td>
            <td>(Optional) Specify attributes to filter the results according to a set criteria.</td>
        </tr>
        <tr>
            <td>Limit</td>
            <td>(Optional) Specify the maximum number of results that this operation should return.</td>
        </tr>
        <tr>
            <td>Offset</td>
            <td>(Optional) Specify the offset value to retrieve a subset of records that starts from the offset value. The offset works with the <em>Limit</em> parameter, which determines how many records to retrieve starting from the offset. Values supported are:
                <ul>
                    <li><strong>Default:<code>&quot;0&quot;</code></strong></li>
                    <li><strong>Minimum:<code>&quot;0&quot;</code></strong></li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Sort By</td>
            <td>Select <em>Field</em> as the sorting criteria to order the results and specify values in the following fields:
                <ul>
                    <li><strong>Field</strong>: Specify the name of the field on which to sort the results. For example,<code> _image-base64, allow-routing, associated-interface, cache-ttl, clearpass-spt, color, comment, country, end-ip, epg-name, fabric-object, filter, fqdn, fsso-group, interface, macaddr, name, node-ip-only, obj-id, obj-tag, obj-type, organization, policy-group, sdn, sdn-addr-type, sdn-tag, start-ip, sub-type, subnet, subnet-name, tenant, type, uuid, wildcard, wildcard-fqdn,</code> etc.</li>
                    <li><strong>Order</strong>: Select the order in which to sort the results. You can select from following options:
                        <ul>
                            <li>Ascending (default)</li>
                            <li>Descending</li>
                        </ul>
                    </li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "url": "",
            "status": {
                "code": "",
                "message": ""
            },
            "data": [
                {
                    "list": "",
                    "name": "",
                    "type": "",
                    "uuid": "",
                    "color": "",
                    "subnet": [],
                    "comment": "",
                    "macaddr": [],
                    "tagging": "",
                    "obj-type": "",
                    "node-ip-only": "",
                    "allow-routing": "",
                    "clearpass-spt": "",
                    "fabric-object": "",
                    "sdn-addr-type": "",
                    "dynamic_mapping": "",
                    "associated-interface": []
                }
            ]
        }
    ]
}</pre>

<h3>operation: Update Address</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Level Type</td>
            <td>Select the level type at which you want to update the address. You can select from following options:
                <ul>
                    <li><strong>ADOM</strong>: Specify the following parameters:
                        <ul>
                            <li><strong>ADOM</strong>: Administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified as a configuration parameter.</li>
                            <li><strong>Address Name</strong>: Valid address name to update in Fortinet FortiManager.</li>
                        </ul>
                    </li>
                    <li><strong>Global</strong>: Specify values in the following fields:
                        <ul>
                            <li><strong>Address Name</strong>: Valid address name to update in Fortinet FortiManager.</li>
                        </ul>
                    </li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Address Type</td>
            <td>Select the type of address to update in Fortinet FortiManager. You can select from following options:
                <ul>
                    <li><strong>Subnet</strong>: Specify values in the following fields:
                        <ul>
                            <li><strong>Subnet</strong>: Specify the IP address and subnet mask of the address that you want to update.</li>
                            <li><strong>Subnet Name</strong>: Specify the Subnet name of the address that you want to update.</li>
                        </ul>
                    </li>
                    <li><strong>IP Range</strong>: Specify values in the following fields:
                        <ul>
                            <li><strong>Start IP</strong>: Specify the starting (First) IP address (inclusive) in the IP address range to be assigned to the address you want to update.</li>
                            <li><strong>End IP</strong>: Specify the ending (Final) IP address (inclusive) in the IP address range to be assigned to the address you want to update.</li>
                        </ul>
                    </li>
                    <li><strong>FQDN</strong>: Specify the Fully Qualified Domain Name (FQDN) of the address to update, in the <strong>FQDN</strong> field.</li>
                    <li><strong>Wildcard</strong>: Specify the IP address and wildcard netmask of the address to update, in the <strong>Wildcard</strong> field.</li>
                    <li><strong>Geography</strong>: Specify the country whose IP addresses you want to associate with the address being updated, in the <strong>Country</strong> field.</li>
                    <li><strong>MAC Address</strong>: Specify values in the following fields:
                        <ul>
                            <li><strong>MAC Address Scope</strong>: Select the MAC address scope to be associated with the address being updated. You can select from following options:
                                <ul>
                                    <li><strong>Single Address</strong>: Specify the single MAC address to be added to the address being updated, in the <strong>MAC Address</strong> field. For example, <code>00:15:00:e8:27:25</code>.</li>
                                    <li><strong>Range</strong>: Specify values in the following fields:
                                        <ul>
                                            <li><strong>MAC Address Start</strong>: Specify the starting (First) MAC address of the address range to update. For example, <code>00:15:00:e8:27:25</code></li>
                                            <li><strong>MAC Address End</strong>: : Specify the ending (Final) MAC address of the address range to update. For example, <code>00:15:00:e8:27:27</code></li>
                                        </ul>
                                    </li>
                                    <li><strong>MAC List</strong>: Specify a CSV or a list of MAC addresses being updated, in the <strong>MAC Address</strong> field. For example:
                                        <pre>[&quot;00:15:00:e8:27:25&quot;,&quot;00:15:00:e8:27:26&quot;,]</pre>
                                    </li>
                                </ul>
                            </li>
                        </ul>
                    </li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Policy Group Name</td>
            <td>(Optional) Specify the name of the policy group to be added to the address that you want to update.</td>
        </tr>
        <tr>
            <td>Comment</td>
            <td>(Optional) Specify a comment to be added to the address that you want to update.</td>
        </tr>
        <tr>
            <td>Additional Address Arguments</td>
            <td>(Optional) Specify additional arguments, in JSON format, to be added during the updation of the address. You can enter the arguments in the following format: <code>{&quot;field1&quot;:value1, &quot;field2&quot;:value2}</code>.</td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "url": "",
            "data": {
                "name": ""
            },
            "status": {
                "code": "",
                "message": ""
            }
        }
    ]
}</pre>

<h3>operation: Delete Address</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Level Type</td>
            <td>Select the level type from which to delete the address. You can select from following options:
                <ul>
                    <li><strong>ADOM</strong>: Specify the following parameters:
                        <ul>
                            <li><strong>ADOM</strong>: Administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified as a configuration parameter.</li>
                            <li><strong>Address Name</strong>: Valid address name to delete from Fortinet FortiManager.</li>
                        </ul>
                    </li>
                    <li><strong>Global</strong>: Specify values in the following fields:
                        <ul>
                            <li><strong>Address Name</strong>: Valid address name to delete from Fortinet FortiManager.</li>
                        </ul>
                    </li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "url": "",
            "status": {
                "code": "",
                "message": ""
            }
        }
    ]
}</pre>

<h3>operation: Create Address Group</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Level Type</td>
            <td>Select the level type in which to create the address group. You can select from following options:
                <ul>
                    <li><strong>ADOM</strong>: Specify the following parameters:
                        <ul>
                            <li><strong>ADOM</strong>: Specify the Administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified as a configuration parameter.</li>
                            <li><strong>Address Group Name</strong>: Specify a valid address group name to create in Fortinet FortiManager.</li>
                        </ul>
                    </li>
                    <li><strong>Global</strong>: Specify values in the following fields:
                        <ul>
                            <li><strong>Address Group</strong>: Specify a valid address group name to create in Fortinet FortiManager.</li>
                        </ul>
                    </li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Type</td>
            <td>Select the type of address group to create in Fortinet FortiManager. You can select from the following options:
                <ul>
                    <li><strong>Group (default)</strong>: Select this option if the members belong to multiple groups.</li>
                    <li><strong>Folder</strong>: Select this option if the members do not belong to any group.</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Member</td>
            <td>Specify a CSV list or a list of address objects or address groups that you want to add to the address group being created in Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Exclude</td>
            <td>Select this option, i.e., set it to true, to enable address exclusion. Once selected, specify a CSV list or a list of address objects or address groups to add to the exclude member list, in the <strong>Exclude Member</strong> field.</td>
        </tr>
        <tr>
            <td>Comment</td>
            <td>(Optional) Specify the comment to be added to the address group that you want to create.</td>
        </tr>
        <tr>
            <td>Additional Address Group Arguments</td>
            <td>(Optional) Specify additional arguments, in JSON format, to be added during the creation of the address group. You can enter the arguments in the following format:
                <pre>{&quot;field1&quot;:value1, &quot;field2&quot;:value2}</pre>
            </td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "url": "",
            "data": {
                "name": ""
            },
            "status": {
                "code": "",
                "message": ""
            }
        }
    ]
}</pre>

<h3>operation: Get Address Groups List</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Level Type</td>
            <td>Select the level type from which you want to retrieve the address group details. You can select from following options:
                <ul>
                    <li><strong>ADOM</strong>: Specify values in the following fields:
                        <ul>
                            <li><strong>ADOM</strong>: Administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified as a configuration parameter.</li>
                            <li><strong>Address Group</strong>: Valid address group name based on which you want to retrieve address group details from Fortinet FortiManager.
                                <p><strong>Note</strong>: If this parameter is left blank or <code>null</code>, this operation returns address groups matching all values.</p>
                            </li>
                        </ul>
                    </li>
                    <li><strong>Global</strong>: Specify values in the following fields:
                        <ul>
                            <li><strong>Address Group</strong>: Valid address group name based on which you want to retrieve address group details from Fortinet FortiManager.
                                <p><strong>Note</strong>: If this parameter is left blank or <code>null</code>, this operation returns address groups matching all values.</p>
                            </li>
                        </ul>
                    </li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Attributes in Result</td>
            <td>(Optional) Specify a string array to limit the output by returning only the specified attributes. For example,<code>[ &quot;_image-base64&quot;, &quot;allow-routing&quot;, &quot;associated-interface&quot;, &quot;cache-ttl&quot;, &quot;clearpass-spt&quot;, &quot;color&quot;, &quot;comment&quot;, &quot;country&quot;, &quot;end-ip&quot;, &quot;epg-name&quot;, &quot;fabric-object&quot;, &quot;filter&quot;, &quot;fqdn&quot;, &quot;fsso-group&quot;, &quot;interface&quot;, &quot;macaddr&quot;, &quot;name&quot;, &quot;node-ip-only&quot;, &quot;obj-id&quot;, &quot;obj-tag&quot;, &quot;obj-type&quot;, &quot;organization&quot;, &quot;policy-group&quot;, &quot;sdn&quot;, &quot;sdn-addr-type&quot;, &quot;sdn-tag&quot;, &quot;start-ip&quot;, &quot;sub-type&quot;, &quot;subnet&quot;, &quot;subnet-name&quot;, &quot;tenant&quot;, &quot;type&quot;, &quot;uuid&quot;, &quot;wildcard&quot;, &quot;wildcard-fqdn&quot;]</code><br />
                <strong>Note</strong>: If attributes are not specified, then all attributes will be returned.
            </td>
        </tr>
        <tr>
            <td>Filter By</td>
            <td>(Optional) Specify attributes to filter the results according to a set criteria.
        </tr>
        <tr>
            <td>Limit</td>
            <td>(Optional) Specify the maximum number of results that this operation should return.</td>
        </tr>
        <tr>
            <td>Offset</td>
            <td>(Optional) Specify the offset value to retrieve a subset of records that starts from the offset value. The offset works with the <em>Limit</em> parameter, which determines how many records to retrieve starting from the offset. Values supported are:
                <ul>
                    <li><strong>Default:<code>&quot;0&quot;</code></strong></li>
                    <li><strong>Minimum:<code>&quot;0&quot;</code></strong></li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Sort By</td>
            <td>Select <em>Field</em> as the sorting criteria to order the results and specify values in the following fields:
                <ul>
                    <li><strong>Field</strong>: Specify the name of the field on which to sort the results. For example, <code>_image-base64, allow-routing, category, color, comment, exclude, exclude-member, fabric-object, member, name, type, uuid</code></li>
                    <li><strong>Order</strong>: Select the order in which to sort the results. You can select from following options:
                        <ul>
                            <li>Ascending (default)</li>
                            <li>Descending</li>
                        </ul>
                    </li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "url": "",
            "data": [
                {
                    "name": "",
                    "type": "",
                    "uuid": "",
                    "color": "",
                    "member": [],
                    "exclude": "",
                    "tagging": "",
                    "category": "",
                    "allow-routing": "",
                    "fabric-object": "",
                    "exclude-member": [],
                    "dynamic_mapping": ""
                }
            ],
            "status": {
                "code": "",
                "message": ""
            }
        }
    ]
}</pre>

<h3>operation: Update Address Group</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Level Type</td>
            <td>Select the level type at which you want to update the address group. You can select from following options:
                <ul>
                    <li><strong>ADOM</strong>: Specify the following parameters:
                        <ul>
                            <li><strong>ADOM</strong>: Administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified as a configuration parameter.</li>
                            <li><strong>Address Group</strong>: Valid address group to update in Fortinet FortiManager.</li>
                        </ul>
                    </li>
                    <li><strong>Global</strong>: Specify values in the following fields:
                        <ul>
                            <li><strong>Address Group</strong>: Valid address group to update in Fortinet FortiManager.</li>
                        </ul>
                    </li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Method</td>
            <td>Select the action that you want to perform on members of the address group. You can from following options:
                <ul>
                    <li><strong>Add</strong>: Specify a CSV or a list of address group objects to add to the address group being updated in the <strong>Add Member</strong> field.</li>
                    <li><strong>Remove</strong>: Specify a CSV or a list of address group objects to remove from the address group being updated in the <strong>Remove Member</strong> field.</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Exclude</td>
            <td>Select this option, i.e., set it to true, to enable address exclusion and if this option is selected, then specify the following:
                <ul>
                    <li>In the <strong>Add Exclude Member</strong> field specify a CSV list or a list of address objects or address groups that you want to add to the exclusion member list.</li>
                    <li>In the <strong>Remove Exclude Member</strong> field specify a CSV list or a list of address objects or address groups that you want to remove from the exclusion member list.</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Comment</td>
            <td>(Optional) Specify a comment to be added to the address group that you want to update.</td>
        </tr>
        <tr>
            <td>Additional Address Group Arguments</td>
            <td>(Optional) Specify additional arguments, in JSON format, to be added during the updation of the address group. You can enter the arguments in the following format: <code>{&quot;field1&quot;:value1, &quot;field2&quot;:value2}</code></td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "url": "",
            "data": {
                "name": ""
            },
            "status": {
                "code": "",
                "message": ""
            }
        }
    ]
}</pre>

<h3>operation: Delete Address Group</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Level Type</td>
            <td>Select the level type at which you want to delete the address group. You can select from following options:
                <ul>
                    <li><strong>ADOM</strong>: Specify the following parameters:
                        <ul>
                            <li><strong>ADOM</strong>: Administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified as a configuration parameter.</li>
                            <li><strong>Address Group</strong>: Valid Address Group Name to delete in Fortinet FortiManager.</li>
                        </ul>
                    </li>
                    <li><strong>Global</strong>: Specify values in the following fields:
                        <ul>
                            <li><strong>Address Group</strong>: Valid Address Group Name to delete in Fortinet FortiManager.</li>
                        </ul>
                    </li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "url": "",
            "status": {
                "code": "",
                "message": ""
            }
        }
    ]
}</pre>

<h3>operation: Get Service Categories List</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Level Type</td>
            <td>Select the level type at which you want to retrieve the service categories details. You can select from following options:
                <ul>
                    <li><strong>ADOM</strong>: Specify the following parameters:
                        <ul>
                            <li><strong>ADOM</strong>: Administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified as a configuration parameter.</li>
                            <li><strong>Service Category Name</strong>: Valid service category name based on which you want to retrieve details of category from Fortinet FortiManager.
                                <p><strong>Note</strong>: If this parameter is left blank or <code>null</code>, this operation returns service categories matching all values.</p>
                            </li>
                        </ul>
                    </li>
                    <li><strong>Global</strong>: Specify values in the following fields:
                        <ul>
                            <li><strong>Service Category Name</strong>: Valid service category name based on which you want to retrieve details of category from Fortinet FortiManager.
                                <p><strong>Note</strong>: If this parameter is left blank or <code>null</code>, this operation returns service categories matching all values.</p>
                            </li>
                        </ul>
                    </li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Attributes in Result</td>
            <td>(Optional) Specify a string array to limit the output by returning only the specified attributes. For example,<code>[&quot;comment&quot;, &quot;fabric-object&quot;, &quot;name&quot;]</code><br />
                <strong>Note</strong>: If attributes are not specified, then all attributes will be returned.
            </td>
        </tr>
        <tr>
            <td>Filter By</td>
            <td>(Optional) Specify attributes to filter the results according to a set criteria.
        </tr>
        <tr>
            <td>Limit</td>
            <td>(Optional) Specify the maximum number of results that this operation should return.</td>
        </tr>
        <tr>
            <td>Offset</td>
            <td>(Optional) Specify the offset value to retrieve a subset of records that starts from the offset value. The offset works with the <em>Limit</em> parameter, which determines how many records to retrieve starting from the offset. Values supported are:
                <ul>
                    <li><strong>Default:<code>&quot;0&quot;</code></strong></li>
                    <li><strong>Minimum:<code>&quot;0&quot;</code></strong></li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Sort By</td>
            <td>Select <em>Field</em> as the sorting criteria to order the results and specify values in the following fields:
                <ul>
                    <li><strong>Field</strong>: Specify the name of the field on which to sort the results. For example, <code>comment, fabric-object, name</code></li>
                    <li><strong>Order</strong>: Select the order in which to sort the results. You can select from following options:
                        <ul>
                            <li>Ascending (default)</li>
                            <li>Descending</li>
                        </ul>
                    </li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "url": "",
            "data": [
                {
                    "name": "",
                    "comment": "",
                    "obj seq": "",
                    "fabric-object": ""
                }
            ],
            "status": {
                "code": "",
                "message": ""
            }
        }
    ]
}</pre>

<h3>operation: Create Service Group</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Level Type</td>
            <td>Select the level type at which you want to create the service group. You can select from following options:
                <ul>
                    <li><strong>ADOM</strong>: Specify the following parameters:
                        <ul>
                            <li><strong>ADOM</strong>: Administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified as a configuration parameter.</li>
                            <li><strong>Service Group</strong>: Valid Service group to create in Fortinet FortiManager.</li>
                        </ul>
                    </li>
                    <li><strong>Global</strong>: Specify values in the following fields:
                        <ul>
                            <li><strong>Service Group</strong>: Valid Service group to create in Fortinet FortiManager.</li>
                        </ul>
                    </li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Member</td>
            <td>Specify a CSV list or a list of service objects that you want to add to the service group that you want to create in Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Proxy</td>
            <td>Select <strong>Enable </strong>to enable the web proxy service group or <strong>Disable</strong>to disable the web proxy service group.</td>
        </tr>
        <tr>
            <td>Comment</td>
            <td>(Optional) Specify a comment to be added to the service group that you want to create.</td>
        </tr>
        <tr>
            <td>Additional Service Group Arguments</td>
            <td>(Optional) Specify additional arguments, in JSON format, to be added during the creation of the service group. You can enter the arguments in the following format: <code>{&quot;field1&quot;:value1, &quot;field2&quot;:value2}</code></td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "url": "",
            "data": {
                "name": ""
            },
            "status": {
                "code": "",
                "message": ""
            }
        }
    ]
}</pre>

<h3>operation: Get Service Groups List</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Level Type</td>
            <td>Select the level type at which you want to retrieve the service group details. You can select from following options:
                <ul>
                    <li><strong>ADOM</strong>: Specify the following parameters:
                        <ul>
                            <li><strong>ADOM</strong>: Administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified as a configuration parameter.</li>
                            <li><strong>Service Group</strong>: Valid service group based on which you want to retrieve details of service group from Fortinet FortiManager.
                                <p><strong>Note</strong>: If this parameter is left blank or <code>null</code>, this operation returns service group matching all values.</p>
                            </li>
                        </ul>
                    </li>
                    <li><strong>Global</strong>: Specify values in the following fields:
                        <ul>
                            <li><strong>Service Group</strong>: Valid service group based on which you want to retrieve details of service group from Fortinet FortiManager
                                <p><strong>NOTE</strong>: If this parameter is left blank or <code>null</code>, this operation returns service group matching all values.</p>
                            </li>
                        </ul>
                    </li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Attributes in Result</td>
            <td>(Optional) Specify a string array to limit the output by returning only the specified attributes. For example, <code>[&quot;color&quot;, &quot;comment&quot;, &quot;fabric-objec&quot;t, &quot;member&quot;, &quot;name&quot;, &quot;proxy&quot;]&nbsp;</code><br />
                <strong>NOTE</strong>: If attributes are not specified, then all attributes are returned.
            </td>
        </tr>
        <tr>
            <td>Filter By</td>
            <td>(Optional) Specify attributes to filter the results according to a set criteria.
        </tr>
        <tr>
            <td>Limit</td>
            <td>(Optional) Specify the maximum number of results that this operation should return.</td>
        </tr>
        <tr>
            <td>Offset</td>
            <td>(Optional) Specify the offset value to retrieve a subset of records that starts from the offset value. The offset works with the <em>Limit</em> parameter, which determines how many records to retrieve starting from the offset. Values supported are:
                <ul>
                    <li><strong>Default:<code>&quot;0&quot;</code></strong></li>
                    <li><strong>Minimum:<code>&quot;0&quot;</code></strong></li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Sort By</td>
            <td>Select <em>Field</em> as the sorting criteria to order the results and specify values in the following fields:
                <ul>
                    <li><strong>Field</strong>: Specify the name of the field on which you want to sort the result. For example, color, comment, fabric-object, member, name, proxy</li>
                    <li><strong>Order</strong>: Select the order in which to sort the results. You can select from following options:
                        <ul>
                            <li>Ascending (default)</li>
                            <li>Descending</li>
                        </ul>
                    </li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "url": "",
            "data": [
                {
                    "name": "",
                    "member": [],
                    "global-object": ""
                }
            ],
            "status": {
                "code": "",
                "message": ""
            }
        }
    ]
}</pre>

<h3>operation: Update Service Group</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Level Type</td>
            <td>Select the level type at which you want to update the service group. You can select from following options:
                <ul>
                    <li><strong>ADOM</strong>: Specify the following parameters:
                        <ul>
                            <li><strong>ADOM</strong>: Administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified as a configuration parameter.</li>
                            <li><strong>Service Group</strong>: Valid Service group to update in Fortinet FortiManager.</li>
                        </ul>
                    </li>
                    <li><strong>Global</strong>: Specify values in the following fields:
                        <ul>
                            <li><strong>Service Group</strong>: Valid Service group to update in Fortinet FortiManager.</li>
                        </ul>
                    </li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Method</td>
            <td>Select the action that you want to perform on members of the service group. You can select from following options:
                <ul>
                    <li><strong>Add</strong>: In the <strong>Add Member</strong> field, specify a CSV list or a list of service group objects that you want to add to the service group that you want to update in Fortinet FortiManager.</li>
                    <li><strong>Remove</strong>: In the <strong>Remove Member</strong> field, specify a CSV list or a list of service group objects that you want to remove from the service group that you want to update in Fortinet FortiManager.</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Proxy</td>
            <td>Select <strong>Enable </strong>to enable the web proxy service group or <strong>Disable</strong>to disable the web proxy service group.</td>
        </tr>
        <tr>
            <td>Comment</td>
            <td>(Optional) Specify a comment to be added to the service group that you want to update.</td>
        </tr>
        <tr>
            <td>Additional Service Group Arguments</td>
            <td>(Optional) Specify additional arguments, in JSON format, to be added while updating the service group. You can enter the arguments in the following format: <code>{&quot;field1&quot;:value1, &quot;field2&quot;:value2}</code></td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "url": "",
            "data": {
                "name": ""
            },
            "status": {
                "code": "",
                "message": ""
            }
        }
    ]
}</pre>

<h3>operation: Delete Service Group</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Level Type</td>
            <td>Select the level type at which you want to delete the service group. You can select from following options:
                <ul>
                    <li><strong>ADOM</strong>: Specify the following parameters:
                        <ul>
                            <li><strong>ADOM</strong>: Administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified as a configuration parameter.</li>
                            <li><strong>Service Group</strong>: Valid Service group to delete in Fortinet FortiManager.</li>
                        </ul>
                    </li>
                    <li><strong>Global</strong>: Specify values in the following fields:
                        <ul>
                            <li><strong>Service Group</strong>: Valid Service group to delete in Fortinet FortiManager.</li>
                        </ul>
                    </li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "url": "",
            "status": {
                "code": "",
                "message": ""
            }
        }
    ]
}</pre>

<h3>operation: Create Custom Service</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Level Type</td>
            <td>Select the level type at which to create the custom service. You can select from following options:
                <ul>
                    <li><strong>ADOM</strong>: Specify the following parameters:
                        <ul>
                            <li><strong>ADOM</strong>: Administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified as a configuration parameter.</li>
                            <li><strong>Custom Service Name</strong>: Valid custom service name to create in Fortinet FortiManager.</li>
                        </ul>
                    </li>
                    <li><strong>Global</strong>: Specify values in the following fields:
                        <ul>
                            <li><strong>Custom Service Name</strong>: Valid custom service name to create in Fortinet FortiManager.</li>
                        </ul>
                    </li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Service Category</td>
            <td>(Optional) Specify the ID of the custom service category that you want to create in Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Proxy</td>
            <td>Select one of the following options for the web proxy service:
                <ul>
                    <li><strong>Enable</strong>: Select to enable the web proxy service and specify the following parameters:
                        <ul>
                            <li><strong>Protocol</strong>: (Optional) Select the protocol type based on IANA numbers for the custom service that you want to create in Fortinet FortiManager. You can select from the following protocols:
                                <ul>
                                    <li>ALL</li>
                                    <li>CONNECT</li>
                                    <li>FTP</li>
                                    <li>HTTP</li>
                                    <li>SOCKS-TCP</li>
                                    <li>SOCKS-UDP</li>
                                </ul>
                                <p>For <strong>ALL</strong>, <strong>CONNECT</strong>, <strong>FTP</strong>, <strong>HTTP</strong>, and <strong>SOCKS-TCP</strong>, specify TCP port ranges in the <strong>TCP Port Range</strong> field. For example,<code>0-64535:0-65535</code></p>
                                <p>For <strong>SOCKS-UDP</strong>, specify UDP port ranges in the <strong>UDP Port Range</strong> field. For example,<code>0-64535:0-65535</code></p>
                            </li>
                        </ul>
                    </li>
                    <li><strong>Disable</strong>: Select to disable the web proxy service and specify the following parameters:
                        <ul>
                            <li><strong>Protocol</strong>: (Optional) Select the protocol type based on IANA numbers for the custom service that you want to create in Fortinet FortiManager. You can select from the following protocols:
                                <ul>
                                    <li><strong>TCP/UDP/SCTP</strong>: Select the protocol, to apply to the custom service, in the <strong>Protocol</strong> field. You can select one or more values from the following options:
                                        <ul>
                                            <li><strong>TCP</strong>: Specify TCP port ranges in the <strong>TCP Port Range</strong> field.</li>
                                            <li><strong>UDP</strong>: Specify UDP port ranges in the <strong>UDP Port Range</strong> field.</li>
                                            <li><strong>SCTP</strong>: Specify SCTP port ranges in the <strong>SCTP Port Range</strong> field.</li>
                                            <li><strong>IP/FQDN</strong>: Select the method to reach the service. You can select from the following options:
                                                <ul>
                                                    <li><strong>IP</strong>: Specify an IP address or an IP address range in the <strong>IP (Range)</strong> field.</li>
                                                    <li><strong>FQDN</strong>: Specify a fully qualified domain name (FQDN) in the <strong>FQDN</strong> field.</li>
                                                </ul>
                                            </li>
                                        </ul>
                                    </li>
                                    <li>ICMP</li>
                                    <li>ICMP6</li>
                                    <p>If you select <strong><em>ICMP</em></strong> or <strong><em>ICMP6</em></strong>, specify the following parameters:</p>
                                        <ul>
                                            <li>In the <strong>ICMP Code</strong> field, specify the ICMP code for the custom service that you want to create in Fortinet FortiManager.</li>
                                            <li>In the <strong>ICMP Type</strong> field, specify the ICMP type for the custom service that you want to create in Fortinet FortiManager.</li>
                                        </ul>
                                    <li><strong>IP</strong>: Specify values in the following fields:
                                        <ul>
                                            <li><strong>Protocol Number</strong>: Specify the IP protocol number for the custom service that you want to create in Fortinet FortiManager.</li>
                                            <li><strong>ICMP Type</strong>: Specify the ICMP type for the custom service that you want to create in Fortinet FortiManager.</li>
                                        </ul>
                                    </li>
                                </ul>
                            </li>
                        </ul>
                    </li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>App Category</td>
            <td>(Optional) Specify the ID of the application category for the custom service that you want to create in Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>App Service Type</td>
            <td>Select the type of application service type for the custom service that you want to create in Fortinet FortiManager. You can select from following options:
                <ul>
                    <li>Disable (default)</li>
                    <li>App ID</li>
                    <li>App Category</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Application ID</td>
            <td>(Optional) Specify the ID of the application for the custom service that you want to create in Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>ICMP Error Message</td>
            <td>Select the type of ICMP error message verification for the custom service that you want to create in Fortinet FortiManager. You can select from folowing options:
                <ul>
                    <li>Disable</li>
                    <li>Default</li>
                    <li>Strict</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Helper Name</td>
            <td>(Optional) Specify the helper name for the custom service that you want to create in Fortinet FortiManager. You can specify the following values: <code>disable, auto, ftp, tftp, ras, h323, tns, mms, sip, pptp, rtsp, dns-udp, dns-tcp, pmap, rsh, dcerpc, mgcp, gtp-c, gtp-u, gtp-b, pfcp</code></td>
        </tr>
        <tr>
            <td>Session TTL</td>
            <td>(Optional) Specify the TTL for the session, between <code>5</code> - <code>300</code> seconds, associated with the custom service that you want to create in Fortinet FortiManager. Default is <code>0</code>.</td>
        </tr>
        <tr>
            <td>TCP Halfclose Timer</td>
            <td>(Optional) Specify the wait time to close a TCP session waiting for an unanswered FIN packet, between <code>5</code> - <code>300</code> seconds, for the custom service that you want to create in Fortinet FortiManager. Default is <code>0</code>.</td>
        </tr>
        <tr>
            <td>TCP Halfopen Timer</td>
            <td>(Optional) Specify the wait time to open a TCP session waiting for an unanswered open session packet, between <code>5</code> - <code>300</code> seconds, for the custom service that you want to create in Fortinet FortiManager. Default is <code>0</code>.</td>
        </tr>
        <tr>
            <td>TCP Rst Timer</td>
            <td>(Optional) Specify the length of the TCP CLOSE state in seconds, between <code>5</code> - <code>300</code> seconds, for the custom service that you want to create in Fortinet FortiManager. Default is <code>0</code>.</td>
        </tr>
        <tr>
            <td>TCP Time-Wait Timer</td>
            <td>(Optional) Specify the length of the TCP TIME-WAIT state in seconds, between <code>1</code> - <code>300</code> seconds, for the custom service that you want to create in Fortinet FortiManager. Default is <code>0</code>.</td>
        </tr>
        <tr>
            <td>UDP Idle Timer</td>
            <td>(Optional) Specify UDP half-close timeout in seconds, between <code>1</code> - <code>86400</code> seconds,  the custom service that you want to create in Fortinet FortiManager. Default is <code>0</code>.</td>
        </tr>
        <tr>
            <td>Comment</td>
            <td>(Optional) Specify the comment to be added to the custom service that you want to create.</td>
        </tr>
        <tr>
            <td>Additional Custom Service Arguments</td>
            <td>(Optional) Specify additional arguments, in JSON format, to be added during the creation of the custom service. You can enter the arguments in the following format: <code>{&quot;field1&quot;:value1, &quot;field2&quot;:value2}</code></td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "url": "",
            "data": {
                "name": ""
            },
            "status": {
                "code": "",
                "message": ""
            }
        }
    ]
}</pre>

<h3>operation: Get Custom Services List</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Level Type</td>
            <td>Select the level type from which to retrieve the custom service details. You can select from following options:
                <ul>
                    <li><strong>ADOM</strong>: Specify the following parameters:
                        <ul>
                            <li><strong>ADOM</strong>: Administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified as a configuration parameter.</li>
                            <li><strong>Custom Service Name</strong>: Specify a valid Custom Service name based on which you want to retrieve custom service details from Fortinet FortiManager.
                                <p><strong>NOTE</strong>: If this parameter is left blank or <code>null</code>, this operation returns custom services matching all values.</p>
                            </li>
                        </ul>
                    </li>
                    <li><strong>Global</strong>: Specify values in the following fields:
                        <ul>
                            <li><strong>Custom Service Name</strong>: Specify a valid custom service name based on which you want to retrieve custom service details from Fortinet FortiManager.
                                <p><strong>NOTE</strong>: If this parameter is left blank or <code>null</code>, this operation returns custom services matching all values.</p>
                            </li>
                        </ul>
                    </li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Attributes in Result</td>
            <td>(Optional) Specify a string array to limit the output by returning only the specified attributes. For example, <code>[&quot;app-category&quot;, &quot;app-service-type&quot;, &quot;application&quot;, &quot;category&quot;, &quot;check-reset-range&quot;, &quot;color&quot;, &quot;comment&quot;, &quot;fabric-object&quot;, &quot;fqdn&quot;, &quot;helper&quot;, &quot;icmpcode&quot;, &quot;icmptype&quot;, &quot;iprange&quot;, &quot;name&quot;, &quot;protocol&quot;, &quot;protocol-number&quot;, &quot;proxy&quot;, &quot;sctp-portrange&quot;, &quot;session-ttl&quot;, &quot;tcp-halfclose-timer&quot;, &quot;tcp-halfopen-timer&quot;, &quot;tcp-portrange&quot;, &quot;tcp-rst-timer&quot;, &quot;tcp-timewait-timer&quot;, &quot;udp-idle-timer&quot;, &quot;udp-portrange&quot;, &quot;visibility&quot;]&nbsp;</code><br />
                <strong>Note</strong>: If attributes are not specified, then all attributes will be returned.
            </td>
        </tr>
        <tr>
            <td>Filter By</td>
            <td>(Optional) Specify attributes to filter the results according to a set criteria.
        </tr>
        <tr>
            <td>Limit</td>
            <td>(Optional) Specify the maximum number of results that this operation should return.</td>
        </tr>
        <tr>
            <td>Offset</td>
            <td>(Optional) Specify the offset value to retrieve a subset of records that starts from the offset value. The offset works with the <em>Limit</em> parameter, which determines how many records to retrieve starting from the offset. Values supported are:
                <ul>
                    <li><strong>Default:<code>&quot;0&quot;</code></strong></li>
                    <li><strong>Minimum:<code>&quot;0&quot;</code></strong></li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Sort By</td>
            <td>Select <em>Field</em> as the sorting criteria to order the results and specify values in the following fields:
                <ul>
                    <li><strong>Field</strong>: Specify the name of the field on which to sort the results. For example, <code>color, comment, fabric-object, member, name, proxy</code>.</li>
                    <li><strong>Order</strong>: Select the order in which to sort the results. You can select from following options:
                        <ul>
                            <li>Ascending (default)</li>
                            <li>Descending</li>
                        </ul>
                    </li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "url": "",
            "data": [
                {
                    "name": "",
                    "color": "",
                    "proxy": "",
                    "helper": "",
                    "iprange": "",
                    "obj seq": "",
                    "category": [],
                    "protocol": "",
                    "visibility": "",
                    "application": [],
                    "app-category": [],
                    "fabric-object": "",
                    "tcp-rst-timer": "",
                    "udp-portrange": [],
                    "protocol-number": "",
                    "app-service-type": ""
                }
            ],
            "status": {
                "code": "",
                "message": ""
            }
        }
    ]
}</pre>

<h3>operation: Update Custom Service</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Level Type</td>
            <td>Select the level type from which to update the custom service details. You can select from following options:
                <ul>
                    <li><strong>ADOM</strong>: Specify the following parameters:
                        <ul>
                            <li><strong>ADOM</strong>: Administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified as a configuration parameter.</li>
                            <li><strong>Custom Service Name</strong>: Specify a valid custom Service name to update its details in Fortinet FortiManager.</li>
                        </ul>
                    </li>
                    <li><strong>Global</strong>: Specify values in the following fields:
                        <ul>
                            <li><strong>Custom Service Name</strong>: Specify a valid custom Service name to update its details in Fortinet FortiManager.</li>
                        </ul>
                    </li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Service Category</td>
            <td>(Optional) Specify the ID of the category of the custom service that you want to update in Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Proxy</td>
            <td>Select one of the following options for the web proxy service:
                <ul>
                    <li><strong>Enable</strong>: Select to enable the web proxy service and specify the following parameters:
                        <ul>
                            <li><strong>Protocol</strong>: (Optional) Select the protocol type based on IANA numbers for the custom service that you want to update in Fortinet FortiManager. You can select from the following protocols:
                                <ul>
                                    <li>ALL</li>
                                    <li>CONNECT</li>
                                    <li>FTP</li>
                                    <li>HTTP</li>
                                    <li>SOCKS-TCP</li>
                                    <li>SOCKS-UDP</li>
                                </ul>
                                <p>For <strong>ALL</strong>, <strong>CONNECT</strong>, <strong>FTP</strong>, <strong>HTTP</strong>, and <strong>SOCKS-TCP</strong>, specify TCP port ranges in the <strong>TCP Port Range</strong> field. For example,<code>0-64535:0-65535</code></p>
                                <p>For <strong>SOCKS-UDP</strong>, specify UDP port ranges in the <strong>UDP Port Range</strong> field. For example,<code>0-64535:0-65535</code></p>
                            </li>
                        </ul>
                    </li>
                    <li><strong>Disable</strong>: Select to disable the web proxy service and specify the following parameters:
                        <ul>
                            <li><strong>Protocol</strong>: (Optional) Select the protocol type based on IANA numbers for the custom service that you want to update in Fortinet FortiManager. You can select from the following protocols:
                                <ul>
                                    <li><strong>TCP/UDP/SCTP</strong>: Select the protocol, to apply to the custom service, in the <strong>Protocol</strong> field. You can select one or more values from the following options:
                                        <ul>
                                            <li><strong>TCP</strong>: Specify TCP port ranges in the <strong>TCP Port Range</strong> field.</li>
                                            <li><strong>UDP</strong>: Specify UDP port ranges in the <strong>UDP Port Range</strong> field.</li>
                                            <li><strong>SCTP</strong>: Specify SCTP port ranges in the <strong>SCTP Port Range</strong> field.</li>
                                            <li><strong>IP/FQDN</strong>: Select the method to reach the service. You can select from the following options:
                                                <ul>
                                                    <li><strong>IP</strong>: Specify an IP address or an IP address range in the <strong>IP (Range)</strong> field.</li>
                                                    <li><strong>FQDN</strong>: Specify a fully qualified domain name (FQDN) in the <strong>FQDN</strong> field.</li>
                                                </ul>
                                            </li>
                                        </ul>
                                    </li>
                                    <li>ICMP</li>
                                    <li>ICMP6</li>
                                    <p>If you select <strong><em>ICMP</em></strong> or <strong><em>ICMP6</em></strong>, specify the following parameters:</p>
                                        <ul>
                                            <li>In the <strong>ICMP Code</strong> field, specify the ICMP code for the custom service that you want to update in Fortinet FortiManager.</li>
                                            <li>In the <strong>ICMP Type</strong> field, specify the ICMP type for the custom service that you want to update in Fortinet FortiManager.</li>
                                        </ul>
                                    <li><strong>IP</strong>: Specify values in the following fields:
                                        <ul>
                                            <li><strong>Protocol Number</strong>: Specify the IP protocol number for the custom service that you want to update in Fortinet FortiManager.</li>
                                            <li><strong>ICMP Type</strong>: Specify the ICMP type for the custom service that you want to update in Fortinet FortiManager.</li>
                                        </ul>
                                    </li>
                                </ul>
                            </li>
                        </ul>
                    </li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>App Category</td>
            <td>(Optional) Specify the ID of the application category for the custom service that you want to update in Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>App Service Type</td>
            <td>Select the type of application service type for the custom service that you want to update in Fortinet FortiManager. You can select from following options:
                <ul>
                    <li>Disable (default)</li>
                    <li>App ID</li>
                    <li>App Category</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Application ID</td>
            <td>(Optional) Specify the ID of the application for the custom service that you want to update in Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>ICMP Error Message</td>
            <td>Select the type of ICMP error message verification for the custom service that you want to update in Fortinet FortiManager. You can select from folowing options:
                <ul>
                    <li>Disable</li>
                    <li>Default</li>
                    <li>Strict</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Helper Name</td>
            <td>(Optional) Specify the helper name for the custom service that you want to update in Fortinet FortiManager. You can specify the following values: <code>disable, auto, ftp, tftp, ras, h323, tns, mms, sip, pptp, rtsp, dns-udp, dns-tcp, pmap, rsh, dcerpc, mgcp, gtp-c, gtp-u, gtp-b, pfcp</code></td>
        </tr>
        <tr>
            <td>Session TTL</td>
            <td>(Optional) Specify the TTL for the session, between <code>5</code> - <code>300</code> seconds, associated with the custom service that you want to update in Fortinet FortiManager. Default is <code>0</code>.</td>
        </tr>
        <tr>
            <td>TCP Halfclose Timer</td>
            <td>(Optional) Specify the wait time to close a TCP session waiting for an unanswered FIN packet, between <code>5</code> - <code>300</code> seconds, for the custom service that you want to update in Fortinet FortiManager. Default is <code>0</code>.</td>
        </tr>
        <tr>
            <td>TCP Halfopen Timer</td>
            <td>(Optional) Specify the wait time to open a TCP session waiting for an unanswered open session packet, between <code>5</code> - <code>300</code> seconds, for the custom service that you want to update in Fortinet FortiManager. Default is <code>0</code>.</td>
        </tr>
        <tr>
            <td>TCP Rst Timer</td>
            <td>(Optional) Specify the length of the TCP CLOSE state in seconds, between <code>5</code> - <code>300</code> seconds, for the custom service that you want to update in Fortinet FortiManager. Default is <code>0</code>.</td>
        </tr>
        <tr>
            <td>TCP Time-Wait Timer</td>
            <td>(Optional) Specify the length of the TCP TIME-WAIT state in seconds, between <code>1</code> - <code>300</code> seconds, for the custom service that you want to update in Fortinet FortiManager. Default is <code>0</code>.</td>
        </tr>
        <tr>
            <td>UDP Idle Timer</td>
            <td>(Optional) Specify UDP half-close timeout in seconds, between <code>1</code> - <code>86400</code> seconds,  the custom service that you want to update in Fortinet FortiManager. Default is <code>0</code>.</td>
        </tr>
        <tr>
            <td>Comment</td>
            <td>(Optional) Specify the comment to be added to the custom service that you want to update.</td>
        </tr>
        <tr>
            <td>Additional Custom Service Arguments</td>
            <td>(Optional) Specify additional arguments, in JSON format, to be added during the updation of the custom service. You can enter the arguments in the following format: <code>{&quot;field1&quot;:value1, &quot;field2&quot;:value2}</code></td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "url": "",
            "data": {
                "name": ""
            },
            "status": {
                "code": "",
                "message": ""
            }
        }
    ]
}</pre>

<h3>operation: Delete Custom Service</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Level Type</td>
            <td>Select the level type from which to delete the custom service details. You can select from following options:
                <ul>
                    <li><strong>ADOM</strong>: Specify the following parameters:
                        <ul>
                            <li><strong>ADOM</strong>: Administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified as a configuration parameter.</li>
                            <li><strong>Custom Service Name</strong>: Specify a valid custom Service name to delete it from Fortinet FortiManager.</li>
                        </ul>
                    </li>
                    <li><strong>Global</strong>: Specify values in the following fields:
                        <ul>
                            <li><strong>Custom Service Name</strong>: Specify a valid custom Service name to delete it from Fortinet FortiManager.</li>
                        </ul>
                    </li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "url": "",
            "status": {
                "code": "",
                "message": ""
            }
        }
    ]
}</pre>

<h3>operation: Create Policy Package</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Level Type</td>
            <td>Select the level type at which to create the policy package details. You can select from following options:
                <ul>
                    <li><strong>ADOM</strong>: Specify the Administrative domain name (ADOM) of the Fortinet FortiManager server, in the <strong>ADOM</strong> field. The ADOM that you specify here overwrites the ADOM that you have specified as a configuration parameter.</li>
                    <li><strong>Global</strong>: Select this option to create the policy package at the global level.</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Package Type</td>
            <td>Select the type of package for the policy package that you want to create in Fortinet FortiManager. You can select from the following options:
                <ul>
                    <li><strong>Package</strong>: Specify values in the following fields:
                        <ul>
                            <li><strong>Policy Package Name</strong>: Specify a valid policy package name that you want to create in Fortinet FortiManager.</li>
                            <li><strong>NGFW Mode</strong>: Select the NGFW mode for the policy package that you want to create in Fortinet FortiManager. You can select from following options:
                                <ul>
                                    <li><strong>Profile-based</strong>: Select if you want to <strong>Enable</strong> or <strong>Disable</strong> the central NAT for the policy package that you want to create in Fortinet FortiManager.</li>
                                    <li><strong>Policy-based</strong>: You cannot select <strong>Disable</strong> for the central NAT for the policy package as it is enabled by default.</li>
                                </ul>
                            </li>
                            <li><strong>Policy Offload Level</strong>: Select the policy offload level at which you want to create the policy package on Fortinet FortiManager. You can select from followin options:
                                <ul>
                                    <li>Disable</li>
                                    <li>Default</li>
                                    <li>DoS Offload</li>
                                    <li>Full Offload</li>
                                </ul>
                            </li>
                            <li><strong>Consolidated Firewall Mode</strong>: Select if you want to <strong>Enable</strong> or <strong>Disable</strong> the consolidated firewall mode for the policy package that you want to create in Fortinet FortiManager.</li>
                            <li><strong>Firewall Policy Implicit Log</strong>: Select if you want to <strong>Enable</strong> or <strong>Disable</strong> the firewall policy implicit log for the policy package that you want to create in Fortinet FortiManager.</li>
                            <li><strong>Firewall Policy6 Implicit Log</strong>: Select if you want to <strong>Enable</strong> or <strong>Disable</strong> the firewall policy6 implicit log for the policy package that you want to create in Fortinet FortiManager.</li>
                            <li><strong>Inspection Mode</strong>: Select the inspection mode for the policy package that you want to create in Fortinet FortiManager. You can select from following options:
                                <ul>
                                    <li>Proxy</li>
                                    <li>Flow</li>
                                </ul>
                            </li>
                            <li><strong>SSL SSH Profile</strong>: Specify the SSL SSH Profile for the policy package that you want to create in Fortinet FortiManager.</li>
                        </ul>
                    </li>
                    <li><strong>Folder</strong>: Specify the valid policy package folder name, in the <strong>Policy Package Folder Name</strong> field, that you want to create in Fortinet FortiManager.</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Additional Policy Package Arguments</td>
            <td>(Optional) Specify additional arguments, in JSON format, to be added during the creation of the policy package. You can enter the arguments in the following format:<code> {&quot;field1&quot;:value1, &quot;field2&quot;:value2}</code></td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "url": "",
            "status": {
                "code": "",
                "message": ""
            }
        }
    ]
}</pre>

<h3>operation: Update Policy Package</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Level Type</td>
            <td>Select the level type at which to update the policy package details. You can select from following options:
                <ul>
                    <li><strong>ADOM</strong>: Specify the following parameters:
                        <ul>
                            <li><strong>ADOM</strong>: Administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified as a configuration parameter.</li>
                            <li><strong>Policy Package Name</strong>: Specify a valid policy package name to update in Fortinet FortiManager.</li>
                        </ul>
                    </li>
                    <li><strong>Global</strong>: Specify values in the following fields:
                        <ul>
                            <li><strong>Policy Package Name</strong>: Specify a valid policy package name to update in Fortinet FortiManager.</li>
                        </ul>
                    </li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Package Type</td>
            <td>Select the type of package for the policy package that you want to update in Fortinet FortiManager. You can select from the following options:
                <ul>
                    <li><strong>Package</strong>: Specify values in the following fields:
                        <ul>
                            <li><strong>Policy Package Name</strong>: Specify a valid policy package name that you want to update in Fortinet FortiManager.</li>
                            <li><strong>NGFW Mode</strong>: Select the NGFW mode for the policy package that you want to update in Fortinet FortiManager. You can select from following options:
                                <ul>
                                    <li><strong>Profile-based</strong>: Select if you want to <strong>Enable</strong> or <strong>Disable</strong> the central NAT for the policy package that you want to update in Fortinet FortiManager.</li>
                                    <li><strong>Policy-based</strong>: You cannot select <strong>Disable</strong> for the central NAT for the policy package as it is enabled by default.</li>
                                </ul>
                            </li>
                            <li><strong>Policy Offload Level</strong>: Select the policy offload level at which you want to update the policy package on Fortinet FortiManager. You can select from followin options:
                                <ul>
                                    <li>Disable</li>
                                    <li>Default</li>
                                    <li>DoS Offload</li>
                                    <li>Full Offload</li>
                                </ul>
                            </li>
                            <li><strong>Consolidated Firewall Mode</strong>: Select if you want to <strong>Enable</strong> or <strong>Disable</strong> the consolidated firewall mode for the policy package that you want to update in Fortinet FortiManager.</li>
                            <li><strong>Firewall Policy Implicit Log</strong>: Select if you want to <strong>Enable</strong> or <strong>Disable</strong> the firewall policy implicit log for the policy package that you want to update in Fortinet FortiManager.</li>
                            <li><strong>Firewall Policy6 Implicit Log</strong>: Select if you want to <strong>Enable</strong> or <strong>Disable</strong> the firewall policy6 implicit log for the policy package that you want to update in Fortinet FortiManager.</li>
                            <li><strong>Inspection Mode</strong>: Select the inspection mode for the policy package that you want to update in Fortinet FortiManager. You can select from following options:
                                <ul>
                                    <li>Proxy</li>
                                    <li>Flow</li>
                                </ul>
                            </li>
                            <li><strong>SSL SSH Profile</strong>: Specify the SSL SSH Profile for the policy package that you want to update in Fortinet FortiManager.</li>
                        </ul>
                    </li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Additional Policy Package Arguments</td>
            <td>(Optional) Specify additional arguments, in JSON format, to be added during the updation of the policy package. You can enter the arguments in the following format:<code> {&quot;field1&quot;:value1, &quot;field2&quot;:value2}</code></td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "url": "",
            "status": {
                "code": "",
                "message": ""
            }
        }
    ]
}</pre>

<h3>operation: Delete Policy Package</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Level Type</td>
            <td>Select the level type at which to delete the policy package details. You can select from following options:
                <ul>
                    <li><strong>ADOM</strong>: Specify the following parameters:
                        <ul>
                            <li><strong>ADOM</strong>: Administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified as a configuration parameter.</li>
                            <li><strong>Policy Package Name</strong>: Specify a valid policy package name to delete in Fortinet FortiManager.</li>
                        </ul>
                    </li>
                    <li><strong>Global</strong>: Specify values in the following fields:
                        <ul>
                            <li><strong>Policy Package Name</strong>: Specify a valid policy package name to delete in Fortinet FortiManager.</li>
                        </ul>
                    </li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Policy Package Path</td>
            <td>(Optional) Specify a valid path for the policy package you want to delete from Fortinet FortiManager.</td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "url": "",
            "status": {
                "code": "",
                "message": ""
            }
        }
    ]
}</pre>

<h3>operation: Create Firewall Policy</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Level Type</td>
            <td>Select the level type at which to create the firewall policy. You can select from following options:
                <ul>
                    <li><strong>ADOM</strong>: Specify the following parameters:
                        <ul>
                            <li><strong>ADOM</strong>: Administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified as a configuration parameter.</li>
                        </ul>
                    </li>
                    <li><strong>Global</strong>: Specify values in the following fields:
                        <ul>
                            <li><strong>Policy Type</strong>: Specify a valid firewall policy type to create in Fortinet FortiManager.</li>
                        </ul>
                    </li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>NGFW Mode</td>
            <td>Select the NGFW mode of the policy package. You can select from following options:
                <ul>
                    <li>Policy Based</li>
                    <li><strong>Profile Based</strong>: Specify values in the followin fields:
                        <ul>
                            <li><strong>Inspection Mode</strong>: Select the Inspection mode for the firewall policy that you want to create in Fortinet FortiManager. You can select from following fields:
                                <ul>
                                    <li>Proxy</li>
                                    <li>Flow (default)</li>
                                </ul>
                            </li>
                            <li><strong>Schedule Timeout</strong>: Select one of the following:
                                <ul>
                                    <li><strong>Enable</strong>: Select to forcefully end currently running sessions when the schedule object times out.</li>
                                    <li><strong>Disable</strong>: Select to allow sessions to end from inactivity.</li>
                                </ul>
                            </li>
                        </ul>
                    </li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Policy Package Name</td>
            <td>Specify a valid policy package name for the firewall policy you want to create in Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Policy Name</td>
            <td>Valid name of the policy name that you want to create in Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Source Interface</td>
            <td>Specify the Incoming (ingress) interface for the firewall policy you want to create in Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Destination Interface</td>
            <td>Specify the Outgoing (egress) interface for the firewall policy you want to create in Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Service</td>
            <td>Specify service and service group names for the firewall policy you want to create in Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Source IPv4 Address</td>
            <td>Specify source IPv4 address and address group names for the firewall policy you want to create in Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Source IPv6 Address</td>
            <td>Specify source IPv6 address and address group names for the firewall policy you want to create in Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Destination IPv4 Address</td>
            <td>Specify destination IPv4 address and address group names for the firewall policy you want to create in Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Destination IPv6 Address</td>
            <td>Specify destination IPv6 address and address group names for the firewall policy you want to create in Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Policy Action</td>
            <td>Select the policy action for the firewall policy you want to create in Fortinet FortiManager. You can select from the following options:
                <ul>
                    <li><strong>Accept</strong>: Allows sessions that match the firewall policy.</li>
                    <li><strong>Deny</strong>: Blocks sessions that match the firewall policy.</li>
                    <li><strong>IPSec</strong>: Firewall policy becomes a policy-based IPsec VPN policy.</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Status</td>
            <td>Select <strong>Enable</strong> to enable this firewall policy on Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Schedule</td>
            <td>Specify the name for the schedule to be associated with the firewall policy that you want to create in Fortinet FortiManager. For example, <code>always, none,</code>etc.</td>
        </tr>
        <tr>
            <td>Comment</td>
            <td>(Optional) Comment to be added to the firewall policy that you want to create.</td>
        </tr>
        <tr>
            <td>Log Traffic</td>
            <td>Select the method of logging traffic, i.e, logging of all sessions or security profile sessions. You can select from the following:
                <ul>
                    <li><strong>All</strong>: Logs all sessions accepted or denied by this policy.</li>
                    <li><strong>UTM</strong>: Logs traffic that has an applied security profile applied.</li>
                    <li><strong>Disable</strong>: Disables all logging for this policy.</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Additional Policy Arguments</td>
            <td>(Optional) Specify additional arguments, in JSON format, to be added during the creation of the firewall policy. You can enter the arguments in the following format: <code>{&quot;field1&quot;:value1, &quot;field2&quot;:value2}</code>.<br />
                For example,<code>{&quot;logtraffic-start&quot;: &quot;disable&quot;, &quot;radius-mac-auth-bypass&quot;: &quot;disable&quot;, &quot;profile-type&quot;: &quot;single&quot; }</code></td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "data": {
                "policyid": ""
            },
            "status": {
                "code": "",
                "message": ""
            },
            "url": ""
        }
    ]
}</pre>

<h3>operation: Update Firewall Policy</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Level Type</td>
            <td>Select the level type at which you want to update the firewall policy. You can select between ADOM or Global Type.<br />
                If you select 'ADOM', then you can specify the following parameters:
                <ul>
                    <li>ADOM: Administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified as a configuration parameter.</li>
                </ul>
                <p>If you select 'Global', then you can specify the following parameters:</p>
                <ul>
                    <li>Policy Type: Select the type of firewall policy you want to update in Fortinet FortiManager.</li>
                </ul>
            </td>
        </tr>
        <tr>
        <td>NGFW Mode</td>
        <td>Select the NGFW mode of the policy package. You can select from following options:
            <ul>
                <li>Policy Based</li>
                <li><strong>Profile Based</strong>: Specify values in the followin fields:
                    <ul>
                        <li><strong>Inspection Mode</strong>: Select the Inspection mode for the firewall policy that you want to update in Fortinet FortiManager. You can select from following fields:
                            <ul>
                                <li>Proxy</li>
                                <li>Flow (default)</li>
                            </ul>
                        </li>
                        <li><strong>Schedule Timeout</strong>: Select one of the following:
                            <ul>
                                <li><strong>Enable</strong>: Select to forcefully end currently running sessions when the schedule object times out.</li>
                                <li><strong>Disable</strong>: Select to allow sessions to end from inactivity.</li>
                            </ul>
                        </li>
                    </ul>
                </li>
            </ul>
        </td>
        </tr>
        <tr>
            <td>Policy Package Name</td>
            <td>Specify a valid policy package name for the firewall policy you want to update in Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Policy Name</td>
            <td>Valid name of the policy name that you want to update in Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Method</td>
            <td>Select the action that you want to perform for updating the firewall policy in Fortinet FortiManager. You can select between Add or Remove.<br />
                If you select 'Add', then you can specify the following parameters:
                <ul>
                    <li>Add Source Interface: Specify the Incoming (ingress) interface that you want to add to the firewall policy you want to update in Fortinet FortiManager.</li>
                    <li>Add Destination Interface: Specify the Outgoing (egress) interface that you want to add to the firewall policy you want to update in Fortinet FortiManager.</li>
                    <li>Add Service: Specify service and service group names that you want to add to the firewall policy you want to update in Fortinet FortiManager.</li>
                    <li>Add Source IPv4 Address: Specify the source IPv4 address and address group names that you want to add to the firewall policy you want to update in Fortinet FortiManager.</li>
                    <li>Add Source IPv6 Address: Specify the source IPv6 address and address group names that you want to add to the firewall policy you want to update in Fortinet FortiManager.</li>
                    <li>Add Destination IPv4 Address: Specify the destination IPv4 address and address group names that you want to add to the firewall policy you want to update in Fortinet FortiManager.</li>
                    <li>Add Destination IPv6 Address: Specify the destination IPv6 address and address group names that you want to add to the firewall policy you want to update in Fortinet FortiManager.</li>
                </ul>
                If you select 'Remove', then you can specify the following parameters:
                <ul>
                    <li>Remove Source Interface: Specify the Incoming (ingress) interface that you want to remove from the firewall policy you want to update in Fortinet FortiManager.</li>
                    <li>Remove Destination Interface: Specify the Outgoing (egress) interface that you want to remove from the firewall policy you want to update in Fortinet FortiManager.</li>
                    <li>Remove Service: Specify service and service group names that you want to remove from the firewall policy you want to update in Fortinet FortiManager.</li>
                    <li>Remove Source IPv4 Address: Specify the source IPv4 address and address group names that you want to remove from the firewall policy you want to update in Fortinet FortiManager.</li>
                    <li>Remove Source IPv6 Address: Specify the source IPv6 address and address group names that you want to remove from the firewall policy you want to update in Fortinet FortiManager.</li>
                    <li>Remove Destination IPv4 Address: Specify the destination IPv4 address and address group names that you want to remove from the firewall policy you want to update in Fortinet FortiManager.</li>
                    <li>Remove Destination IPv6 Address: Specify the destination IPv6 address and address group names that you want to remove from the firewall policy you want to update in Fortinet FortiManager.</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Policy Action</td>
            <td>Select the policy action for the firewall policy you want to update in Fortinet FortiManager. You can select from the following options:
                <ul>
                    <li><strong>Accept</strong>: Allows sessions that match the firewall policy.</li>
                    <li><strong>Deny</strong>: Blocks sessions that match the firewall policy.</li>
                    <li><strong>IPSec</strong>: Firewall policy becomes a policy-based IPsec VPN policy.</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Status</td>
            <td>Select <strong>Enable</strong> to enable this firewall policy on Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Schedule</td>
            <td>Specify the name for the schedule to be associated with the firewall policy that you want to update in Fortinet FortiManager. For example, <code>always, none</code>, etc.</td>
        </tr>
        <tr>
            <td>Comment</td>
            <td>(Optional) Comment to be added to the firewall policy that you want to update.</td>
        </tr>
        <tr>
            <td>Additional Policy Arguments</td>
            <td>(Optional) Specify additional arguments, in JSON format, to be added during the updation of the firewall policy. You can enter the arguments in the following format:&nbsp;<code>{&quot;field1&quot;:value1, &quot;field2&quot;:value2}</code>. For example, <code>{&quot;radius-mac-auth-bypass&quot;: &quot;disable&quot;, &quot;profile-type&quot;: &quot;single&quot; }</code></td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "data": {
                "policyid": ""
            },
            "status": {
                "code": "",
                "message": ""
            },
            "url": ""
        }
    ]
}</pre>

<h3>operation: Delete Firewall Policy</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Type</td>
            <td>Select the level type at which you want to delete the firewall policy. You can select between ADOM or Global Type.<br />
                If you select 'ADOM', then you can specify the following parameters:
                <ul>
                    <li>ADOM: Administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified as a configuration parameter.</li>
                </ul>
                <p>If you select 'Global', then you can specify the following parameters:</p>
                <ul>
                    <li>Policy Type: Select the type of firewall policy you want to delete from Fortinet FortiManager.</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>NGFW Mode</td>
            <td>Select the NGFW mode of the policy package. You can choose from following options:
                <ul>
                    <li>Profile Based</li>
                    <li>Policy Based</li>
                </ul>
                By default, it is Profile Based.
            </td>
        </tr>
        <tr>
            <td>Policy Package Name</td>
            <td>Specify a valid policy package name for the firewall policy you want to delete from Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Policy ID</td>
            <td>Specify the ID of the firewall policy that you want to delete from Fortinet FortiManager. You can get the policy ID from &quot;List Global Firewall Policies&quot; or &quot;List ADOM Firewall Policies&quot; actions.</td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "url": "",
            "status": {
                "code": "",
                "message": ""
            }
        }
    ]
}</pre>

<h3>operation: Move Firewall Policy</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Level</td>
            <td>Select the level type at which you want to move the firewall policy. You can select between ADOM or Global Type.<br />
                If you select 'ADOM', then you can specify the following parameters:
                <ul>
                    <li>ADOM: Administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified as a configuration parameter.</li>
                </ul>
                <p>If you select 'Global', then you can specify the following parameters:</p>
                <ul>
                    <li>Policy Type: Select the type of firewall policy you want to move in Fortinet FortiManager.</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>NGFW Mode</td>
            <td>Select the NGFW mode of the policy package. You can choose from following options:
                <ul>
                    <li>Profile Based</li>
                    <li>Policy Based</li>
                </ul>
                By default, it is Profile Based.
            </td>
        </tr>
        <tr>
            <td>Policy Package Name</td>
            <td>Specify a valid policy package name for the firewall policy you want to move in Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Policy ID</td>
            <td>Specify the ID of the firewall policy that you want to move in Fortinet FortiManager. You can get the policy ID from &quot;List Global Firewall Policies&quot; or &quot;List ADOM Firewall Policies&quot; actions.</td>
        </tr>
        <tr>
            <td>Target</td>
            <td>Specify the Key to the target entry, i.e., the ID of the target policy.</td>
        </tr>
        <tr>
            <td>Option</td>
            <td>Select whether you want to move the firewall policy <strong>Before</strong> or <strong>After</strong> the target policy in Fortinet FortiManager.</td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "url": "",
            "data": {
                "policyid": ""
            },
            "status": {
                "code": "",
                "message": ""
            }
        }
    ]
}</pre>

<h3>operation: Get Dynamic Interface List</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Level</td>
            <td>Select the level type from which you want to retrieve the dynamic interface details. You can select between ADOM or Global Type.<br />
                If you select 'ADOM', then you can specify the following parameters:
                <ul>
                    <li>ADOM: Administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified as a configuration parameter.</li>
                    <li>Interface Name: Valid dynamic interface name based on which you want to retrieve dynamic interface details from Fortinet FortiManager.<br />
                        <strong>Note</strong>: If this parameter is left blank or <code>null</code>, this operation returns all dynamic interfaces matching all values.
                    </li>
                </ul>
                If you select 'Global', then you can specify the following parameters:
                <ul>
                    <li>Interface Name: Valid dynamic interface name based on which you want to retrieve dynamic interface details from Fortinet FortiManager.<br />
                        <strong>Note</strong>: If this parameter is left blank or <code>null</code>, this operation returns all dynamic interfaces matching all values.
                    </li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Attributes in Result</td>
            <td>(Optional) Specify a string array to limit the output by returning only the specified attributes. For example, <code>[&quot;color&quot;, &quot;default-mapping&quot;, &quot;defmap-intf&quot;, &quot;defmap-intrazone-deny&quot;, &quot;defmap-zonemember&quot;, &quot;description&quot;, &quot;egress-shaping-profile&quot;, &quot;name&quot;, &quot;single-intf&quot;, &quot;wildcard&quot;, &quot;wildcard-intf&quot;]</code><br />
                <strong>Note</strong>: If attributes are not specified, then all attributes will be returned.
            </td>
        </tr>
        <tr>
            <td>Filter By</td>
            <td>(Optional) Specify attributes to filter the results according to a set criteria.
        </tr>
        <tr>
            <td>Limit</td>
            <td>(Optional) Specify the maximum number of results that this operation should return.</td>
        </tr>
        <tr>
            <td>Offset</td>
            <td>(Optional) Specify the offset value to retrieve a subset of records that starts from the offset value. The offset works with the <em>Limit</em> parameter, which determines how many records to retrieve starting from the offset. Values supported are:
                <ul>
                    <li><strong>Default:<code>&quot;0&quot;</code></strong></li>
                    <li><strong>Minimum:<code>&quot;0&quot;</code></strong></li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Sort By</td>
            <td>Sort the dynamic interfaces by the specified field and order the results. You can select to either sort the results by fields, or can order the results, or both.<br />
                If you select 'Field', then you must specify the following parameters:
                <ul>
                    <li>Field: Field: Specify the name of the field on which you want to sort the result. For example,<code>color, default-mapping, defmap-intf, defmap-intrazone-deny, defmap-zonemember, description, egress-shaping-profile, name, single-intf, wildcard, wildcard-intf</code>, etc.</li>
                    <li>Order: Select the order in which to sort the results. You can choose from following options:
                        <ul>
                            <li>Ascending (default)</li>
                            <li>Descending</li>
                        </ul>
                    </li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "url": "",
            "data": [
                {
                    "name": "",
                    "color": "",
                    "wildcard": "",
                    "single-intf": "",
                    "default-mapping": "",
                    "dynamic_mapping": "",
                    "platform_mapping": [
                        {
                            "name": "",
                            "intf-zone": "",
                            "intrazone-deny": ""
                        }
                    ],
                    "defmap-zonemember": [],
                    "defmap-intrazone-deny": ""
                }
            ],
            "status": {
                "code": "",
                "message": ""
            }
        }
    ]
}</pre>

<h3>operation: Install Policy</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>ADOM Name</td>
            <td>Specify the ADOM name of the policy that you want to install in Fortinet FortiManager. The ADOM that you specify here overwrites the ADOM that you have specified as a configuration parameter.</td>
        </tr>
        <tr>
            <td>Policy Package Name</td>
            <td>Select the name of the policy package that you want to install in Fortinet FortiManager. This parameter will make an API call named <code>list_adom_policy_package</code> to dynamically populate its dropdown selections.</td>
        </tr>
        <tr>
            <td>ADOM Revision Comment</td>
            <td>Specify the ADOM revision comment of the policy that you want to install in Fortinet FortiManager</td>
        </tr>
        <tr>
            <td>ADOM Revision Name</td>
            <td>Specify the ADOM revision name of the policy that you want to install in Fortinet FortiManager</td>
        </tr>
        <tr>
            <td>Device Configuration Revision</td>
            <td>Comments that you want to add for the device configuration revision that will be generated during the installation.</td>
        </tr>
        <tr>
            <td>Device Name</td>
            <td>Specify the device name or device group name on which you want to install the policy package.</td>
        </tr>
        <tr>
            <td>VDOM</td>
            <td>Specify the VDOM on which you want to install the policy package.</td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "url": "",
            "data": {
                "task": ""
            },
            "status": {
                "code": "",
                "message": ""
            }
        }
    ]
}</pre>

<h3>operation: Get Installation Policy Package Status</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Task ID</td>
            <td>Specify the ID of the task whose policy package installation status you want to retrieve from Fortinet FortiManager. You get the task ID using the &quot;Install Policy&quot; action.</td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "url": "",
            "data": {
                "id": "",
                "pid": "",
                "src": "",
                "adom": "",
                "line": [
                    {
                        "ip": "",
                        "err": "",
                        "oid": "",
                        "name": "",
                        "vdom": "",
                        "state": "",
                        "detail": "",
                        "end_tm": "",
                        "history": [
                            {
                                "name": "",
                                "vdom": "",
                                "state": "",
                                "detail": "",
                                "percent": ""
                            },
                            {
                                "name": "",
                                "vdom": "",
                                "state": "",
                                "detail": "",
                                "percent": ""
                            }
                        ],
                        "percent": "",
                        "start_tm": ""
                    }
                ],
                "user": "",
                "flags": "",
                "state": "",
                "title": "",
                "end_tm": "",
                "num_err": "",
                "percent": "",
                "num_done": "",
                "num_warn": "",
                "start_tm": "",
                "num_lines": "",
                "tot_percent": ""
            },
            "status": {
                "code": "",
                "message": ""
            }
        }
    ]
}</pre>

<h3>operation: Create LDAP Server</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Level Type</td>
            <td>Select the level type at which you want to create the LDAP server. You can select between ADOM or Global Type.<br />
                If you select 'ADOM', then you can specify the following parameters:
                <ul>
                    <li>ADOM: Administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified as a configuration parameter.</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>LDAP Server Name</td>
            <td>Specify the entry name of the LDAP server used to create the LDAP server that you want to create on Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Username</td>
            <td>Specify the Username (full DN) used for initial binding at the time of the creation of the LDAP server on Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Password</td>
            <td>Specify the Password used for initial binding at the time of the creation of the LDAP server on Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Distinguished Name</td>
            <td>Specify the Distinguished Name used to look up entries on the LDAP server at the time of the creation of the LDAP server on Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Server</td>
            <td>Specify the LDAP server CN domain name or IP to be used at the time of the creation of the LDAP server on Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Account Key Processing</td>
            <td>Select the type of Account Key processing operation, either <strong>Same</strong>&nbsp;(keep) or <strong>Strip</strong>&nbsp;(strip domain string of UPN in the token) to be used at the time of the creation of the LDAP server on Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>AntiPhishing</td>
            <td>Select <strong>Enable </strong>to enable the AntiPhishing credential backend when the LDAP server is being created on Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Group Member Check</td>
            <td>Select the type of group member checking methods to be used at the time of the creation of the LDAP server on Fortinet FortiManager. You can select between User Attribute, Group Object, or Posix Group Object.</td>
        </tr>
        <tr>
            <td>Interface Select Method</td>
            <td>Select the type of outgoing interface selection method used to reach the server at the time of the creation of the LDAP server on Fortinet FortiManager. You can select between Auto, SD-WAN, or Specify.</td>
        </tr>
        <tr>
            <td>Obtain User Info</td>
            <td>Select <strong>Enable</strong> to enable obtaining user information when the LDAP server is being created on Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Source IP</td>
            <td>(Optional) Specify the IP address of FortiGate to be used for communication with the LDAP server when the LDAP server is being created on Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Source Port</td>
            <td>(Optional) Specify the source port to be used for communication with the LDAP server when the LDAP server is being created on Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Additional LDAP Server Arguments</td>
            <td>(Optional) Specify additional arguments, in JSON format, to be added during the creation of the LDAP server. You can enter the arguments in the following format: <code>{&quot;field1&quot;:value1, &quot;field2&quot;:value2}</code>. For example, <code>{&quot;account-key-filter&quot;: &quot;string&quot;, &quot;group-filter&quot;: &quot;string&quot;, &quot;ssl-min-proto-version&quot;: &quot;default&quot; }</code></td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "data": {
                "name": ""
            },
            "status": {
                "code": "",
                "message": ""
            },
            "url": ""
        }
    ]
}</pre>

<h3>operation: Get LDAP Server List</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Level</td>
            <td>Select the level type from which you want to retrieve the details for the LDAP servers. You can select between ADOM or Global Type.<br />
                If you select 'ADOM', then you can specify the following parameters:
                <ul>
                    <li>ADOM: Administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified as a configuration parameter.</li>
                    <li>LDAP Server Name: Valid LDAP server name based on which you want to retrieve LDAP server details from Fortinet FortiManager.<br />
                        <strong>Note</strong>: If this parameter is left blank or <code>null</code>, this operation returns all LDAP servers matching all values.
                    </li>
                </ul>
                If you select 'Global', then you can specify the following parameters:
                <ul>
                    <li>LDAP Server Name: Valid LDAP server name based on which you want to retrieve LDAP server details from Fortinet FortiManager.<br />
                        <strong>Note</strong>: If this parameter is left blank or <code>null</code>, this operation returns all LDAP servers matching all values.
                    </li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Attributes in Result</td>
            <td>(Optional) Specify a string array to limit the output by returning only the specified attributes. For example, <code>[ &quot;account-key-filter&quot;, &quot;account-key-processing&quot;, &quot;antiphish&quot;, &quot;ca-cert&quot;, &quot;cnid&quot;, &quot;dn&quot;, &quot;group-filter&quot;, &quot;group-member-check&quot;, &quot;group-object-filter&quot;, &quot;group-search-base&quot;, &quot;interface&quot;, &quot;interface-select-method&quot;, &quot;member-attr&quot;, &quot;name&quot;, &quot;obtain-user-info&quot;, &quot;password&quot;, &quot;password-attr&quot;, &quot;password-expiry-warning&quot;, &quot;password-renewal&quot;, &quot;port&quot;, &quot;search-type&quot;, &quot;secondary-server&quot;, &quot;secure&quot;, &quot;server&quot;, &quot;server-identity-check&quot;, &quot;source-ip&quot;, &quot;source-port&quot;, &quot;ssl-min-proto-version&quot;, &quot;tertiary-server&quot;, &quot;two-factor&quot;, &quot;two-factor-authentication&quot;, &quot;two-factor-notification&quot;, &quot;type&quot;, &quot;user-info-exchange-server&quot;, &quot;username&quot; ]</code><br />
                <strong>Note</strong>: If attributes are not specified, then all attributes will be returned.
            </td>
        </tr>
        <tr>
            <td>Filter By</td>
            <td>(Optional) Specify attributes to filter the results according to a set criteria.
        </tr>
        <tr>
            <td>Limit</td>
            <td>(Optional) Specify the maximum number of results that this operation should return.</td>
        </tr>
        <tr>
            <td>Offset</td>
            <td>(Optional) Specify the offset value to retrieve a subset of records that starts from the offset value. The offset works with the <em>Limit</em> parameter, which determines how many records to retrieve starting from the offset. Values supported are:
                <ul>
                    <li><strong>Default:<code>&quot;0&quot;</code></strong></li>
                    <li><strong>Minimum:<code>&quot;0&quot;</code></strong></li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Sort By</td>
            <td>Sort the LDAP servers by the specified field and order the results. You can select to either sort the results by fields, or can order the results, or both.<br />
                If you select 'Field', then you must specify the following parameters:
                <ul>
                    <li>Field: Specify the name of the field on which you want to sort the result. For example, <code>account-key-filter, account-key-processing, antiphish, ca-cert, cnid, dn, group-filter, group-member-check, group-object-filter, group-search-base, interface, interface-select-method, member-attr, name, obtain-user-info, password, password-attr, password-expiry-warning, password-renewal, port, search-type, secondary-server, secure, server, server-identity-check, source-ip, source-port, ssl-min-proto-version, tertiary-server, two-factor, two-factor-authentication, two-factor-notification, type, user-info-exchange-server, username</code></li>
                    <li>Order: Select the order in which to sort the results. You can choose from following options:
                        <ul>
                            <li>Ascending (default)</li>
                            <li>Descending</li>
                        </ul>
                    </li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "url": "",
            "data": [],
            "status": {
                "code": "",
                "message": ""
            }
        }
    ]
}</pre>

<h3>operation: Update LDAP Server</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Level Type</td>
            <td>Select the level type at which you want to update the LDAP server. You can select between ADOM or Global Type.<br />
                If you select 'ADOM', then you can specify the following parameters:
                <ul>
                    <li>ADOM: Administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified as a configuration parameter.</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>LDAP Server Name</td>
            <td>Specify the entry name of the LDAP server used to update the LDAP server that you want to update on Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Username</td>
            <td>(Optional) Specify the Username (full DN) used for initial binding at the time of the updation of the LDAP server on Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Password</td>
            <td>(Optional) Specify the Password used for initial binding at the time of the updation of the LDAP server on Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Distinguished Name</td>
            <td>(Optional) Specify the Distinguished Name used to look up entries on the LDAP server at the time of the updation of the LDAP server on Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Server</td>
            <td>(Optional) Specify the LDAP server CN domain name or IP to be used at the time of the updation of the LDAP server on Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Account Key Processing</td>
            <td>Select the type of Account Key processing operation, either <strong>Same</strong>&nbsp;(keep) or <strong>Strip</strong>&nbsp;(strip domain string of UPN in the token) to be used at the time of the updation of the LDAP server on Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>AntiPhishing</td>
            <td>Select <strong>Enable </strong>to enable the AntiPhishing credential backend when the LDAP server is being updated on Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Group Member Check</td>
            <td>Select the type of group member checking methods to be used at the time of the updation of the LDAP server on Fortinet FortiManager. You can select between User Attribute, Group Object, or Posix Group Object.</td>
        </tr>
        <tr>
            <td>Interface Select Method</td>
            <td>Select the type of outgoing interface selection method used to reach the server at the time of the updation of the LDAP server on Fortinet FortiManager. You can select between Auto, SD-WAN, or Specify.</td>
        </tr>
        <tr>
            <td>Obtain User Info</td>
            <td>Select <strong>Enable</strong> to enable obtaining of user information when the LDAP server is being updated on Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Source IP</td>
            <td>(Optional) Specify the IP address of FortiGate to be used for communication with the LDAP server when the LDAP server is being updated on Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Source Port</td>
            <td>(Optional) Specify the source port to be used for communication with the LDAP server when the LDAP server is being updated on Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Additional LDAP Server Arguments</td>
            <td>(Optional) Specify additional arguments, in JSON format, to be added during the updation of the LDAP server. You can enter the arguments in the following format: <code>{&quot;field1&quot;:value1, &quot;field2&quot;:value2}</code>. For example, <code>{&quot;account-key-filter&quot;: &quot;string&quot;, &quot;group-filter&quot;: &quot;string&quot;, &quot;ssl-min-proto-version&quot;: &quot;default&quot; }</code></td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "data": {
                "name": ""
            },
            "status": {
                "code": "",
                "message": ""
            },
            "url": ""
        }
    ]
}</pre>

<h3>operation: Delete LDAP Server</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Type</td>
            <td>Select the level type at which you want to delete the LDAP server. You can select between ADOM or Global Type.<br />
                If you select 'ADOM', then you can specify the following parameters:
                <ul>
                    <li>ADOM: Administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified as a configuration parameter.</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>LDAP Server Name</td>
            <td>Specify the entry name of the LDAP server that you want to delete from Fortinet FortiManager.</td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "url": "",
            "status": {
                "code": "",
                "message": ""
            }
        }
    ]
}</pre>

<h3>operation: Create User Group</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Level Type</td>
            <td>Select the level type at which you want to create the user group. You can select between ADOM or Global Type.<br />
                If you select 'ADOM', then you can specify the following parameters:
                <ul>
                    <li>ADOM: Administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified as a configuration parameter.</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Group Name</td>
            <td>Specify the name of the user group you want to create in Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Member</td>
            <td>Specify a CSV list or list of names of users, peers, LDAP servers, or RADIUS servers that you want to add to the user group, which you want to create in Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Additional User Group Arguments</td>
            <td>(Optional) Specify additional arguments, in JSON format, to be added during the creation of the user group. You can enter the arguments in the following format: <code>{&quot;field1&quot;:value1, &quot;field2&quot;:value2}</code>. For example, <code>{&quot;account-key-filter&quot;: &quot;string&quot;, &quot;group-filter&quot;: &quot;string&quot;, &quot;ssl-min-proto-version&quot;: &quot;default&quot; }</code></td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "data": {
                "name": ""
            },
            "status": {
                "code": "",
                "message": ""
            },
            "url": ""
        }
    ]
}</pre>

<h3>operation: Get User Groups List</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Level</td>
            <td>Select the level type from which you want to retrieve the details for the user groups. You can select between ADOM or Global Type.<br />
                If you select 'ADOM', then you can specify the following parameters:
                <ul>
                    <li>ADOM: Administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified as a configuration parameter.</li>
                    <li>User Group Name: Valid user group name based on which you want to retrieve user group details from Fortinet FortiManager.<br />
                        <strong>Note</strong>: If this parameter is left blank or <code>null</code>, this operation returns all user groups matching all values.
                    </li>
                </ul>
                If you select 'Global', then you can specify the following parameters:
                <ul>
                    <li>User Group Name: Valid user group name based on which you want to retrieve user group details from Fortinet FortiManager.<br />
                        <strong>Note</strong>: If this parameter is left blank or <code>null</code>, this operation returns all user groups matching all values.
                    </li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Attributes in Result</td>
            <td>(Optional) Specify a string array to limit the output by returning only the specified attributes. For example, <code>[&quot;auth-concurrent-override&quot;,&quot;auth-concurrent-value&quot;,&quot;authtimeout&quot;,&quot;company&quot;,&quot;email&quot;,&quot;expire&quot;,&quot;expire-type&quot;,&quot;group-type&quot;,&quot;http-digest-realm&quot;,&quot;id&quot;,&quot;max-accounts&quot;,&quot;member&quot;,&quot;mobile-phone&quot;,&quot;multiple-guest-add&quot;,&quot;name&quot;,&quot;password&quot;,&quot;sms-custom-server&quot;,&quot;sms-server&quot;,&quot;sponsor&quot;,&quot;sso-attribute-value&quot;,&quot;user-id&quot;,&quot;user-name&quot;]&nbsp;</code><br />
                <strong>Note</strong>: If attributes are not specified, then all attributes will be returned.
            </td>
        </tr>
        <tr>
            <td>Filter By</td>
            <td>(Optional) Specify attributes to filter the results according to a set criteria.
        </tr>
        <tr>
            <td>Limit</td>
            <td>(Optional) Specify the maximum number of results that this operation should return.</td>
        </tr>
        <tr>
            <td>Offset</td>
            <td>(Optional) Specify the offset value to retrieve a subset of records that starts from the offset value. The offset works with the <em>Limit</em> parameter, which determines how many records to retrieve starting from the offset. Values supported are:
                <ul>
                    <li><strong>Default:<code>&quot;0&quot;</code></strong></li>
                    <li><strong>Minimum:<code>&quot;0&quot;</code></strong></li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Sort By</td>
            <td>Sort the user groups by the specified field and order the results. You can select to either sort the results by fields, or can order the results, or both.<br />
                If you select 'Field', then you must specify the following parameters:
                <ul>
                    <li>Field: Specify the name of the field on which you want to sort the result. For example, <code>auth-concurrent-override, auth-concurrent-value, authtimeout, company, email, expire, expire-type, group-type, http-digest-realm, id, max-accounts, member, mobile-phone, multiple-guest-add, name, password, sms-custom-server, sms-server, sponsor, sso-attribute-value, user-id, user-name</code></li>
                    <li>Order: Select the order in which to sort the results. You can choose from following options:
                        <ul>
                            <li>Ascending (default)</li>
                            <li>Descending</li>
                        </ul>
                    </li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "url": "",
            "data": [
                {
                    "id": "",
                    "oid": "",
                    "name": "",
                    "guest": "",
                    "match": "",
                    "member": [],
                    "group-type": "",
                    "sms-server": "",
                    "authtimeout": "",
                    "dynamic_mapping": "",
                    "auth-concurrent-value": "",
                    "auth-concurrent-override": ""
                }
            ],
            "status": {
                "code": "",
                "message": ""
            }
        }
    ]
}</pre>

<h3>operation: Update User Group</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Level Type</td>
            <td>Select the level type at which you want to update the user group. You can select between ADOM or Global Type.<br />
                If you select 'ADOM', then you can specify the following parameters:
                <ul>
                    <li>ADOM: Administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified as a configuration parameter.</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Group Name</td>
            <td>Specify the name of the user group you want to update in Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Method</td>
            <td>Select the action that you want to perform on members of the user group. You can select between Add or Remove.
                <ul>
                    <li>If you select '<strong>Add</strong>', then in the <strong>Add Member</strong> field, specify a CSV list or list of names of users, peers, LDAP servers, or RADIUS servers that you want to add to the user group, which you want to update in Fortinet FortiManager.</li>
                    <li>If you select '<strong>Remove</strong>', then in the <strong>Remove Member</strong> field, specify a CSV list or list of names of users, peers, LDAP servers, or RADIUS servers that you want to remove from the user group, which you want to update in Fortinet FortiManager.</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Additional User Group Arguments</td>
            <td>(Optional) Specify additional arguments, in JSON format, to be added during the updation of the user group. You can enter the arguments in the following format: <code>{&quot;field1&quot;:value1, &quot;field2&quot;:value2}</code>. For example, <code>{&quot;sponsor&quot;: &quot;optional&quot;, &quot;sms-server&quot;: &quot;string&quot;, &quot;ssl-min-proto-version&quot;: &quot;default&quot; }</code></td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "data": {
                "name": ""
            },
            "status": {
                "code": "",
                "message": ""
            },
            "url": ""
        }
    ]
}</pre>

<h3>operation: Delete User Group</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Type</td>
            <td>Select the level type at which you want to delete the user group. You can select between ADOM or Global Type.<br />
                If you select 'ADOM', then you can specify the following parameters:
                <ul>
                    <li>ADOM: Administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified as a configuration parameter.</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Group Name</td>
            <td>Name of the group from which you want to delete the user group on Fortinet FortiManager.</td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "url": "",
            "status": {
                "code": "",
                "message": ""
            }
        }
    ]
}</pre>

<h3>operation: Get SSL VPN Settings</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Device</td>
            <td>Specify the device name whose SSL VPN settings you want to retrieve from Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>VDOM</td>
            <td>Specify the VDOM name using which you want to retrieve the SSL VPN settings from Fortinet FortiManager. For example, <code>root</code></td>
        </tr>
        <tr>
            <td>Option</td>
            <td>Select the Fetch option to be set for the request. If you do not select any option then by default all the attributes of the object are returned. You can select from the following:
                <ul>
                    <li><strong>Object</strong> - Returns a list of object members along with other attributes.</li>
                    <li><strong>Check Sum</strong> - Returns the check-sum value instead of attributes.</li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "url": "",
            "data": {
                "algorithm": "",
                "auth-session-check-source-ip": "",
                "auth-timeout": "",
                "authentication-rule": [
                    {
                        "auth": "",
                        "cipher": "",
                        "client-cert": "",
                        "groups": [],
                        "id": "",
                        "obj seq": "",
                        "portal": [],
                        "realm": [],
                        "source-address": [],
                        "source-address-negate": "",
                        "source-address6": [],
                        "source-address6-negate": "",
                        "source-interface": [],
                        "users": []
                    }
                ],
                "auto-tunnel-static-route": "",
                "banned-cipher": "",
                "check-referer": "",
                "ciphersuite": "",
                "client-sigalgs": "",
                "default-portal": [],
                "deflate-compression-level": "",
                "deflate-min-data-size": "",
                "dns-server1": "",
                "dns-server2": "",
                "dns-suffix": "",
                "dtls-hello-timeout": "",
                "dtls-max-proto-ver": "",
                "dtls-min-proto-ver": "",
                "dtls-tunnel": "",
                "dual-stack-mode": "",
                "encode-2f-sequence": "",
                "encrypt-and-store-password": "",
                "force-two-factor-auth": "",
                "header-x-forwarded-for": "",
                "hsts-include-subdomains": "",
                "http-compression": "",
                "http-only-cookie": "",
                "http-request-body-timeout": "",
                "http-request-header-timeout": "",
                "https-redirect": "",
                "idle-timeout": "",
                "ipv6-dns-server1": "",
                "ipv6-dns-server2": "",
                "ipv6-wins-server1": "",
                "ipv6-wins-server2": "",
                "login-attempt-limit": "",
                "login-block-time": "",
                "login-timeout": "",
                "port": "",
                "port-precedence": "",
                "reqclientcert": "",
                "saml-redirect-port": "",
                "servercert": [],
                "source-address": [],
                "source-address-negate": "",
                "source-address6": [],
                "source-address6-negate": "",
                "source-interface": [],
                "ssl-client-renegotiation": "",
                "ssl-insert-empty-fragment": "",
                "ssl-max-proto-ver": "",
                "ssl-min-proto-ver": "",
                "status": "",
                "transform-backward-slashes": "",
                "tunnel-addr-assigned-method": "",
                "tunnel-connect-without-reauth": "",
                "tunnel-ip-pools": [],
                "tunnel-ipv6-pools": [],
                "tunnel-user-session-timeout": "",
                "unsafe-legacy-renegotiation": "",
                "url-obscuration": "",
                "wins-server1": "",
                "wins-server2": "",
                "x-content-type-options": ""
            },
            "status": {
                "code": "",
                "message": ""
            }
        }
    ]
}</pre>

<h3>operation: Update SSL VPN Settings</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Device</td>
            <td>Specify the device name whose SSL VPN settings you want to update in Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>VDOM</td>
            <td>Specify the VDOM name using which you want to update the SSL VPN settings in Fortinet FortiManager. For example, <code>root</code></td>
        </tr>
        <tr>
            <td>Default SSL VPN Portal</td>
            <td>Specify the default SSL VPN portal to be used to update the SSL VPN settings in Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Source Interface</td>
            <td>Specify a comma-separated values or a list of SSL VPN source interfaces incoming traffic to update the SSL VPN settings in Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Port</td>
            <td>Specify the SSL VPN access port (1 - 65535) to be used to update the SSL VPN settings in Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Server Certificate</td>
            <td>Specify the name of the server certificate to be used for SSL VPNs when the SSL VPN settings are updated in Fortinet FortiManager. For example, <code>self-sign</code></td>
        </tr>
        <tr>
            <td>Authentication/Portal Mapping</td>
            <td>By default, all users see the same Authentication/Portal portal and this parameter is unchecked (cleared). The Authentication/Portal Mapping allows you to assign different portals to different users and groups in Fortinet FortiManager.
                <p><strong>Note</strong>: To update the default Authentication/Portal Mapping, you must select this parameter and then specify at least one of the following Authentication/Portal Mapping parameters:</p>
                <ul>
                    <li>Authentication/Portal ID: Specify the Authentication/Portal mapping ID to be updated in the SSL VPN settings in Fortinet FortiManager.</li>
                    <li>Authentication/Portal User Names: Specify the CSV list or list of user names to be updated in the SSL VPN settings in Fortinet FortiManager.</li>
                    <li>Authentication/Portal User Groups: Specify the CSV list or list of user groups to be updated in the SSL VPN settings in Fortinet FortiManager.</li>
                    <li>Authentication/Portal Realm: Specify the SSL VPN Realm to be used to update the SSL VPN settings in Fortinet FortiManager</li>
                    <li>Authentication/Portal Portal: Specify the SSL VPN portal to be used to update the SSL VPN settings in Fortinet FortiManager. For example, <code>web-access</code>, <code>full-access</code>, <code>tunnel-access</code>, etc.</li>
                    <li>Authentication/Portal Authentication: Select the SSL VPN authentication method restriction to be used to update the SSL VPN settings in Fortinet FortiManager. You can select between Any, Local, LDAP, RADIUS, or TACACS+.</li>
                    <li>Authentication/Portal Cipher: Specify the SSL VPN cipher strength to be used to update the SSL VPN settings in Fortinet FortiManager. You can select between Any, High, or Medium.</li>
                    <li>Authentication/Portal Client Certificate: Select <strong>Enable</strong> to enable SSL VPN client certificate restriction when the SSL VPN settings are updated in Fortinet FortiManager.</li>
                    <li>Authentication/Portal Source Interface: Specify the CSV or the list of SSL VPN source interfaces of incoming traffic to be used to update the SSL VPN settings in Fortinet FortiManager.</li>
                    <li>Authentication/Portal Source Address: Specify the CSV or the list of source addresses of incoming traffic to be updated in the SSL VPN settings in Fortinet FortiManager.</li>
                    <li>Authentication/Portal Source Address Negate: Select Enable to enable negated source address match when the SSL VPN settings are updated in Fortinet FortiManager.</li>
                    <li>Authentication/Portal Source Address6: Specify the CSV or the list of IPv6 source addresses of incoming traffic to be updated in the SSL VPN settings in Fortinet FortiManager.</li>
                    <li>Authentication/Portal Source Address6 Negate: Select Enable to enable negated source address match when the SSL VPN settings are updated in Fortinet FortiManager.</li>
                    <li>Authentication/Portal User Peer: Specify the name of the user peer to be used to update the SSL VPN settings in Fortinet FortiManager.</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Source Address</td>
            <td>Specify the CSV or the list of source addresses of incoming traffic to be updated in the SSL VPN settings in Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Source Address6</td>
            <td>Specify the CSV or the list of IPv6 source addresses of incoming traffic to be updated in the SSL VPN settings in Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Source Address Negate</td>
            <td>Select <strong>Enable</strong> to enable negated source address match when the SSL VPN settings are updated in Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Source Address6 Negate</td>
            <td>Select <strong>Enable</strong> to enable negated source address match when the SSL VPN settings are updated in Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>User Peer</td>
            <td>Specify the name of the user peer to be used to update the SSL VPN settings in Fortinet FortiManager.</td>
        </tr>
        <tr>
            <td>Additional SSL VPN Settings Arguments</td>
            <td>(Optional) Specify additional arguments, in JSON format, to be added during the updating of the SSL VPN settings. You can enter the arguments in the following format: <code>{&quot;field1&quot;:value1, &quot;field2&quot;:value2}</code>. For example, <code>{&quot;tunnel-ip-pools&quot;: &quot;SSLVPN_TUNNEL_ADDR1&quot;, &quot;sms-server&quot;: &quot;string&quot;, &quot;ssl-min-proto-version&quot;: &quot;default&quot; }</code></td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "url": "",
            "status": {
                "code": "",
                "message": ""
            }
        }
    ]
}</pre>

<h3>operation: Get Web Filter List</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Level</td>
            <td>Select the level type from which you want to retrieve the web filter details. You can select between ADOM or Global Type.<br />
                If you select 'ADOM', then you can specify the following parameters:
                <ul>
                    <li>ADOM: Administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified as a configuration parameter.</li>
                    <li>Web Filter Profile Name: Valid web filter profile name based on which you want to retrieve details of web filters from Fortinet FortiManager.<br />
                        <strong>Note</strong>: If this parameter is left blank or <code>null</code>, this operation returns web filters matching all values.
                    </li>
                </ul>
                If you select 'Global', then you can specify the following parameters:
                <ul>
                    <li>Web Filter Profile Name: Valid web filter profile name based on which you want to retrieve details of web filters from Fortinet FortiManager.<br />
                        <strong>Note</strong>: If this parameter is left blank or <code>null</code>, this operation returns web filters matching all values.
                    </li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Attributes in Result</td>
            <td>(Optional) Specify a string array to limit the output by returning only the specified attributes. For example, <code>[&quot;comment&quot;, &quot;extended-log&quot;, &quot;feature-set&quot;, &quot;https-replacemsg&quot;, &quot;log-all-url&quot;, &quot;name&quot;, &quot;options&quot;, &quot;ovrd-perm&quot;, &quot;post-action&quot;, &quot;replacemsg-group&quot;, &quot;web-antiphishing-log&quot;, &quot;web-content-log&quot;, &quot;web-extended-all-action-log&quot;, &quot;web-filter-activex-log&quot;, &quot;web-filter-applet-log&quot;, &quot;web-filter-command-block-log&quot;, &quot;web-filter-cookie-log&quot;, &quot;web-filter-cookie-removal-log&quot;, &quot;web-filter-js-log&quot;, &quot;web-filter-jscript-log&quot;, &quot;web-filter-referer-log&quot;, &quot;web-filter-unknown-log&quot;, &quot;web-filter-vbs-log&quot;, &quot;web-ftgd-err-log&quot;, &quot;web-ftgd-quota-usage&quot;, &quot;web-invalid-domain-log&quot;, &quot;web-url-log&quot;, &quot;wisp&quot;, &quot;wisp-algorithm&quot;, &quot;wisp-servers&quot;]</code>. If attributes are not specified, then all attributes will be returned.</td>
        </tr>
        <tr>
            <td>Filter By</td>
            <td>(Optional) You can filter the result according to a set of criteria by specifying attributes in the format <code>[[&quot;&quot;, &quot;==&quot;, &quot;&quot;]]</code></td>
        </tr>
        <tr>
            <td>Limit</td>
            <td>(Optional) Specify the maximum number of results that this operation should return.</td>
        </tr>
        <tr>
            <td>Offset</td>
            <td>(Optional) Specify the offset value to retrieve a subset of records that starts from the offset value. The offset works with the <em>Limit</em> parameter, which determines how many records to retrieve starting from the offset. Values supported are:
                <ul>
                    <li><strong>Default:<code>&quot;0&quot;</code></strong></li>
                    <li><strong>Minimum:<code>&quot;0&quot;</code></strong></li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Sort By</td>
            <td>Sort the web filters by a field and order the results. You can select to either sort the results by fields, or can order the results, or both.
                <ul>
                    <li>If you select &quot;Field&quot;, then in the <strong>Field</strong> field specify the name of the field on which you want to sort the result. Fields based on which you can sort are <code>account-key-filter, account-key-processing, antiphish, ca-cert, cnid, dn, group-filter, group-member-check, group-object-filter, group-search-base, interface, interface-select-method, member-attr, name, obtain-user-info, password, password-attr, password-expiry-warning, password-renewal, port, search-type, secondary-server, secure, server, server-identity-check, source-ip, source-port, ssl-min-proto-version, tertiary-server, two-factor, two-factor-authentication, two-factor-notification, type, user-info-exchange-server, username</code>.</li>
                    <li>If you select &quot;Order&quot;, then from the <strong>Order</strong> field, select the order in which you want to sort the result. You can select between <strong>Ascending</strong> or <strong>Descending</strong>. By default, this is set to <strong>Ascending</strong>.</li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "url": "",
            "data": [
                {
                    "antiphish": {
                        "authentication": "",
                        "check-basic-auth": "",
                        "check-uri": "",
                        "check-username-only": "",
                        "custom-patterns": "",
                        "default-action": "",
                        "domain-controller": [],
                        "inspection-entries": "",
                        "ldap": [],
                        "max-body-len": "",
                        "status": ""
                    },
                    "ftgd-wf": {
                        "exempt-quota": [],
                        "filters": [
                            {
                                "action": "",
                                "category": [],
                                "id": "",
                                "log": "",
                                "warn-duration": "",
                                "warning-prompt": ""
                            }
                        ],
                        "max-quota-timeout": "",
                        "options": "",
                        "ovrd": [],
                        "quota": "",
                        "rate-crl-urls": "",
                        "rate-css-urls": "",
                        "rate-javascript-urls": ""
                    },
                    "override": {
                        "ovrd-cookie": "",
                        "ovrd-dur": "",
                        "ovrd-dur-mode": "",
                        "ovrd-scope": "",
                        "ovrd-user-group": [],
                        "profile": [],
                        "profile-attribute": "",
                        "profile-type": ""
                    },
                    "url-extraction": "",
                    "web": {
                        "allowlist": "",
                        "blocklist": "",
                        "bword-table": [],
                        "bword-threshold": "",
                        "content-header-list": [],
                        "urlfilter-table": [],
                        "vimeo-restrict": "",
                        "youtube-restrict": ""
                    },
                    "name": "",
                    "web-content-log": "",
                    "web-filter-cookie-log": "",
                    "web-url-log": "",
                    "web-invalid-domain-log": "",
                    "web-ftgd-err-log": "",
                    "options": "",
                    "ovrd-perm": "",
                    "post-action": "",
                    "replacemsg-group": [],
                    "https-replacemsg": "",
                    "log-all-url": "",
                    "web-filter-command-block-log": "",
                    "wisp": "",
                    "wisp-algorithm": "",
                    "extended-log": "",
                    "web-extended-all-action-log": "",
                    "feature-set": ""
                }
            ],
            "status": {
                "code": "",
                "message": ""
            }
        }
    ]
}</pre>

<h3>operation: Get Blocked URLs</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Level</td>
            <td>Select the level type from which you want to retrieve the details of blocked URLs associated with the specified web filter profile. You can select between ADOM or Global Type.<br />
                If you select 'ADOM', then you can specify the following parameters:
                <ul>
                    <li>ADOM: Administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified as a configuration parameter.</li>
                    <li>Web Filter Profile Name: Valid web filter profile name that you have specified in Fortinet FortiManager for blocking or unblocking URLs. Based on our example, enter <code>default</code> in this field. See the <a href="#blockUnblockIPAdd">Blocking or Unblocking IP addresses, URLs, or applications in Fortinet FortiManager</a> section.</li>
                </ul>
                If you select 'Global', then you can specify the following parameters:
                <ul>
                    <li>Web Filter Profile Name: Valid web filter profile name that you have specified in Fortinet FortiManager for blocking or unblocking URLs. Based on our example, enter <code>default</code> in this field. See the <a href="#blockUnblockIPAdd">Blocking or Unblocking IP addresses, URLs, or applications in Fortinet FortiManager</a> section.</li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "url": "",
            "data": [
                {
                    "action": "",
                    "antiphish-action": "",
                    "dns-address-family": "",
                    "id": "",
                    "obj seq": "",
                    "status": "",
                    "type": "",
                    "url": "",
                    "web-proxy-profile": []
                }
            ],
            "status": {
                "code": "",
                "message": ""
            }
        }
    ]
}</pre>

<h3>operation: Block URL</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Level</td>
            <td>Select the level type from which you want to block the URLs specific to the web filter profile. You can select between ADOM or Global Type.<br />
                If you select 'ADOM', then you can specify the following parameters:
                <ul>
                    <li>ADOM: Administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified as a configuration parameter.</li>
                    <li>Web Filter Profile Name: Valid web filter profile name that you have specified in Fortinet FortiManager for blocking or unblocking URLs. Based on our example, enter <code>default</code> in this field. See the <a href="#blockUnblockIPAdd">Blocking or Unblocking IP addresses, URLs, or applications in Fortinet FortiManager</a> section.</li>
                    <li>URL: List of URLs that you want to block on Fortinet FortiManager. Specify the URLs in the list format, if you want to block more than one URL. For example, for a list of URLs, enter: <code>[&quot;URL1&quot;, &quot;URL2&quot;]</code> in this field. For a single URL enter: <code>example.com</code></li>
                </ul>
                If you select 'Global', then you can specify the following parameters:
                <ul>
                    <li>Web Filter Profile Name: Valid web filter profile name that you have specified in Fortinet FortiManager for blocking or unblocking URLs. Based on our example, enter <code>default</code> in this field. See the <a href="#blockUnblockIPAdd">Blocking or Unblocking IP addresses, URLs, or applications in Fortinet FortiManager</a> section.</li>
                    <li>URL: List of URLs that you want to block on Fortinet FortiManager. Specify the URLs in the list format, if you want to block more than one URL. For example, for a list of URLs, enter: <code>[&quot;URL1&quot;, &quot;URL2&quot;]</code> in this field. For a single URL enter: <code>example.com</code></li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "already_blocked": [],
    "newly_blocked": []
}</pre>

<h3>operation: Unblock URL</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Level</td>
            <td>Select the level type at which you want to unblock the URLs specific to the web filter profile. You can select between ADOM or Global Type.<br />
                If you select 'ADOM', then you can specify the following parameters:
                <ul>
                    <li>ADOM: Administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified as a configuration parameter.</li>
                    <li>Web Filter Profile Name: Valid web filter profile name that you have specified in Fortinet FortiManager for blocking or unblocking URLs. Based on our example, enter <code>default</code> in this field. See the <a href="#blockUnblockIPAdd">Blocking or Unblocking IP addresses, URLs, or applications in Fortinet FortiManager</a> section.</li>
                    <li>URL: List of URLs that you want to unblock on Fortinet FortiManager. Specify the URLs in the list format, if you want to unblock more than one URL. For example, for a list of URLs, enter: <code>[&quot;URL1&quot;, &quot;URL2&quot;]</code> in this field. For a single URL enter: <code>example.com</code></li>
                </ul>
                If you select 'Global', then you can specify the following parameters:
                <ul>
                    <li>Web Filter Profile Name: Valid web filter profile name that you have specified in Fortinet FortiManager for blocking or unblocking URLs. Based on our example, enter <code>default</code> in this field. See the <a href="#blockUnblockIPAdd">Blocking or Unblocking IP addresses, URLs, or applications in Fortinet FortiManager</a> section.</li>
                    <li>URL: List of URLs that you want to unblock on Fortinet FortiManager. Specify the URLs in the list format, if you want to unblock more than one URL. For example, for a list of URLs, enter: <code>[&quot;URL1&quot;, &quot;URL2&quot;]</code> in this field. For a single URL enter: <code>example.com</code></li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "not_exist": [],
    "newly_unblocked": []
}</pre>

<h3>operation: Get Applications Detail</h3>

<h4>Input parameters</h4>

<p>None.</p>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "url": "",
            "data": [
                {
                    "behavior": "",
                    "casi": "",
                    "cat-id": "",
                    "category": "",
                    "database": "",
                    "id": "",
                    "language": "",
                    "name": "",
                    "parameter": "",
                    "popularity": "",
                    "protocol": "",
                    "require_ssl_di": "",
                    "risk": "",
                    "shaping": "",
                    "technology": "",
                    "vendor": "",
                    "weight": ""
                }
            ],
            "status": {
                "code": "",
                "message": ""
            },
            "version": ""
        }
    ]
}</pre>

<h3>operation: Get Applications Control List</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Level</td>
            <td>Select the level type from which you want to retrieve the list of application control profiles. You can select between ADOM or Global Type.<br />
                If you select 'ADOM', then you can specify the following parameters:
                <ul>
                    <li>ADOM: Administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified as a configuration parameter.</li>
                    <li>Application Control Profile Name: Valid application control profile name based on which you want to retrieve details of the application control profile from Fortinet FortiManager.<br />
                        <strong>Note</strong>: If this parameter is left blank or <code>null</code>, this operation returns application control profiles matching all values.
                    </li>
                </ul>
                If you select 'Global', then you can specify the following parameters:
                <ul>
                    <li>Application Control Profile Name: Valid application control profile name based on which you want to retrieve details of the application control profile from Fortinet FortiManager.<br />
                        <strong>Note</strong>: If this parameter is left blank or <code>null</code>, this operation returns application control profiles matching all values.
                    </li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>{
    "id": "",
    "result": [
        {
            "url": "",
            "data": [
                {
                    "default-network-services": "",
                    "entries": [
                        {
                            "action": "",
                            "application": [],
                            "behavior": [],
                            "category": [],
                            "exclusion": [],
                            "id": "",
                            "log": "",
                            "log-packet": "",
                            "obj seq": "",
                            "parameters": "",
                            "per-ip-shaper": [],
                            "popularity": "",
                            "protocols": [],
                            "quarantine": "",
                            "quarantine-expiry": "",
                            "quarantine-log": "",
                            "rate-count": "",
                            "rate-duration": "",
                            "rate-mode": "",
                            "rate-track": "",
                            "risk": [],
                            "session-ttl": "",
                            "shaper": [],
                            "shaper-reverse": [],
                            "technology": [],
                            "vendor": []
                        }
                    ],
                    "name": "",
                    "other-application-action": "",
                    "other-application-log": "",
                    "unknown-application-action": "",
                    "unknown-application-log": "",
                    "replacemsg-group": [],
                    "options": "",
                    "app-replacemsg": "",
                    "deep-app-inspection": "",
                    "extended-log": "",
                    "enforce-default-app-port": "",
                    "control-default-network-services": "",
                    "force-inclusion-ssl-di-sigs": "",
                    "p2p-block-list": ""
                }
            ],
            "status": {
                "code": "",
                "message": ""
            }
        }
    ]
}</pre>

<h3>operation: Get Blocked Applications</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Level</td>
            <td>Select the level type from which to retrieve the list of blocked applications. You can choose between <strong>ADOM</strong> or <strong>Global Type</strong>.
                <br><strong>If you select 'ADOM'</strong>
                <ul>
                    <li>ADOM: Administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified as a configuration parameter.</li>
                    <li>Application Control Profile Name: Valid application control profile name that you have specified in Fortinet FortiManager for blocking or unblocking applications. Based on our example, enter <code>default</code> in this field. See the <a href="#blockUnblockIPAdd">Blocking or Unblocking IP addresses, URLs, or applications in Fortinet FortiManager</a> section.</li>
                </ul>
                If you select 'Global', then you can specify the following parameters:
                <ul>
                    <li>Application Control Profile Name: Valid application control profile name that you have specified in Fortinet FortiManager for blocking or unblocking applications. Based on our example, enter <code>default</code> in this field. See the <a href="#blockUnblockIPAdd">Blocking or Unblocking IP addresses, URLs, or applications in Fortinet FortiManager</a> section.</li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>[
    {
        "behavior": "",
        "casi": "",
        "cat-id": "",
        "category": "",
        "database": "",
        "id": "",
        "language": "",
        "name": "",
        "parameter": "",
        "popularity": "",
        "protocol": "",
        "require_ssl_di": "",
        "risk": "",
        "shaping": "",
        "technology": "",
        "vendor": "",
        "weight": ""
    }
]</pre>

<h3>operation: Block Application</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Level</td>
            <td>Select the level type in which to block the applications. You can choose between <strong>ADOM</strong> or <strong>Global Type</strong>.<br />
                If you select 'ADOM', then you can specify the following parameters:
                <ul>
                    <li>ADOM: Administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified as a configuration parameter.</li>
                    <li>Application Control Profile Name: Valid application control profile name that you have specified in Fortinet FortiManager for blocking or unblocking applications. Based on our example, enter <code>default</code> in this field. See the <a href="#blockUnblockIPAdd">Blocking or Unblocking IP addresses, URLs, or applications in Fortinet FortiManager</a> section.</li>
                    <li>Application Names: List of application names that you want to block on Fortinet FortiManager. Specify the application names in the list format, if you want to block more than one application. For example, for a list of applications, enter: <code>[&quot;Application_Name1&quot;, &quot;Application_Name2&quot;]</code> in this field. For a single application enter: <code>Application_Name</code></li>
                </ul>
                If you select 'Global', then you can specify the following parameters:
                <ul>
                    <li>Application Control Profile Name: Valid application control profile name that you have specified in Fortinet FortiManager for blocking or unblocking applications. Based on our example, enter <code>default</code> in this field. See the <a href="#blockUnblockIPAdd">Blocking or Unblocking IP addresses, URLs, or applications in Fortinet FortiManager</a> section.</li>
                    <li>Application Names: List of application names that you want to block on Fortinet FortiManager. Specify the application names in the list format, if you want to block more than one application. For example, for a list of applications, enter: <code>[&quot;Application_Name1&quot;, &quot;Application_Name2&quot;]</code> in this field. For a single application enter: <code>Application_Name</code></li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>[
    {
        "name": "",
        "message": "",
        "status": ""
    }
]</pre>

<h3>operation: Unblock Application</h3>

<h4>Input parameters</h4>

<table border="1">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Level</td>
            <td>Select the level type in which to unblock applications. You can choose between <strong>ADOM</strong> or <strong>Global Type</strong>.<br />
                <br><strong>If you select 'ADOM'</strong>
                <ul>
                    <li>ADOM: Administrative domain name (ADOM) of the Fortinet FortiManager server to which you will connect and perform the automated operations. The ADOM that you specify here overwrites the ADOM that you have specified as a configuration parameter.</li>
                    <li>Application Control Profile Name: Valid application control profile name that you have specified in Fortinet FortiManager for blocking or unblocking applications. Based on our example, enter <code>default</code> in this field. See the <a href="#blockUnblockIPAdd">Blocking or Unblocking IP addresses, URLs, or applications in Fortinet FortiManager</a> section.</li>
                    <li>Application Names: List of application names that you want to unblock on Fortinet FortiManager. Specify the application names in the list format, if you want to unblock more than one application. For example, for a list of applications, enter: <code>[&quot;Application_Name1&quot;, &quot;Application_Name2&quot;]</code> in this field. For a single application enter: <code>Application_Name</code></li>
                </ul>
                If you select 'Global', then you can specify the following parameters:
                <ul>
                    <li>Application Control Profile Name: Valid application control profile name that you have specified in Fortinet FortiManager for blocking or unblocking applications. Based on our example, enter <code>default</code> in this field. See the <a href="#blockUnblockIPAdd">Blocking or Unblocking IP addresses, URLs, or applications in Fortinet FortiManager</a> section.</li>
                    <li>Application Names: List of application names that you want to unblock on Fortinet FortiManager. Specify the application names in the list format, if you want to unblock more than one application. For example, for a list of applications, enter: <code>[&quot;Application_Name1&quot;, &quot;Application_Name2&quot;]</code> in this field. For a single application enter: <code>Application_Name</code></li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

<h4>Output</h4>

<p>The output contains the following populated JSON schema:</p>

<pre>[
    {
        "name": "",
        "message": "",
        "status": ""
    }
]</pre>

<h2>Included playbooks</h2>

<p>The <code><em>Sample - Fortinet Fortimanager - 4.0.0</em></code> playbook collection comes bundled with the Fortinet FortiManager connector. These playbooks contain steps using which you can perform all supported actions. You can see bundled playbooks in the <strong>Automation</strong> &gt; <strong>Playbooks</strong> section in FortiSOAR&trade; after importing the Fortinet FortiManager connector.</p>

<ul>
    <li>ADOM Level Block IP Address</li>
    <li>ADOM Level Get Blocked IP Addresses</li>
    <li>ADOM Level Unblock IP Address</li>
    <li>Assign Global Policy Package</li>
    <li>Block Application</li>
    <li>Block URL</li>
    <li>Create Address</li>
    <li>Create Address Group</li>
    <li>Create Custom Service</li>
    <li>Create Firewall Policy</li>
    <li>Create Incident</li>
    <li>Create LDAP Server</li>
    <li>Create Policy Package</li>
    <li>Create Service Group</li>
    <li>Create User Group</li>
    <li>Delete Address</li>
    <li>Delete Address Group</li>
    <li>Delete Custom Service</li>
    <li>Delete Firewall Policy</li>
    <li>Delete LDAP Server</li>
    <li>Delete Policy Package</li>
    <li>Delete Service Group</li>
    <li>Delete User Group</li>
    <li>&gt; Fortinet-FortiManager &gt; Fetch and Create</li>
    <li>Fortinet-FortiManager &gt; Ingest</li>
    <li>Fortinet-FortiManager &gt; Fetch Incident Events</li>
    <li>Get Address Groups List</li>
    <li>Get Addresses List</li>
    <li>Get Applications Control List</li>
    <li>Get Applications Detail</li>
    <li>Get Blocked Applications</li>
    <li>Get Blocked URLs</li>
    <li>Get Custom Services List</li>
    <li>Get Device Groups List</li>
    <li>Get Device List</li>
    <li>Get Dynamic Interface List</li>
    <li>Get Event Details</li>
    <li>Get Events</li>
    <li>Get Events Related to Incident</li>
    <li>Get Installation Policy Package Status</li>
    <li>Get LDAP Server List</li>
    <li>Get SSL VPN Settings</li>
    <li>Get Service Categories List</li>
    <li>Get Service Groups List</li>
    <li>Get User Groups List</li>
    <li>Get Web Filter List</li>
    <li>Global Level Block IP Address</li>
    <li>Global Level Get Blocked IP Addresses</li>
    <li>Global Level Unblock IP Address</li>
    <li>Install Policy</li>
    <li>List ADOM Firewall Policies</li>
    <li>List ADOM Policy Package</li>
    <li>List Global Firewall Policies</li>
    <li>List Global Policy Package</li>
    <li>List Incident</li>
    <li>Move Firewall Policy</li>
    <li>Re-install Policy</li>
    <li>Unblock Application</li>
    <li>Unblock URL</li>
    <li>Update Address</li>
    <li>Update Address Group</li>
    <li>Update Custom Service</li>
    <li>Update Firewall Policy</li>
    <li>Update Incident</li>
    <li>Update LDAP Server</li>
    <li>Update Policy Package</li>
    <li>Update SSL VPN Settings</li>
    <li>Update Service Group</li>
    <li>Update User Group</li>
</ul>

<p><strong>Note</strong>: If you are planning to use any of the sample playbooks in your environment, ensure that you clone those playbooks and move them to a different collection since the sample playbook collection gets deleted during the connector upgrade and delete.</p>

<h2><a id="dataIngestion" name="dataIngestion"></a>Data Ingestion Support</h2>

<p>Use the Data Ingestion Wizard to easily ingest data into FortiSOAR&trade; by pulling incidents from Fortinet FortiManager. Currently, &quot;incidents&quot; in Fortinet FortiManager are mapped to &quot;alerts&quot; in FortiSOAR&trade;. For more information on the Data Ingestion Wizard, see the &quot;Connectors Guide&quot; in the FortiSOAR&trade; product documentation.</p>

<h3>Configure Data Ingestion</h3>

<p>You can configure data ingestion using the <strong>Data Ingestion Wizard</strong> to seamlessly map the incoming Fortinet FortiManager &quot;Incidents&quot;&nbsp;to FortiSOAR&trade; &quot;Alerts&quot;.</p>

<p>The Data Ingestion Wizard enables you to configure the scheduled pulling of data from Fortinet FortiManager into FortiSOAR&trade;. It also lets you pull some sample data from Fortinet FortiManager using which you can define the mapping of data between Fortinet FortiManager and FortiSOAR&trade;. The mapping of common fields is generally already done by the Data Ingestion Wizard; users are mostly required to only map any custom fields that are added to the Fortinet FortiManager incident.</p>

<ol>
    <li>To begin configuring data ingestion, click <strong>Configure Data Ingestion</strong> on the Fortinet FortiManager connector&rsquo;s &quot;Configurations&quot; page.&nbsp;<br />
        Click <strong>Let&rsquo;s Start by fetching some data</strong>, to open the <strong>Fetch Sample Data</strong> screen.<br />
        <img src="./res/ingestion-00.png" /><br />
        Sample data is required to create a field mapping between Fortinet FortiManager data and FortiSOAR&trade;. The sample data is pulled from connector actions or ingestion playbooks.
    </li>
    <li>On the <strong>Fetch Data</strong> screen, provide the configurations required to fetch Fortinet FortiManager data.<br />
        Users can select to pull data from Fortinet FortiManager by specifying the last X minutes in which the incidents have been created or updated in Fortinet FortiManager and the administrative domain name (ADOM) of the Fortinet FortiManager server from which your want to fetch incidents. You can also specify a query to filter data retrieved from Fortinet FortiManager and can also specify additional parameters such as the category, severity, and status of the incidents to be fetched from Fortinet FortiManager. The fetched data is used to create a mapping between the Fortinet FortiManager data and FortiSOAR&trade; alerts.<br />
        Once you have completed specifying the configurations, click <strong>Fetch Data</strong>.</li>
    <li>
        <p>On the <strong>Field Mapping</strong> screen, map the fields of a Fortinet FortiManager incident to the fields of an alert present in FortiSOAR&trade;.&nbsp;<br />
            To map a field, click the key in the sample data to add the <strong>Jinja</strong> value of the field. For example, to map the <em>status</em>parameter of a Fortinet FortiManager incident to the <em>state</em> parameter of a FortiSOAR&trade; alert, click the <strong>State</strong> field and then click the <strong>status</strong> field to populate its keys: &nbsp;<br />
            <img src="./res/ingestion-01.png" /><br />
            For more information on field mapping, see the <em>Data Ingestion</em>chapter in the &quot;Connectors Guide&quot; in the FortiSOAR&trade; product documentation. Once you have completed mapping the fields, click <strong>Save Mapping &amp; Continue</strong>.
        </p>
    </li>
    <li>
        <p>Use the <strong>Scheduling</strong> screen to configure schedule-based ingestion, i.e., specify the polling frequency to Fortinet FortiManager, so that the content gets pulled from the Fortinet FortiManager integration into FortiSOAR&trade;.&nbsp;<br />
            On the Scheduling screen, from the <strong>Do you want to schedule the ingestion?</strong> drop-down list, select <strong>Yes</strong>. &nbsp; &nbsp;<br />
            In the <strong>Configure Schedule Settings</strong> section, specify the Cron expression for the schedule. For example, if you want to pull data from Fortinet FortiManager every 5 minutes, click <strong>Every X Minute,</strong> and in the minute box enter <code>*/5</code>. This would mean that based on the configuration you have set up, data, i.e., incidents will be pulled from Fortinet FortiManager every 5 minutes.<br />
            <img src="./res/ingestion-02.png" /><br />
            Once you have completed scheduling, click <strong>Save Settings&nbsp;&amp; Continue</strong>.
        </p>
    </li>
    <li>
        <p>The <strong>Summary</strong> screen displays a summary of the mapping done, and it also contains links to the Ingestion playbooks. Click <strong>Done</strong> to complete the data ingestion and exit the Data Ingestion Wizard.</p>
    </li>
</ol>

<ul>
</ul>

<h2><a id="blockUnblockIPAdd" name="blockUnblockIPAdd"></a>Blocking or Unblocking IP addresses, URLs, or applications in Fortinet FortiManager</h2>

<ol>
    <li>
        <p>Log on to the Fortinet FortiManager server with the necessary credentials.</p>
    </li>
    <li>
        <p>To block or unblock an IP address, you must create a policy for IP addresses on the Fortinet FortiManager server. The following steps define the process of adding a policy:</p>
        <ol>
            <li>In <code>Policy &amp; Objects &gt; Policy Packages</code>, click <strong>IPv4 Policy</strong> or <strong>Firewall Policy</strong> to create a policy for IPv4 with the following conditions.<br />
                IPv4 Source Address = Blocked_IPs<br />
                IPv4 Destination Address = Blocked_IPs<br />
                Schedule = always<br />
                Service = ALL<br />
                Action = DENY<br />
                <strong>Note</strong>: You can create an IPv6 policy in a similar manner.<br />
                For more information on address group exclusions, see the <a href="https://docs.fortinet.com/document/fortimanager/6.2.2/administration-guide/547958/create-a-new-object" rel="noopener noreferrer" target="_blank">Create a new object topic in the FortiManager 6.2.2 Administration Guide</a>.
            </li>
            <li>In <code>Policy &amp; Objects &gt; Object Configuration</code>, click <strong>Address Group</strong> to create an address group with the following conditions.<br />
                Group Name = Blocked_IPs<br />
                Member = none<br />
                Show in address list = enable<br />
                For more information on creating address groups and address group exclusions, see the <a href="https://docs.fortinet.com/document/fortimanager/6.2.2/administration-guide/834430/ip-policies" rel="noopener noreferrer" target="_blank">IP policies topic in the FortiManager 6.2.2 Administration Guide</a>.</li>
        </ol>
    </li>
    <li>To block or unblock a URL, you must create a profile for blocking or unblocking static URLs on the Fortinet FortiManager server. For information on creating web filters, see the 'Web Filter' topic at <a href="https://docs.fortinet.com/document/fortimanager/6.2.2/administration-guide/795923/web-filter" target="_blank">https://docs.fortinet.com/document/fortimanager/6.2.2/administration-guide/795923/web-filter</a>. The following steps define the process of adding a policy:
        <ol>
            <li>In <strong>Security Profiles</strong>, click <strong>Web Filter</strong> to create a new profile for blocking or unblocking static URLs or use the default profile.&nbsp;<br />
                <strong>Note</strong>: Ensure that the &quot;URL Filter&quot; is enabled.&nbsp;
            </li>
            <li>Enter the Web Filter Profile name on the action page. For our example, we have named this 'URL Block Policy'.</li>
        </ol>
    </li>
    <li>To block or unblock an application, you must create a profile for blocking or unblocking applications on the Fortinet FortiManager server. The following steps define the process of adding a policy:&nbsp;
        <ol>
            <li>In <strong>Security Profiles</strong>, click <strong>Application Control</strong> to create a new profile for blocking or unblocking applications or use the default profile.</li>
            <li>Enter the policy name on the configuration page. For our example, we have named this?'App Block Policy'. When you are configuring your Fortinet FortiManager connector in FortiSOAR&trade;, you must use the Application Control Profile name that you have specified in this step as your 'Application Control Profile Name' action parameter.&nbsp;<br />
                For information on adding application controls, see the 'Application Control' topic at <a href="https://docs.fortinet.com/document/fortimanager/6.2.2/administration-guide/966512/application-control" target="_blank">https://docs.fortinet.com/document/fortimanager/6.2.2/administration-guide/966512/application-control</a>.</li>
        </ol>
    </li>
    <li>Users who are configuring Fortinet FortiManager for the first time have to perform the following steps for the 'Install' Policy:
        <ol>
            <li>Add devices to the <strong>Installation Targets</strong> where the user wants to install the IPv4/Firewall policy. &nbsp;&nbsp;</li>
            <li>Navigate to the Device Manager select the Device that is specified in the installation target and click <strong>Install</strong>.</li>
            <li>Click <strong>Install Policy Package &amp; Device Settings</strong>and select the policy package where the IPv4 Policy or Firewall Policy is created. &nbsp;</li>
            <li>Run the 'Install Wizard' completely.</li>
        </ol>
    </li>
    <li>Users who are configuring Fortinet FortiManager for the first time have to perform the following steps for the 'Assign Global Policy Package':
        <ol>
            <li>Add ADOM to the <strong>Assignment</strong> where the user wants to assign the Global Policy Package. For more information see the <a href="https://docs.fortinet.com/document/fortimanager/6.2.2/administration-guide/53760/assign-a-global-policy-package" target="_blank">Assign a global policy package</a> section in the FortiManager document</li>
            <li>Select the ADOM that you have specified in the assignment. &nbsp;</li>
            <li>Run the 'Assign Wizard' completely.</li>
        </ol>
    </li>
</ol>