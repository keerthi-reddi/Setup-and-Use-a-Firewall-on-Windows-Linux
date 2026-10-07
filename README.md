# Setup-and-Use-a-Firewall-on-Windows-Linux
🎯 Objective
Configure and test basic firewall rules to allow or block network traffic on specific ports. Understand how firewalls filter traffic and manage network security through port-based rules.
**Specific Goals:**
- ✅ Open firewall configuration tool
- ✅ List current firewall rules
- ✅ Add a rule to block inbound traffic on port 23 (Telnet)
- ✅ Test the rule to verify it works
- ✅ Remove the test rule to restore original state
  
## 📝 What I Did
### Phase 1: Firewall Configuration Setup
#### Step 1: Opened Windows Firewall
- **Method:** Keyboard shortcut
- **Command:** `Win + R` → `wf.msc` → Enter
- **Result:** Windows Defender Firewall with Advanced Security opened
- **Location:** Advanced Security Console
- **Action:** Navigated to Inbound Rules section

#### Step 2: Reviewed Current Rules
- **Location:** Windows Firewall → Inbound Rules
- **Action:** Examined existing firewall rules
- **Observations:** 
  - Multiple default rules present
  - Rules for Windows services and applications
  - Default policy: Deny inbound, Allow outbound
- **Documentation:** Screenshot taken of current state

#### Step 3: Created Test Rule to Block Port 23
- **Rule Configuration:**
  - Rule Type: Port-based
  - Protocol: TCP
  - Port: 23 (Telnet)
  - Action: Block the connection
  - Profiles: Domain, Private, Public (all enabled)
  - Rule Name: Block Telnet Test
  - Description: Test rule to block port 23 (Telnet)

#### Step 4: Verified Rule Creation
- **Verification Method:** GUI inspection
- **Result:** Rule appeared in Inbound Rules list
- **Details Confirmed:**
  - Name: Block Telnet Test
  - Action: Block
  - Protocol: TCP
  - Port: 23
  - Status: Active
- **Documentation:** Screenshot taken

### Phase 2: Testing the Firewall Rule
#### Step 5: Tested the Blocking Rule
**Test Command 1: Telnet Connection Test**
telnet localhost 23
**Output:**
Connecting to localhost...Could not open connection to the host, on port 23: Connect failed
**Analysis:** ✅ Connection BLOCKED successfully
**Test Command 2: Netstat Port Check**
netstat -an | findstr :23
**Output:** (No output returned)
**Analysis:** ✅ Port 23 not listening/accessible
**Test Command 3: PowerShell Verification**
Test-NetConnection -ComputerName localhost -Port 23
**Output:**
ComputerName : localhost RemotePort : 23 TcpTestSucceeded : False
**Analysis:** ✅ Connection test failed (blocked as expected)

### Phase 3: Cleanup and Documentation
#### Step 6: Removed Test Rule
- **Location:** Windows Firewall → Inbound Rules
- **Process:**
  1. Right-clicked "Block Telnet Test" rule
  2. Selected "Delete"
  3. Confirmed deletion
- **Verification:** Rule no longer appears in list
- **Documentation:** Screenshot taken of cleaned-up state
#### Step 7: Documented All Steps
- Created comprehensive documentation files
- Recorded all commands used
- Captured screenshots at each stage
- Prepared for submission


