# <span style="color:blue;">🔒 Configuring Domain User Password Policy</span>

This document provides a comprehensive guide for configuring password policies for domain user accounts in a Windows environment using Group Policy Management. Properly configuring password policies is critical for securing user accounts and protecting sensitive information.

---

## <span style="color:blue;">⚙️ Accessing Group Policy Management</span>

1. Open the **Group Policy Management** console by navigating to **Tools** > **Group Policy Management**.
2. In the left pane, **right-click** on the **Default Domain Policy** and select **Edit**.
3. Navigate to:  
   `Computer Configuration > Policies > Windows Settings > Security Settings > Account Policies > Password Policy`.

---

## <span style="color:blue;">🔑 Password Policy Settings</span>

### 1. <span style="color:blue;">🔒 Enforce Password History</span>  
This policy defines the number of unique new passwords a user must have before an old password can be reused. This helps prevent users from cycling through their old passwords.

- **Range**: 0 to 24 passwords  
- **Default**:  
  - **24** on domain controllers  
  - **0** on stand-alone servers  
- **Best Practice**: For effective enforcement of password history, enable the **Minimum Password Age** policy to prevent users from bypassing password history by quickly changing their passwords.

---

### 2. <span style="color:blue;">📅 Maximum Password Age</span>  
This policy determines the maximum period a password can be used before it must be changed. The goal is to limit the amount of time a password is valid to reduce the risk of unauthorized access.

- **Range**: 1 to 999 days (or set to 0 to disable expiration)  
- **Best Practice**: Set password expiration to **30–90 days** to balance security and user convenience.  
- **Default**: **42 days** on domain controllers.

---

### 3. <span style="color:blue;">⏳ Minimum Password Age</span>  
This setting defines the minimum duration a password must be in use before the user can change it. By enforcing a minimum password age, users are prevented from repeatedly changing their password to bypass other policies, such as **Enforce Password History**.

- **Range**: 1 to 998 days (or set to 0 for no restriction)  
- **Default**:  
  - **1** on domain controllers  
  - **0** on stand-alone servers  
- **Tip**: Set a minimum password age greater than 0 to ensure the **Enforce Password History** policy is effective.

---

### 4. <span style="color:blue;">🔢 Minimum Password Length</span>  
This policy sets the minimum number of characters required for a password. A longer password typically provides better security.

- **Range**: 1 to 14 characters (or set to 0 for no password requirement)  
- **Default**:  
  - **7** on domain controllers  
  - **0** on stand-alone servers

---

### 5. <span style="color:blue;">🔐 Password Complexity Requirements</span>  
When enabled, this policy enforces the following complexity requirements to enhance password strength:

- Passwords must be at least **six characters** in length.  
- Passwords must contain characters from at least **three of the following four categories**:  
  - Uppercase English letters (A-Z)  
  - Lowercase English letters (a-z)  
  - Base-10 digits (0-9)  
  - Non-alphabetic characters (e.g., !, $, #, %)  
- **Default**: Enabled on domain controllers, disabled on stand-alone servers.

---

### 6. <span style="color:blue;">🔑 Store Passwords Using Reversible Encryption</span>  
This policy determines whether passwords are stored using reversible encryption. This method is less secure and should only be used when absolutely necessary for specific applications.

- **Default**: Disabled

---

### 7. <span style="color:blue;">⏲️ Account Lockout Duration</span>  
This setting determines how long an account remains locked after reaching the account lockout threshold. Locking out accounts after multiple failed login attempts helps prevent brute force attacks.

- **Range**: 0 to 99,999 minutes (or set to 0 for manual unlocking)  
- **Default**: None (only applies when an account lockout threshold is defined)

---

### 8. <span style="color:blue;">🚫 Account Lockout Threshold</span>  
This policy determines the number of failed login attempts that result in an account being locked. Locking out accounts after multiple failed attempts reduces the risk of brute-force attacks.

- **Range**: 0 to 999 failed login attempts (set to 0 to disable lockout)  
- **Default**: **0** (no account lockout)

---

### 9. <span style="color:blue;">🔄 Reset Account Lockout Counter After</span>  
This policy defines the number of minutes that must pass after a failed login attempt before the failed login attempt counter resets to 0. It helps manage failed login attempts and resets the counter after a specified period.

- **Range**: 1 minute to 99,999 minutes  
- **Default**: None (only applies when an account lockout threshold is defined)

---

## <span style="color:blue;">💡 Best Practices</span>

To optimize security while maintaining usability, consider the following best practices for password policies:

- Set **password expiration** to **30–90 days** to ensure timely updates and minimize the risk of password compromise.  
- Enforce **password complexity requirements** to ensure strong passwords are used throughout the organization.  
- Enable **account lockout** policies to prevent brute-force attacks by limiting the number of failed login attempts.

---
