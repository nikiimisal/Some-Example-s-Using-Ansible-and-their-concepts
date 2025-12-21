<h3>🚀 Quick Navigation</h3>


  
- [Create Shortcut's](#example-0)

<table>
  <thead>
    <tr>
      <th>Example's </th>
      <th>.</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <a href="#example-1">Example 1 – Ping Playbook (Easy & Beginner Friendly)</a><br>
        <a href="#example-2">Example 2 – Create a folder using Ansible</a><br>
        <a href="#example-3">Example 3 – Create Directory</a><br>
        <a href="#example-4">Example 4 – Copy File</a><br>
        <a href="#example-5">Example 5 – Install Tree</a>
      </td>
      <td>
        <a href="#example-6">Example 6 – Install and Run Apache HTTPD with Sample Web Page</a><br>
        <a href="#example-7">Example 7 – NGINX Instead of HTTPD</a><br>
        <a href="#example-8">Example 8 – Install LAMP Stack & Deploy Php-test page</a><br>
        <a href="#example-9">Example 9 – Dynamic LEMP Stack Setup with Ansible (Using Variables)</a><br>
        <a href="#example-10">Example 10 – Switch from LEMP to LAMP with php</a>
      </td>
    </tr>
  </tbody>
</table>

- [Inventroy](#example-11)

<table>
  <thead>
    <tr>
      <th>Example </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <a href="#example-12">Example 1 –Optimized Ansible Playbook to Install LEMP Stack on Target Servers</a><br>
      </td>
    </tr>
  </tbody>
</table>

- [Handlers](#example-13)

<table>
  <thead>
    <tr>
      <th>Example </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <a href="#example-14">Example 1 – Without handlers</a><br>
        <a href="#example-15">Example 2 – With handlers</a><br>
      </td>
    </tr>
  </tbody>
</table>

---
---
---

<a id="example-0"></a>

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

<a id="example-1"></a>

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

<a id="example-2"></a>

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

<a id="example-3"></a>

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
  <img src="https://github.com/nikiimisal/Some-Example-s-Using-Ansible/blob/main/img/l/Screenshot%202025-12-17%20222602.png?raw=true" width="500" alt="Initialize Repository Screenshot">
</p>

---

<a id="example-4"></a>

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
  <img src="https://github.com/nikiimisal/Some-Example-s-Using-Ansible/blob/main/img/l/Screenshot%202025-12-17%20224622.png?raw=true" width="500" alt="Initialize Repository Screenshot">
</p>


---

<a id="example-5"></a>

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
  <img src="https://github.com/nikiimisal/Some-Example-s-Using-Ansible/blob/main/img/l/Screenshot%202025-12-17%20225212.png?raw=true" width="500" alt="Initialize Repository Screenshot">
</p>

---

<a id="example-6"></a>

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
  <img src="https://github.com/nikiimisal/Some-Example-s-Using-Ansible/blob/main/img/l/Screenshot%202025-12-17%20230540.png?raw=true" width="500" alt="Initialize Repository Screenshot">
</p>


---

<a id="example-7"></a>

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

<a id="example-8"></a>

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

<a id="example-9"></a>

##  Example  9  - Dynamic LEMP Stack Setup with Ansible (Using Variables)


```
# variable -> dynamic value assignment
---
- name: install LEMP stack using variable
  hosts: localhost
  become: yes
  # define variable and assign values
  vars:
    web_pkg: nginx # hard codeing
    db_pkg: mariadb105-server
    php_pkg:
     - php
     - php-fpm
    web_service: nginx
    db_service: mariadb
    php_service: php-fpm
    web_file_path: /usr/share/nginx/html/index.php
  tasks:
  - name: install nginx
    ansible.builtin.dnf:
      name: "{{web_pkg}}" # varaible call
      state: present
  - name: install mariadb
    ansible.builtin.dnf:
      name: "{{db_pkg}}"
      state: present
  - name: install php-fpm
    ansible.builtin.dnf:
      name: "{{php_pkg}}"
      state: present
  - name: start and enable nginx
    ansible.builtin.systemd_service:
      name: "{{web_service}}"
      state: started
      enabled: true
  - name: start and enable mariadb
    ansible.builtin.systemd_service:
      name: "{{db_service}}"
      state: started
      enabled: true
  - name: start and enable php-fpm
    ansible.builtin.systemd_service:
      name: "{{php_service}}"
      state: started
      enabled: true
  - name : deploy php page
    ansible.builtin.copy:
      dest: "{{web_file_path}}"
      content: |
        <?php
        phpinfo();
        ?>
```

Verify if the code has executed successfully by opening the IP address in a browser and confirming the output.

```
<public-ip>/index.php
```

---

<a id="example-10"></a>

##  Example  10  - Switch from lemp to lamp with php

```
---
- name: Switch from lemp to lamp with php
  hosts: localhost
  become: yes

  vars:
    old_web_service: nginx
    new_web_pkg: httpd
    new_web_service: httpd
    db_pkg: mariadb105-server
    php_pkgs: 
      - php
      - php-fpm
    php_index_file: /var/www/html/index.php   # apache default docroot

  tasks:
    # Stop and disable nginx
    - name: stop and disable nginx
      ansible.builtin.service:
        name: "{{ old_web_service }}"
        state: stopped
        enabled: false

    # Install httpd
    - name: install httpd
      ansible.builtin.dnf:
        name: "{{ new_web_pkg }}"
        state: present

    # Start and enable httpd
    - name: start httpd
      ansible.builtin.service:
        name: "{{ new_web_service }}"
        state: started
        enabled: true

    # Install php (already installed but kept for idempotency)
    - name: install php and php-fpm
      ansible.builtin.dnf:
        name: "{{ php_pkgs }}"
        state: present

    # Deploy php page for apache
    - name: deploy php application on apache
      ansible.builtin.copy:
        dest: "{{ php_index_file }}"
        content: |
          <?php
          phpinfo();
          ?>
```




---

<a id="example-11"></a>

# Inventory.

Till now, we were running Ansible playbooks on `localhost`.<br>
That means the code was created and executed on the same machine.
<br>
<br>

Now, moving forward, we will write targeted playbooks, where Ansible will run tasks on remote servers instead of localhost.
<br>

For this, we need to define an `inventory`.

---

<h3>What is an Inventory in Ansible?</h3>

An inventory is a file that contains a complete collection of target servers on which Ansible will execute playbooks.

👉 Inventory tells Ansible:

- Which servers to manage
- How to connect to them


The commonly used inventory file is:
  
  ```
inventory.ini
  ```

---

<h4>Important Things Required in Inventory</h4>

To connect to a target server, three things are very important:
<br>

1️⃣ IP Address (Private IP – Recommended)

- Private IP is preferred when servers are in the same network (VPC).
- Public IP can also be used, but it is less secure and depends on internet access.

```
192.168.1.10
```


2️⃣ Username

- This is the remote server user Ansible will log in as.
- Example:
   - `ec2-user` (Amazon Linux)
   - `ubuntu` (Ubuntu)


3️⃣ Private Key

- Used for SSH authentication.
- This is the `.pem` key that allows Ansible to access the target server without a password.


```
ansible_ssh_private_key_file=/home/ec2-user/key.pem
```

Sample `inventory.ini` File

```
[webservers]
192.168.1.10 ansible_user=ec2-user ansible_ssh_private_key_file=/home/ec2-user/key.pem
```

Why Inventory is Important?

- Allows automation on multiple servers
- Makes playbooks reusable
- Supports grouping of servers (web, db, app, etc.)
- Enables centralized management


---

<h4>Group's Concept</h4>

When you write an inventory.ini file, you can create groups inside it.<br>
Because of this, while running a playbook, you can target and run the playbook for a specific group only.<br>
<br>
This gives you more control and flexibility.
<br>

Example: Inventory with Groups

```
[webserver]
192.168.1.10 ansible_user=ec2-user ansible_ssh_private_key_file=/home/ec2-user/key.pem

192.168.1.10 ansible_user=ec2-user ansible_ssh_private_key_file=/home/ec2-user/key.pem

[appserver]
192.168.1.20 ansible_user=ec2-user ansible_ssh_private_key_file=/home/ec2-user/key.pem

192.168.1.10 ansible_user=ec2-user ansible_ssh_private_key_file=/home/ec2-user/key.pem

```

Running Playbook for a Specific Group

If you want to run the playbook only on the `appserver` group, use the `--limit` option.

Correct Command:

```
ansible-playbook lamp-install.yml -i inventory.ini --limit appserver
```

Why Use `--limit`

- Run playbook on only selected servers
- Avoid affecting other environments
- Useful for testing, partial deployments, and production safety?


---

Now we will not hard-code IP addresses inside the `.yml` playbook.<br>
Instead, we will use group names.<br>
This is important because one target is rarely a single server — usually it is a group of servers.<br>
<br>

Below is a clear explanation of the Group concept, covering both `.yml` (playbook) and `.ini` (inventory) files.<br>

---

Why We Use Groups Instead of IPs

- In real projects, multiple servers perform the same role
- IPs can change, but group names stay constant
- Playbooks become clean, reusable, and scalable
- One playbook → many servers

So instead of:

```
0.0.0.0/1   ❌
```

We use:

```
webserver
appserver
dbserver
```

<h4>Inventory File (inventory.ini) – Group Definition</h4>

This is where actual IPs and connection details live.

```
[webserver]
192.168.1.10
192.168.1.11

[appserver]
192.168.1.20
192.168.1.21

[dbserver]
192.168.1.30
```

You can also add user and key once using group variables:

```
[appserver:vars]
ansible_user=ec2-user
ansible_ssh_private_key_file=/home/ec2-user/key.pem
```

👉 Inventory answers:<br>
WHO are the target servers and HOW to connect to them.


---

<h4>Playbook File (.yml) – Using Group Names</h4>
Here we never mention IPs.


```
- name: Install LAMP stack
  hosts: appserver
  become: yes
  tasks:
    - name: Install Apache
      dnf:
        name: httpd
        state: present
```
👉 `hosts: appserver` means:

>Run this playbook on all servers inside the appserver group

---

<h3>How Ansible Works Internally</h3>

1.  Playbook reads:

```
hosts: appserver
```

2.  Ansible looks into `inventory.ini`
3.  Finds all IPs under `[appserver]`
4.  Connects to each server using SSH
5.  Executes tasks one by one

---


Running for Specific Groups

```
ansible-playbook lamp-install.yml -i inventory.ini
```

Only `appserver` runs because playbook says:

```
hosts: appserver
```
Or override at runtime:
```
ansible-playbook lamp-install.yml -i inventory.ini --limit webserver
```

Real-World Example (Best Practice)
<br>
<br>
Inventory
```
[prod_app]
10.0.1.10
10.0.1.11

[dev_app]
10.0.2.10
```
Playbook

```
hosts: prod_app
```

Same playbook → different environments 🔥


---

---

#  Example's

<a id="example-12"></a>

##  Example  1 - Optimized Ansible Playbook to Install LEMP Stack on Target Servers


inventry.ini
```
# this s the file where you can mention all the ip of target server

[server]
51.21.246.156 ansible_user=ec2-user ansible_ssh_private_key_file=/home/ec2-user/server1.pem

```

lemp_on_target.yml

```
# install lemp on target server in optimize format

---

- name: install lemp on target server
  hosts: server
  become: yes
  tasks:
  - name: install nginx, mariadb, php
    ansible.builtin.dnf:
      name:
       - nginx
       - mariadb105-server
       - php
       - php-fpm
      state: present
  - name: start and enable nginx, mariadb, php
    ansible.builtin.systemd_service:
      name: "{{item}}"
      state: started
      enabled: true
    loop:
     - nginx
     - mariadb
     - php-fpm
  - name: deploy php page
    ansible.builtin.copy:
      dest: /usr/share/nginx/html/index.php
      content: |
       <?php
       phpinfo();
       ?>

```

Run this script

```

ansible-playbook nginx.yml -i inventory.ini --syntax-check
```

```
ansible-playbook nginx.yml -i inventory.ini

```



 To view the output of this example, copy the target server’s public IP address and paste it into the browser’s search bar.

| **AWS-Console**    | **.ini file**          | **.yml file**          |
|--------------------------------|------------------------------------|------------------------------------|
| ![VS](https://github.com/nikiimisal/Some-Example-s-Using-Ansible/blob/main/img/l/Screenshot%202025-12-18%20205230.png?raw=true) | ![AWS](https://github.com/nikiimisal/Some-Example-s-Using-Ansible/blob/main/img/l/Screenshot%202025-12-18%20201654.png?raw=true) | ![AWS](https://github.com/nikiimisal/Some-Example-s-Using-Ansible/blob/main/img/l/Screenshot%202025-12-18%20230311.png?raw=true) |

| **private-key upload on Ansible server **    | **Run .ini and .yml file's**          | **output**          |
|--------------------------------|------------------------------------|------------------------------------|
| ![VS](https://github.com/nikiimisal/Some-Example-s-Using-Ansible/blob/main/img/l/Screenshot%202025-12-18%20203421.png?raw=true) | ![AWS](https://github.com/nikiimisal/Some-Example-s-Using-Ansible/blob/main/img/l/Screenshot%202025-12-18%20214548.png?raw=true) | ![AWS](https://github.com/nikiimisal/Some-Example-s-Using-Ansible/blob/main/img/l/Screenshot%202025-12-18%20230245.png?raw=true) |

---



<a id="example-13"></a>

<h1> Handlers </h1>

🔔 Ansible Handlers & Notify 

🔹 What is a Handler?

A handler is a special task in Ansible that runs only when it is triggered by a `notify` directive from another task.<br>
Handlers execute after all tasks are completed, at the end of the playbook.

They are mainly used for actions that should run only when a change occurs, such as restarting or reloading services.

---

🔹 Why Use Handlers?

Handlers help to:

- 🔄 Avoid unnecessary service restarts  
- ⚡ Improve playbook efficiency  
- ✅ Follow best practices by running actions only when needed  

---

🔹 How Handler & Notify Work

1. A normal task runs  
2. If the task makes a change, it triggers `notify`
3. The handler is queued for execution  
4. All queued handlers run once, at the end of the play  

---

🔹 How `notify` Works

- `notify` is written inside a task  
- It is triggered only when the task results in a change  
- If no change occurs, the handler does not run

  >Notify always appears at the end of the script`tasks`

```
- name: copy config file
  copy:
    src: app.conf
    dest: /etc/app.conf
  notify: restart app
```

👉 File changed → handler is notified  
👉 File unchanged → handler is not triggered 

---

🔹 Why Handlers Don’t Run Immediately

Handlers are delayed because:

- Ansible executes multiple tasks in a play  
- The same handler can be notified by multiple tasks  
- Ansible avoids duplicate or repeated restarts  

💡 As a result:

- The handler is stored in a queue  
- It runs only once, after all tasks finish

  ---

🔹 Why Are Handlers Written at the End?

Technical Reason <br> 
- Handlers are event-driven, not part of the normal task flow  
- They depend on `notify` events  

Best Practice  

- 📘 Keeps the playbook clean and readable  
- 🚫 Prevents services from restarting during every task  
- 📍 All handlers are defined in one dedicated section  

```
tasks:
  - task1
  - task2
  - task3

handlers:
  - restart service

```
---

🔹 We Can Multiple Tasks Notify the Same Handler

```

- name: copy config1
  copy:
    src: a.conf
    dest: /etc/a.conf
  notify: restart nginx

- name: copy config2
  copy:
    src: b.conf
    dest: /etc/b.conf
  notify: restart nginx
```

➡️ Even if both tasks change  
➡️ `restart nginx` runs only once  

---

🔹 When Does a Handler NOT Run?

A handler will not run if:

- ❌ The task makes no change  
- ❌ notify is not defined  
- ❌ The playbook fails before completion

  ---

🔹 Running Handlers Immediately (Optional)

By default, handlers run at the end of the playbook.

To force immediate execution:
```
- meta: flush_handlers
```
👉 This runs all notified handlers at that point.

---

🔹 Real-Life Example

Imagine you update multiple configuration files:

- Restarting the service after each change is inefficient ❌  
- Applying all changes first and restarting once is optimal ✅  

👉 Handlers are designed to solve exactly this problem.


---
---


#  Example's

<a id="example-14"></a>


## Example 1 : install nginx without handler block


without_handeler.yml
```
# install nginx without handler block
---

- name: deployment of nginx without handler
  hosts: targetserver
  become: yes

  vars:
    pkg: nginx
    svc: nginx
    file_path: /usr/share/nginx/html/index.html
    conf_file: /etc/nginx/conf.d/custom.conf

  tasks:

  # install nginx
  - name: install nginx
    ansible.builtin.dnf:
      name: "{{ pkg }}"
      state: present

  # start and enable nginx
  - name: start and enable nginx
    ansible.builtin.systemd:
      name: "{{ svc }}"
      state: started
      enabled: true

  # add configuration block
  - name: add configuration block
    ansible.builtin.blockinfile:
      path: "{{ conf_file }}"
      create: yes
      block: |
        server {
            listen 80;

            location / {
                root /usr/share/nginx/html;
                index index.html index.htm;
            }
        }

  # deploy index.html
  - name: deployment of index page
    ansible.builtin.copy:
      dest: "{{ file_path }}"
      content: "<h1>This app is without handlers</h1>"

```

inventry.ini
```
# this s the file where you can mention all the ip of target server

[server]
51.21.246.156 ansible_user=ec2-user ansible_ssh_private_key_file=/home/ec2-user/server1.pem
```

Run this script

```
ansible-playbook nginx.yml -i inventory.ini --syntax-check
```

```
ansible-playbook nginx.yml -i inventory.ini
```

After running this, check the output.

<p align="center">
  <img src="" width="500" alt="Initialize Repository Screenshot">
</p>

---

After confirming the output, change the port number from `80` to `81`. This will cause the application to fail and return an error.

<p align="center">
  <img src="" width="500" alt="Initialize Repository Screenshot">
</p>

<br>

This is where the use of handlers comes in. It is a concept used to manage such changes.<br>
So next example be using handler's


---

<a id="example-15"></a>


## Example 2 : Deploy nginx with handler block


with_handler.yml

```
# install nginx with handler block
---
- name: deployment of nginx with handler
  hosts: targetserver
  become: yes

  vars:
    pkg: nginx
    svc: nginx
    file_path: /usr/share/nginx/html/index.html
    conf_file: /etc/nginx/conf.d/custom.conf

  tasks:

  # install nginx
  - name: install nginx
    ansible.builtin.dnf:
      name: "{{ pkg }}"
      state: present

  # start and enable nginx
  - name: start and enable nginx
    ansible.builtin.systemd:
      name: "{{ svc }}"
      state: started
      enabled: true

  # add configuration block
  - name: add configuration block
    ansible.builtin.blockinfile:
      path: "{{ conf_file }}"
      create: yes
      block: |
        server {
            listen 80;

            location / {
                root /usr/share/nginx/html;
                index index.html index.htm;
            }
        }

# notify block here

    notify: restart nginx

  # deploy index.html
  - name: deployment of index page
    ansible.builtin.copy:
      dest: "{{ file_path }}"
      content: "<h1>This app is with handlers</h1>"
    notify: restart nginx

  handlers:
  - name: restart nginx
    ansible.builtin.systemd:
      name: "{{ svc }}"
      state: restarted

```

inventry.ini

```
# this s the file where you can mention all the ip of target server

[server]
51.21.246.156 ansible_user=ec2-user ansible_ssh_private_key_file=/home/ec2-user/server1.pem
```

First, run this file once. After it runs successfully, change the port from `80` to `81` and run it again to verify whether the handler is working properly.

---
---
