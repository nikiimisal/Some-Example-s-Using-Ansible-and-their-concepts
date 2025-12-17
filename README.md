<h1>⚡ Create a Shortcut (Alias) for Ansible Playbook  </h1>

- If you do not want to type the full command every time,  
- you can create a **shortcut (alias)** for it.

---

📝 Step 1: Open Profile File  
Open the system profile file using the command:

```
nano /etc/profile
```

---

➕ Step 2: Add Alias  
Scroll to the **bottom of the file** and add the following line:

```
alias ap='ansible-playbook'
```

This creates a shortcut where `ap` will work the same as `ansible-playbook`.

---

🔄 Step 3: Apply the Changes  
To apply the changes without restarting the system, run:

```
source /etc/profile
```

---

✅ Now you can run Ansible playbooks using the shortcut command:

```
ap ping.yml
```

This makes working with Ansible faster and easier 🚀😄





<h1>📘 Ansible Example's</h1>

##   Example  1 – Ping Playbook (Easy & Beginner Friendly) 🧠✨

🔍 What does the ping command do?  

- The `ping` command is used to **check connectivity**. 

For example:<br>
- `ping google.com` → checks internet connectivity 🌐  
- `ping localhost` → checks local machine connectivity 💻  

👉 Till now, we were checking connectivity **manually** using ping.  
Now we will do the **same thing using Ansible automation** ⚙️🤖.

---

🛠️ How will we do this in Ansible?  
We will write a **playbook (YAML file)** that performs the ping operation automatically.

---

🧑‍💻 Step 1: Create Local Workspace  
<br>
- On your **local machine**, create a folder named **ansible**.  
- This folder will act as your workspace.

📂 Open **Git Bash** inside this folder  
🧑‍🎨 Then open the folder in **VS Code**

---

📝 Step 2: Create Playbook File  

- Inside VS Code, create a new file named:
  `ping.yml`

Add the following content inside the file 👇
```
# ping command -> check connectivity
---

- name: Check the connectivity
  hosts: localhost
  tasks:
    - name: check the connectivity using ping command
      ansible.builtin.ping:
```

---

🧾 Step 3: Copy and Paste into Terminal

After creating the `ping.yml` file in VS Code,
save the file, then copy the file content
and paste it into the terminal where Ansible is installed.

This ensures that the playbook is available and ready to be executed from the terminal.

---

🧪 Step 4: Syntax Check (Like Terraform Plan)

In Terraform, before running `terraform apply`, we run `terraform plan`

to check whether:
- the syntax is correct
- everything is properly defined

Similarly, in Ansible, we use the following command to check for syntax errors before running the playbook:
```
ansible-playbook ping.yml --syntax-check
```

If no errors are displayed, it means the playbook syntax is correct and safe to run ✅

   <p align="center">
  <img src="https://github.com/nikiimisal/Some-Example-s-Using-Ansible/blob/main/img/Screenshot%202025-12-16%20195250.png?raw=true" width="500" alt="Initialize Repository Screenshot">
</p>


---

▶️ Step 5: Run the Playbook

After a successful syntax check, run the playbook using:
```
ansible-playbook ping.yml
```

If you have created a shortcut or alias, you can also run:
```
ap ping.yml
```

   <p align="center">
  <img src="https://github.com/nikiimisal/Some-Example-s-Using-Ansible/blob/main/img/Screenshot%202025-12-16%20222426.png?raw=true" width="500" alt="Initialize Repository Screenshot">
</p>


---

📊 Step 6: Verify Output

In Ansible, status codes are shown after a command or playbook is executed.<br>
After execution, if you see output like:
```
ok=2
```
✅ This means the task was executed successfully<br>
   and all defined tasks completed without any errors. 🎉

   <p align="center">
  <img src="https://github.com/nikiimisal/Some-Example-s-Using-Ansible/blob/main/img/Screenshot%202025-12-16%20222426.png?raw=true" width="500" alt="Initialize Repository Screenshot">
</p>

---

##  Ansible Example  2 –Create a folder using Ansible

```
---

- name: Create a file
  hosts: localhost
  tasks:
    - name: create ansible file
      ansible.builtin.file:
        path: /root/ansible.txt
        state: touch
```

<p align="center">
  <img src="https://github.com/nikiimisal/Some-Example-s-Using-Ansible/blob/main/img/Screenshot%202025-12-16%20224226.png?raw=true" width="500" alt="Initialize Repository Screenshot">
</p>

---


