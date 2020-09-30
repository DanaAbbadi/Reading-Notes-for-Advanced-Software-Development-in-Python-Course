# Secure Shell (SSH)

![img](https://miro.medium.com/max/875/1*ZItMQX9ycwTOsqNZ9yvSog.jpeg)

SSH, also known as Secure Shell or Secure Socket Shell, is a network protocol that gives users, particularly system administrators, a secure way to access a computer over an unsecured network. In addition to providing secure network services, SSH refers to the suite of utilities that implement the SSH protocol. Secure Shell provides strong password authentication and public key authentication, as well as encrypted data communications between two computers connecting over an open network, such as the internet. In addition to providing strong encryption, SSH is widely used by network administrators for managing systems and applications remotely, enabling them to log in to another computer over a network, execute commands and move files from one computer to another.

SSH refers both to the cryptographic network protocol and to the suite of utilities that implement that protocol. SSH uses the client-server model, connecting a Secure Shell client application, which is the end where the session is displayed, with an SSH server, which is the end where the session runs. SSH implementations often include support for application protocols used for terminal emulation or file transfers. SSH can also be used to create secure tunnels for other application protocols, for example, to securely run X Window System graphical sessions remotely. An SSH server, by default, listens on the standard Transmission Control Protocol (TCP) port 22.

## SSH Structure

Secure Shell was created to replace insecure terminal emulation or login programs, such as Telnet, rlogin (remote login) and rsh (remote shell); SSH enables the same functions (logging in to and running terminal sessions on remote systems). SSH also replaces file transfer programs, such as File Transfer Protocol (FTP) and rcp (remote copy).

The most basic use of SSH is for connecting to a remote host for a terminal session. The form of that command is the following:

    ssh UserName@SSHserver.example.com

This command will cause the client to attempt to connect to the server named server.example.com, using the user ID UserName. If this is the first time negotiating a connection between the local host and the server, the user will be prompted with the remote host's public key fingerprint and prompted to connect, despite there having been no prior connection:

    The authenticity of host 'sample.ssh.com' cannot be established.
    DSA key fingerprint is 01:23:45:67:89:ab:cd:ef:ff:fe:dc:ba:98:76:54:32:10.
    Are you sure you want to continue connecting (yes/no)?


Answering yes to the prompt will cause the session to continue, and the host key is stored in the local system's known_hosts file. This is a hidden file, stored by default in a hidden directory, called /.ssh/known_hosts, in the user's home directory. Once the host key has been stored in the known_hosts file, the client system can connect directly to that server again without need for any approvals; the host key authenticates the connection.

## HOW SSH WORKS?

SSH protocol uses symmetric encryption, asymmetric encryption and hashing in order to secure transmission of information. The SSH connection between the client and the server happens in three stages:



1. **VERIFICATION OF SERVER**

   The client initiates a SSH connection with the    server. Server listens to default port 22(this port    can be changed) for SSH connections. At this point,    the server identity is verified. There are two    cases:
   1. If the client is accessing the server for first    time, client is asked to authenticate server    manually by verifying public key of server. Public    key of server can be found using ssh-keyscan    command or can be found at different places(WHERE?   GOOGLE!).Once the key is verified, the server is    added in known_hosts file in ~/.ssh directory on    client machine. The known_hosts file contains the    information about all the verified servers by the    client.
   
   2. If the client is not accessing the server for    the first time, the server’s identity is matched    with previously recorded information in known_hosts    file for verification.

2. **GENERATION OF SESSION KEY**
After the server is verified, both the parties negotiate a session key using a version of something called the Diffie-Hellman algorithm. This algorithm is designed in such a way that both the parties contribute equally in generation of session key. The generated session key is shared symmetric key i.e. the same key is used for encryption and decryption.

3. **AUTHENTICATION OF THE CLIENT**
The final stage involves authentication of the client. Authentication is done using SSH key pair. As the name suggests, SSH key pair is nothing but a pair of two key to serve two different purposes. One is public key that is used to encrypt data and can be freely shared. The other one is private key that is used to decrypt data and is never shared with anyone.

### Uses

Present in all data centers, SSH ships by default with every Unix, Linux and Mac server. SSH connections have been used to secure many different types of communications between a local machine and a remote host, including secure remote access to resources, remote execution of commands, delivery of software patches, and updates and other administrative or management tasks. In addition to creating a secure channel between local and remote computers, SSH is used for managing routers, server hardware, virtualization platforms, operating systems (OSes), and inside systems management and file transfer applications.

Secure Shell is used to connect to servers, make changes, perform uploads and exit, either using tools or directly through the terminal. SSH keys can be employed to automate access to servers and often are used in scripts, backup systems and configuration management tools. Designed to be convenient and work across organizational boundaries, SSH keys provide single sign-on (SSO) so that users can move between their accounts without typing a password each time.


________________________________

# Managing Django Settings: Issues

**Different environments**. Usually, you have several environments: local, dev, ci, qa, staging, production, etc. Each environment can have its own specific settings (for example: DEBUG = True, more verbose logging, additional apps, some mocked data, etc). You need an approach that allows you to keep all these Django setting configurations.

**Sensitive data**. You have SECRET_KEY in each Django project. On top of this there can be DB passwords and tokens for third-party APIs like Amazon or Twitter. This data cannot be stored in VCS.

**Sharing settings between team members**. You need a general approach to eliminate human error when working with the settings. For example, a developer may add a third-party app or some API integration and fail to add specific settings. On large (or even mid-size) projects, this can cause real issues.

**Django settings are a Python code**. This is a curse and a blessing at the same time. It gives you a lot of flexibility, but can also be a problem – instead of key-value pairs, settings.py can have a very tricky logic.
