### Deploying Active Directory

#### **Install Active Directory**
1. Log in to `DC-1`.
2. Install Active Directory Domain Services (AD DS).
3. Promote `DC-1` as a Domain Controller and set up a new forest (e.g., `mydomain.com`).
4. Restart `DC-1` and log in as `mydomain.com\labuser`.

<p>
<img src="https://i.imgur.com/xlMwDNZ.png" height="80%" width="80%" alt="Lab 5"/>
</p>

<p>
<img src="https://i.imgur.com/TRXeQJq.png" height="80%" width="80%" alt="Lab 5"/>
</p>

#### **Create a Domain Admin User**
1. Open Active Directory Users and Computers (ADUC).
2. Create an Organizational Unit (OU) named `_EMPLOYEES`.
3. Create another OU named `_ADMINS`.
4. Add a new user:
   - Name: `Jane Doe`
   - Username: `jane_admin`
   - Password: `Cyberlab123!`
5. Add `jane_admin` to the `Domain Admins` security group.
6. Log out and log back in as `mydomain.com\jane_admin`.

<p>
<img src="https://i.imgur.com/Jq4eZPI.png" height="80%" width="80%" alt="Lab 5"/>
</p>

<p>
<img src="https://i.imgur.com/fjfBu5v.png" height="80%" width="80%" alt="Lab 5"/>
</p>

<p>
<img src="https://i.imgur.com/OTBl5tT.png" height="80%" width="80%" alt="Lab 5"/>
</p>

#### **Join Client-1 to the Domain**
1. Log in as the local admin and join `Client-1` to the domain.
2. Create a new OU titled '_CLIENTS' & add `Client-1` in ADUC to `_CLIENTS`.

<p>
<img src="https://i.imgur.com/2xHyKvs.png" height="80%" width="80%" alt="Lab 5"/>
</p>

<p>
<img src="https://i.imgur.com/kcyfdIP.png" height="80%" width="80%" alt="Lab 5"/>
</p>

---

### Part 3: Creating Users with PowerShell

#### **Setup Remote Desktop for Domain Users**
1. Log into `Client-1` as `mydomain.com\jane_admin`.
2. Open System Properties and enable Remote Desktop.
3. Allow "domain users" access to Remote Desktop.

<p>
<img src="https://i.imgur.com/hK9sB8R.png" height="80%" width="80%" alt="Lab 5"/>
</p>

#### **Create Users with PowerShell**
1. Log in to `DC-1` as `jane_admin`.
2. Open PowerShell ISE as an administrator.
3. Create multiple new users using a script (script link: https://github.com/joshmadakor1/AD_PS/blob/master/Generate-Names-Create-Users.ps1).
4. Verify users appear in the `_EMPLOYEES` OU in ADUC.
5. Attempt to log into `Client-1` with one of the created accounts.

<p>
<img src="https://i.imgur.com/RAgS5GM.png" height="80%" width="80%" alt="Lab 5"/>
</p>

<p>
<img src="https://i.imgur.com/Qe1OaOn.png" height="80%" width="80%" alt="Lab 5"/>
</p>

<p>
<img src="https://i.imgur.com/iXBrDci.png" height="80%" width="80%" alt="Lab 5"/>
</p>

---

### Part 4: Group Policy and Managing Accounts

#### **Account Lockout Configuration**
1. Log in to `DC-1`.
2. Open Group Policy Management.
3. Edit the Default Domain Policy:
   - Set account lockout threshold to 5 invalid attempts.
4. Attempt to log in with a user account using incorrect passwords. Observe the account lockout behavior.
5. Unlock the account in ADUC and reset the password.

<p>
<img src="https://i.imgur.com/4xZVZxJ.png" height="80%" width="80%" alt="Lab 5"/>
</p>

<p>
<img src="https://i.imgur.com/KW95ZOG.png" height="80%" width="80%" alt="Lab 5"/>
</p>

<p>
<img src="https://i.imgur.com/uWoFU61.png" height="80%" width="80%" alt="Lab 5"/>
</p>

#### **Enable and Disable Accounts**
1. Disable a user account in ADUC.
2. Attempt to log in with the disabled account and observe the error message.
3. Re-enable the account and log in successfully.

<p>
<img src="https://i.imgur.com/CUUcX8S.png" height="80%" width="80%" alt="Lab 5"/>
</p>

<p>
<img src="https://i.imgur.com/TkMtlW1.png" height="80%" width="80%" alt="Lab 5"/>
</p>

<p>
<img src="https://i.imgur.com/KWKL3VZ.png" height="80%" width="80%" alt="Lab 5"/>
</p>

#### **Observing Logs**
1. Review authentication and account-related logs in Event Viewer:
   - Log on `DC-1` for domain-level events (shown below).
   - Log on `Client-1` for local events.

<p>
<img src="https://i.imgur.com/YwM0mgQ.png" height="80%" width="80%" alt="Lab 5"/>
</p>

---

### Completion

Congratulations! You have successfully deployed and configured an on-premises Active Directory environment in Azure.# Deploying-Active-Directory
