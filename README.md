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

## Example 3 - This playbook is used to create a directory named aws inside /home/ec2-user on the local machine using Ansible automation.

```
---

- name: Create a folder inside /home/ec2-user/aws
  hosts: localhost
  tasks:
    - name: Create aws directory
      ansible.builtin.file:
        path: /home/ec2-user/aws
        state: directory
        mode: 0700                             # starting 0 means unmask  1 means mask
```


<p align="center">
  <img src="" width="500" alt="Initialize Repository Screenshot">
</p>

---

##  Example 4 - This playbook copies a file named ansible.txt from /root directory to /home/ec2-user/aws on the local machine.

```
---
- name: copy file from one directory to another
  hosts: localhost
  tasks:
  - name: copy file from /root/ansible.txt to /home/ec2-user/aws/
    ansible.builtin.copy:
      src: /root/ansible.txt
      dest: /home/ec2-user/aws/ansible.txt
```

<p align="center">
  <img src="" width="500" alt="Initialize Repository Screenshot">
</p>


---
 ##  Example  5  - This playbook installs the `tree` package on the local machine using Ansible.

```
---
- name: install tree package
  hosts: localhost
  tasks:
  - name: install tree
    ansible.builtin.dnf:
      name: tree  # package name
      state: present # to install any software
```

<p align="center">
  <img src="" width="500" alt="Initialize Repository Screenshot">
</p>

---

##  Example  6  - This playbook installs the Apache HTTPD server, starts and enables the service, and deploys a simple `index.html` webpage on the local machine.



```
---
- name: install ,start, enable httpd
  hosts: localhost
  become: yes # it assign sudo privileges
  tasks:
  # install httpd
  - name: install httpd
    ansible.builtin.dnf:
      name: httpd
      state: present
  # start and enabled httpd
  - name: start and enabled httpd
    ansible.builtin.systemd_service:
      name: httpd
      state: started
      enabled: true
  # deploy index.html
  - name: deploy index.html file
    ansible.builtin.copy:
     dest: /var/www/html/index.html
     content: |
      <h1>welcome to my httpd website</h1>
```

<p align="center">
  <img src="" width="500" alt="Initialize Repository Screenshot">
</p>


---

##  Example  7  - Here is the same previous example, but using NGINX instead of HTTPD

> If httpd (Apache) is already running, then we must stop it before starting nginx, because both use port 80.

```
---
- name: install ,start, enable httpd
  hosts: localhost
  become: yes # it assign sudo privileges
  tasks:
  # install httpd
  - name: install httpd
    ansible.builtin.dnf:
      name: httpd
      state: absent     # ------------------     -----------------> changes  not needed ..but you want delete the softewae so run this
  # start and enabled httpd
  - name: start and enabled httpd
    ansible.builtin.systemd_service:
      name: httpd
      state: stopped    #------------------     -----------------> changes
      enabled: false    # ------------------     -----------------> changes
  # deploy index.html
  - name: deploy index.html file
    ansible.builtin.copy:
     dest: /var/www/html/index.html
     content: |
      <h1>welcome to my httpd website</h1>
```
●  Run this file &
●  Check whether it has been uninstalled or not.

```
ansible-playbook httpd_install.yml --syntax-check
ansible-playbook httpd_install.yml
sudo systemctl httpd status
```

Now install NGINX.
```
---
- name: nginx install
  hosts: localhost
  tasks:
  - name: install nginx
    ansible.builtin.dnf:
      name: nginx
      state: present
  - name: start and enable nginx
    ansible.builtin.systemd_service:
      name: nginx
      state: started
      enabled: true
  - name : deploy index.html
    ansible.builtin.copy:
      dest: /usr/share/nginx/html/index.html
      content: |
        <h1> welcome to my nginx server</h1>
```


---

##  Example  8  - This Ansible playbook installs and configures a complete LAMP stack (Linux, Apache, MariaDB, PHP) on an Amazon Linux system and deploys a PHP test page.


```
#lamp -> amazon linux->
#httpd, mariadb105-server , mariadb, php, php-fpm
---
- name: install lamp in amazon linux
  hosts: localhost
  become: yes
  tasks:
  # install httpd
  - name: install httpd package
    ansible.builtin.dnf:
      name: httpd
      state: present
  # install mariadb
  - name: install mariadb package
    ansible.builtin.dnf:
      name: mariadb105-server
      state: present
  # install php
  - name: install php package
    ansible.builtin.dnf:
      name:
       - php
       - php-fpm
      state: present
  # start httpd
  - name: start and enable httpd
    ansible.builtin.systemd_service:
      name: httpd
      state: started
      enabled: true
  # start mariadb
  - name: start and enable mariadb
    ansible.builtin.systemd_service:
      name: mariadb
      state: started
      enabled: true
  # start php
  - name: start and enable php
    ansible.builtin.systemd_service:
      name: php-fpm
      state: started
      enabled: true
  # deploy php
  - name: deploy php
    ansible.builtin.copy:
     dest: /var/www/html/index.php
     content: |
      <?php
      phpinfo();
      ?>
```

After running this script, check in the browser by searching and see whether the output is displayed or not.

```
<public_ip>/index.php
```


---



























