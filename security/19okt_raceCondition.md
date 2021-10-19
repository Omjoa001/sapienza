# Race Conditions
<sub>19.okt</sub>

Race condition occurs when two concurrent execution threads both execute on shared state and this is not done atomically. As an example you can take advantage of `mkdir` on Unix by creating symbolic links between the non-atomic directory creation actions to become the owner of files one should not have access to.

![Race condition example](./img/race_cond.png)

Another example is the `1pr` command which prints utility and has the option to remove the file after printing. An attacker could try to go in between the print and remove actions and change the file that is being worked on to as the following remove command targets it. This is how race conditions can also be a security vulnerability.

Due to the rise of multithreaded-CPUs the future of programming is in writing concurrent programs, which gives rise to issues involving data races in code.

["The free lunch is over: a fundamental turn towards concurrency in software", by Herb Sutter](http://www.gotw.ca/publications/concurrency-ddj.htm)


> Semaphores and locks are mechanisms that prevent concurrent access to, or modification of, an object by different processes.

The java synchronized method ensures a lock so one can be safe that variables inside of the method will not change while in use.

- Scann tmp/junk for new creation and use `nice` command to make it run slowly in the backgorund while the scanner runs in the foreground
- When scanner spots new directory:
    - Remove the original /tmp/junk
    - Create a link from the secret file you want

A issue found in SSL approximates to the following, where step 2 and 3 occasionally get swapped:
1. Load buffer with plaintext
2. Encrypt buffer
3. Send buffer contents to recipient


## Security principles
- Secure the weakest link
  - This requires good risk analysis
- Practice defence in depth
  - Avoid SPOF, and beware of typical violations where for instance if you have a firewall, and only a firewall, than so-called enviromental creep, aka a user bringing their own laptop to circumvent the firewall, may still do damage.
  -  Use access control, encrypt files
    - On UNIX systems, the password file /etc/passwd, containing hashed passwords, was world readable (not good).
    - [Read on the Sun tarball problem (1993)](http://etutorials.org/Programming/secure+coding/Chapter+1.+No+Straight+Thing/1.3+Why+Good+People+Write+Bad+Code/)
- Least privilige
  - Device drivers running in kernel mode (bad).
  - In java:
    - ```grant codeBase```
    - Avoid public when you can use ```private``` or ```package```:
      - not ``` public int x;```
      - but ``` private int x; ```
- Compartmentalize
  - Run web application on a different machine from user database
  - Sealing different compartments of a ship will delay sinking.
  - Partition harddisk and install OS twice
  - chroot jail