# Managing SSH Keys

This course demonstrates how to use a Puppet Module to manage SSH client and server keys in your environemnt.  

At the end of this course you will be able to:

* Install the saz-ssh module from the Puppet Forge.
* Add the ssh classes to nodes in your infrastructure.
* Edit ssh class parameters. 

## Slide Content

### slide 1
This course is a quick look at how to use Puppet Enterprise to manage SSH key authentication. 


### slide 2
We'll look at how to install an SSH module from the Puppet Forge, add the ssh classes to a node group, and set ssh class parameters.  
### slide 3
First -  a quick review of SSH. Secure Shell (SSH) is a protocol that enables encrypted connections between nodes on a network for secure data communication, remote command-line login, remote command execution, and other secure network services. Perhaps the most common application of the protocol is for access to shell accounts on Unix-like operating systems, but it can also be used in a similar fashion for accounts on Windows.    

### slide 4SSH uses public-key cryptography to authenticate clients and servers.  During authentication, the client and server prove their identities to each other by using private and public key pairs that work in concert. Information encrypted with the private key can be decrypted with the public key, and vice versa. On a Linux system, the authorized keys file lists the public keys that are permitted to log in.  When the user logs in, the ssh client uses the private half of its key pair to complete a computation and create a secret message, which it sends to the server for authentication. The server validates that secret message by performing the same computation in reverse, using the public key stored in the authorized keys file. Key-based authentication is the most secure of several modes of authentication, including passwords because in order to gain access to your system an attacker must have a copy of your private key that corresponds to the public key stored on the server. 
 

### slide 5
Typically, the first time you attempt to SSH into a host you’ve never connected to before, you receive a message similar to this one. If you select yes, the public key for that host is added to your SSH known_hosts file, and you won’t have to authenticate it again unless that host’s key changes.

### slide 6
You can use Puppet Enterprise to automate management of SSH authentication for the nodes in your environment.  

### slide 7
The saz-ssh module, available on the Puppet Forge, is one of many modules written by members of our user community and available for download. You can use the this module to automate management of your ssh keys. To install the module, from the Puppet Master, run the command puppet module install saz-ssh.  As simple as that, you have installed the saz-ssh module. All of the classes included in the module are available for you to assign to agent nodes.

### slide 8
A Puppet class is a collection of resources that are managed together as a single unit. You can think of them as blocks of Puppet code. The saz-ssh module includes classes for managing the client and server ssh authentication keys.  The main class, ssh, is the class that you declare in order to configure the behavior of the module. The main ssh class includes  additional classes:  The ssh client and server classes manage installation and configuration of the ssh clients and servers. Other classes manage hostkeys and knownhosts.

### slide 9
Now that the ssh module is installed, you can use the Puppet Enterprise Console first to add the ssh class to your environment and then to apply the ssh class to  a group of nodes in your infrastructure.   

### slide 10
Although you have added the ssh classes to your node group, you need to initiate a Puppet run in order to share the SSH keys between nodes. On the Live Management page, select the Control Puppet tab. Then select the runonce action.  During the initial run, the first server that runs shares its key but it not able to collect keys from the other agents. Select the runonce option again so that all keys can be collected and shared.  

### slide 11
After you install the ssh module and run Puppet, Puppet Enterprise can collect the public keys for the agent nodes and distribute the public keys to the known_hosts files of the other agent nodes in the group. Then in the future, users will not be asked to authenticate when they use SSH. The process is automated.

### slide 12
With Puppet Enterprise you can edit or add class parameters from the PE console which means you don't have to edit the module code directly. For example, the saz-ssh module, by default, allows root login over SSH. But you may want to limit root access. To easily change this parameter, from the console, select the node group that you want to change, and then select the class that you want to edit. Edit. For our ssh class example, on the parameters dialog box, in the server_options parameter field, enter the value: {"PermitRootLogin"=>"no"}. Then launch a Puppet run so that Puppet Enterprise can apply the new configuration. 

### slide 13
You can find more information about the saz ssh module and other Puppet modules on the puppet forge.  

### slide 14
In this brief course, we looked at how to install an ssh Puppet module from the Puppet Forge, how to add classes from the module to node groups, and how to edit class parameters.  

### slide 15
To check your knowledge, click the link on the bottom of this course's page and complete the short quiz. There is also a link to additional learning resources.

### slide 16
Thank you for completing this Puppet Labs Workshop course.





## Quiz
1. True or False. 
2. Which ?  
	a. .
	b. **xxx**
	c. .
	d. .
3. Which ?  
	a. .
	b. **xxx**
	c. .
	d. .
4. Which ?  
	a. .
	b. **xxx**
	c. .
	d. .
5. True or False. 
	**True**

## References
* [Vim Documentation](http://www.vim.org/docs)
* [Vim Blog](http://puppetlabs.com/blog/vim-tool-for-learning-puppet)
