# 📘 Day 2 – Create Multiple Linux Users Using a Bash Script

## 🟢 Task Name
Create Multiple Linux Users Using a Bash Script

---

# 🎯 Objective (Why are we doing this?)
In real servers, creating users one by one is:

- Time-consuming  
- Error-prone  
- Not scalable  

👉 DevOps focuses on **automation**.  
So instead of creating users manually, we will automate user creation using a Bash script.

---

# 🧠 What You Will Learn in Day 2
By completing this task, you will learn:

- Basic Linux user management  
- How Bash scripts work  
- How automation saves time in DevOps  
- How real system admins & DevOps engineers work  

---

# ⚙️ Prerequisites
Before starting, make sure:

- You have Linux OS (Ubuntu / Amazon Linux / VM / WSL)  
- You have sudo/root access  
- Basic terminal knowledge  

---

# 🧩 Step 1: Login to Your Linux Machine

Open your terminal and login to your Linux system.

Check your current user:

```bash
whoami
```

---

# 🧩 Step 2: Create a File with Usernames

We will store all usernames in a file.

Create a file:

```bash
nano users.txt
```

Add usernames (example):

```
dev1
dev2
test1
test2
qa1
qa2
admin1
admin2
monitor1
monitor2
```

Save and exit:

- CTRL + X  
- Press Y  
- Press Enter  

📌 Why this step?  
So we can easily manage and reuse user lists.

---

# 🧩 Step 3: Create Bash Script for User Creation

Create script file:

```bash
nano create_users.sh
```

Paste this code:

```bash
#!/bin/bash

for user in $(cat users.txt)
do
sudo useradd -m $user
echo "User $user created successfully"
done
```

---

# 🧩 Step 4: Give Execute Permission to Script

```bash
chmod +x create_users.sh
```

---

# 🧩 Step 5: Run the Script

```bash
./create_users.sh
```

---

# 🧩 Step 6: Verify Users Are Created

```bash
cat /etc/passwd | grep dev
```

or

```bash
ls /home
```

---

# 🧠 Important Concepts

### useradd
Creates a new Linux user

### -m
Creates home directory

### for loop
Runs commands for multiple users

### Bash Script
Automates Linux commands
