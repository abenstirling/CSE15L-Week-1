# Week 1 Lab Report: Remote Access

---

## Student: *[Ben Stirling](https://github.com/abenstirling)*
## Professor: *[Joe Politz](https://github.com/jpolitz)*
## Date: ***9/29/22***

---

## Installing VSCode

---

An `IDE` (Integrated Development Environment) is extremely useful for developers because it allows them to edit code, navigate the terminal, execute code and debug. All in one place. 

You can download a standard IDE, Visual Studio Code, here: [https://code.visualstudio.com/Download](https://code.visualstudio.com/Download)

```coffeescript
💡 Make sure to download the appropriate version for your OS and computer 
```

After you launch the program for the first time, you should see a screen like the one below. 

![Untitled](Week%201%20Lab%20Report%20Remote%20Access%20ec72db670a664d90943bd082614b1550/Untitled.png)

## Remotely Connecting

---

Remotely connecting to another computer is a critical skill for developers. 

Imagine if you have a **`RPI`** (Raspberry Pi), a small computer, connected to your network. Since the **`RPI`** doesn’t have a monitor, keyboard or mouse, you will need a way to connect and control it. 

![Untitled](Week%201%20Lab%20Report%20Remote%20Access%20ec72db670a664d90943bd082614b1550/Untitled%201.png)

*Image Credit: [http://getdrawings.com/image/raspberry-pi-drawing-53.png](http://getdrawings.com/image/raspberry-pi-drawing-53.png)*

**`SSH`** (Secure Shell) uses a client-server technique for a computer to access another. Open the terminal in VSCode:

![Untitled](Week%201%20Lab%20Report%20Remote%20Access%20ec72db670a664d90943bd082614b1550/Untitled%202.png)

We will use the following command to initiate the connection of one computer to another:

```bash
ssh [ucsd_usr]@ieng6.ucsd.edu
psk = [yourUCSDPass]
```

Upon successful login, you will see this screen: 

![Untitled](Week%201%20Lab%20Report%20Remote%20Access%20ec72db670a664d90943bd082614b1550/Untitled%203.png)

Now we have successfully logged into our remote computer!

## Trying Some Commands

---

As you might imagine, we will need some commands to navigate and perform actions in the terminal. A few useful commands to test and see what they do are as follows: 

- `cd ~`
- `cd`
- `ls -lat`
- `ls -a`
- `ls /home/linux/ieng6/cs15lfa22/cs15lfa22abc`, where the `abc` is one of the other group members’ username
- `cp /home/linux/ieng6/cs15lfa22/public/hello.txt ~/`
- `cat /home/linux/ieng6/cs15lfa22/public/hello.txt`

Examples of results of running commands: 

![Untitled](Week%201%20Lab%20Report%20Remote%20Access%20ec72db670a664d90943bd082614b1550/Untitled%204.png)

![Untitled](Week%201%20Lab%20Report%20Remote%20Access%20ec72db670a664d90943bd082614b1550/Untitled%205.png)

![Untitled](Week%201%20Lab%20Report%20Remote%20Access%20ec72db670a664d90943bd082614b1550/Untitled%206.png)

## Moving Files with scp

---

Assuming the computer is truly remote, you might want to move files or project that you have on your main computer, similar to what you might do with a thumb-drive. 

With `WhereAmI.java`, a file on our main computer, where the contents are as follows: 

```java
class WhereAmI {
  public static void main(String[] args) {
    System.out.println(System.getProperty("os.name"));
    System.out.println(System.getProperty("user.name"));
    System.out.println(System.getProperty("user.home"));
    System.out.println(System.getProperty("user.dir"));
  }
}
```

We can compile and run the program from the terminal with the following commands: 

```bash
javac WhereAmI.java
java WhereAmI
```

Now let us move our java file with the terminal onto our remote computer with the following command: 

```bash
scp WhereAmI.java [ucsd_usr]@ieng6.ucsd.edu
```

After entering your password, you should see a **100%** in the response which means that all of the contents have moved successfully. 

![Untitled](Week%201%20Lab%20Report%20Remote%20Access%20ec72db670a664d90943bd082614b1550/Untitled%207.png)

```coffeescript
💡 Make sure to turn your VPN off (if you use a personal one) to ensure the scp command will work
```

## Setting an SSH Key

---

Optimizing a workflow is important for developers, in fact it might be a reason why you would consider yourself a developer. For example, you might spend hours creating a script that saves you a few seconds each time. You justify your time spent by saying something like “Time is time”. 

If we are signing into the same computer from the same computer, you would think there is a way for the computers to remember each other and just let you in when you initiate the log-in. 

`SSH` Keys are a way for us to do this exact thing. 

Running the command `ssh-keygen` from the terminal will start the process. 

![Untitled](Week%201%20Lab%20Report%20Remote%20Access%20ec72db670a664d90943bd082614b1550/Untitled%208.png)

Looks like our public and private keys are generated! Now we need to add a key onto our remote computer so it can match with our other key. We can do this with the following command: 

```bash
$ scp /Users/[usr]/.ssh/id_rsa.pub [ucsd_usr]@ieng6.ucsd.edu:~/.ssh/authorized_keys
```

![Untitled](Week%201%20Lab%20Report%20Remote%20Access%20ec72db670a664d90943bd082614b1550/Untitled%209.png)

Finally, let us try signing in via `SSH` and see if it recognizes our keys!

![Untitled](Week%201%20Lab%20Report%20Remote%20Access%20ec72db670a664d90943bd082614b1550/Untitled%2010.png)

## Optimizing Remote Running

---

Here are some more tips for navigating and running commands in the terminal: 

- Use semicolons to run multiple commands on the same line
    
    ```bash
    cp WhereAmI.java OtherMain.java; javac OtherMain.java; java WhereAmI
    ```
    
- Run a command without keeping you logged in
    
    ```bash
    ssh [ucsd_id]@ieng6.ucsd.edu "ls"
    ```
    
- `Up` and `Down` arrow keys to stroll through previous commands you entered

## Conclusion

---

In this lab, we conquered the following techniques: 

- Utilizing an `IDE`
- Learn and apply remote access with `SSH`
- Use terminal shortcuts and commands
- Transfer files with `SCP`
- Setup `SSH` keys for easy sign-in

```coffeescript
© 2022 Ben Stirling
```