# NPD
1. Introduction 
Securing computer networks is a critical requirement in the 
modern world. Firewalls are essential for protecting systems 
from unauthorized access but managing them through low
level command-line tools like iptables can be difficult for 
many administrators. 
The RapyDe Guard Firewall Management System was 
developed to solve this challenge by offering both: 
• A command-line interface (CLI) for experienced users 
and management users 
• A graphical web-based user interface (GUI) for easier 
access 
This project merges flexibility, security, and usability into a 
complete firewall management solution that can be deployed 
on Linux servers. 
2. Objectives 
The key goals of developing RapyDe Guard Firewall were: 
• Simplification: Make firewall management easier, even 
for administrators who are not deeply familiar with 
iptables. 
• Accessibility: Provide a secure, easy-to-navigate web 
interface along with the traditional CLI. 
• Security: Ensure strong authentication, encrypted 
password handling, and secure log management. 
• Real-Time Monitoring: Allow administrators to 
monitor system logs live, detecting suspicious activity 
quickly. 
• Dual Control Modes: Ensure that both CLI and GUI 
operations synchronize with the firewall, offering 
flexibility to administrators depending on their preferred 
working style. 
  
3. System Overview 
The RapyDe Guard Firewall system integrates several 
important modules: 
• Firewall Rule Management: 
Administrators can add, edit, view, move, and delete 
firewall rules. These rules are applied directly to the 
server using iptables. Changes are persistent and can be 
re-applied after the system restarts. 
• User Authentication and Management: 
Access to the system is restricted through a username
password login system. Passwords are securely hashed 
using SHA-256 to prevent password theft. The system 
supports adding, changing, and deleting users (admin
only). 
• Network Adapter Management: 
Administrators can choose which network interfaces 
(adapters) are involved in firewall filtering. Interfaces 
can be added or removed dynamically. 
• Real-Time Log Monitoring: 
The system captures operational logs like login attempts, 
firewall actions, and error reports. These logs are 
displayed live inside the GUI using WebSocket 
technology (Flask-SocketIO). 
4  
• Firewall Operations: 
Administrators can easily start, stop, or restart the 
firewall from both the CLI and the web interface. 
5  
4. Implementation Details 
4.1 Technologies Used 
• Python 3 is the main programming language for 
scripting, process control, and server handling. 
• Flask as the web server framework to serve the GUI and 
APIs. 
• Flask-SocketIO to push live updates (logs) to the web 
GUI in real time. 
• psutil to interact with system network adapters. 
• subprocess module to execute and manage iptables 
commands on the system. 
• hashlib to secure passwords via SHA-256 hashing. 
• JSON format to store and retrieve users, rules, and 
adapter configurations in lightweight and human
readable files. 
6  
4.2 Key Components 
• Command-Line Interface (CLI): 
A text-based menu system is available for administrators 
who prefer direct server access. 
• Graphical User Interface (GUI): 
A beautiful web application (HTML/CSS/JS) designed 
to simplify firewall operations, with all functions 
accessible by just a few clicks. 
• Authentication System: 
All users must log in, and only authorized users can 
make changes. The "admin" user has additional 
privileges. 
• Logging: 
Every major action (e.g., rule addition, login attempt, 
firewall status change) is recorded with timestamps, 
making tracking easy. 
• Firewall Engine: 
Uses the Linux iptables utility underneath to enforce 
firewall rules dynamically, with the ability to reapply 
them automatically if the firewall is restarted. 
7  
5. Testing and Validation 
5.1 Unit Testing 
Each function was tested individually: 
• Password hashing function was tested against known 
hashes. 
• JSON file handlers were tested for data saving and 
loading without data loss. 
• Authentication tests ensured wrong credentials were 
correctly rejected. 
5.2 Integration Testing 
The complete system was tested in real-world conditions: 
• Users logged in through CLI and GUI simultaneously. 
• Rules were added through the GUI, and their effect was 
verified through CLI. 
• Firewall start/stop/restart actions were validated from 
both CLI and GUI. 
8  
5.3 Manual Testing 
• The system was deployed on Ubuntu 20.04 and CentOS 
8 servers. 
• Browser compatibility was tested (Google Chrome, 
Mozilla Firefox). 
• Stress tests with multiple users operating simultaneously 
were conducted to check consistency. 
9  
6. Limitations 
Despite the system's success, there are limitations to be aware 
of: 
• Root Privilege Dependency: 
RapyDe Guard must be run as a root user because 
iptables requires administrative access. This limits where 
it can be installed. 
• Linux-Only Support: 
The solution is heavily tied to iptables, a Linux-specific 
tool. It cannot be used natively on Windows or macOS 
without major changes. 
• No Secure Web Traffic: 
By default, the web server uses plain HTTP instead of 
HTTPS. An SSL/TLS certificate needs to be added 
manually for production use. 
• No Multi-Role User System: 
All users have near-identical capabilities. There is no 
difference between "viewer" users and "editor" users. 
• No Real IDS/IPS: 
The system mentions "IDS/IPS" management but only 
offers a placeholder. Full intrusion detection systems are 
not yet integrated. 
10  
7. Future Enhancements 
In upcoming versions, the following improvements are 
suggested: 
• Implement HTTPS: 
Add SSL/TLS certificates for encrypted communication 
on the web interface. 
• Introduce Role-Based Access Control (RBAC): 
Allow for different types of users — for example, 
viewers who can only monitor logs, and admins who can 
modify rules. 
• Dockerization: 
Build a Docker image for the firewall system to ease 
installation, updates, and portability. 
• IPv6 Support: 
Expand firewall management to include both IPv4 and 
IPv6 networks, making it future proof. 
11  
8. Conclusion 
The RapyDe Guard Firewall Management System provides a 
strong foundation for modern, simplified network security. It 
successfully bridges the gap between complex command-line 
operations and an easy-to-use web-based environment. 
While it currently focuses on core firewall rule management, 
with minor enhancements, RapyDe Guard can evolve into a 
full network security management platform suitable for small 
businesses, educational institutions, and even larger 
organizations seeking simplified firewall control. 
